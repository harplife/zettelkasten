This is an example code to implement camera & movement with OpenGL, as per the guide [[study_LearnOpenGL_GettingStarted]].

OpenGL code
```C++
#include <iostream>
#include <fstream>
#include <sstream>
#include <string>
#include <glad/glad.h>
#include <GLFW/glfw3.h>
#define STB_IMAGE_IMPLEMENTATION
#include "stb_image.h"
#define GLM_ENABLE_EXPERIMENTAL
#include <glm/glm.hpp>
#include <glm/gtc/matrix_transform.hpp>
#include <glm/gtc/type_ptr.hpp>
#include <glm/gtx/io.hpp>
using namespace std;

const unsigned int SCR_WIDTH = 540;
const unsigned int SCR_HEIGHT = 540;
unsigned int viewWidth = 540;
unsigned int viewHeight = 540;
const char* SCR_TITLE = "OpenGL Application";

glm::mat4 model(1.0f);
glm::mat4 view(1.0f);

// Camera Movement Variables
float pitch = 0.0f;
float yaw = -90.0f;
glm::vec3 worldUp(0.0f, 1.0f, 0.0f);
glm::vec3 cameraPosition(0.0f, 0.0f, 3.0f);
glm::vec3 cameraFront(0.0f, 0.0f, -1.0f);
glm::vec3 cameraRight = glm::normalize(glm::cross(cameraFront, worldUp));
glm::vec3 cameraUp = glm::normalize(glm::cross(cameraRight, cameraFront));

// Cursor Movement Variables
float xPosLast = SCR_WIDTH / 2;
float yPosLast = SCR_HEIGHT / 2;
float sensitivity = 0.1f;
bool firstMouse = true;

float deltaTime = 0.0f;
float lastFrame = 0.0f;
unsigned int frameCount = 0;
float deltaTimeTotal = 0.0f;
float deltaTimeAvg = 0.0f;
float frameRate = 0.0f;

void framebufferSizeCallback(GLFWwindow* window, GLsizei width, GLsizei height);
GLuint buildShader(GLenum shaderType, string filename);
GLuint allocateBuffer(GLenum bufferTarget, const void* bufferData, unsigned int dataSize, GLenum bufferUsuage);
void processInput(GLFWwindow* window);
void keyCallback(GLFWwindow* window, int key, int scancode, int action, int mods);
void updateCameraVectors();
void mouseCallback(GLFWwindow* window, double xPos, double yPos);

int main()
{
	// Initialization
	//-------------------------------------------------------------------------
	cout << "Hello OpenGL!" << endl;

	if (!glfwInit())
	{
		cerr << "GLFW Initialization Failed." << endl;

		return -1;
	}

	glfwWindowHint(GLFW_CONTEXT_VERSION_MAJOR, 3);
	glfwWindowHint(GLFW_CONTEXT_VERSION_MINOR, 3);
	glfwWindowHint(GLFW_OPENGL_PROFILE, GLFW_OPENGL_CORE_PROFILE);

	GLFWwindow* window = glfwCreateWindow(SCR_WIDTH, SCR_HEIGHT, SCR_TITLE, NULL, NULL);

	if (!window)
	{
		cerr << "GLFW Window Creation Failed." << endl;
		glfwTerminate();

		return -1;
	}

	glfwMakeContextCurrent(window);

	glfwSetFramebufferSizeCallback(window, framebufferSizeCallback);
	glfwSetInputMode(window, GLFW_CURSOR, GLFW_CURSOR_DISABLED);

	if (!gladLoadGLLoader((GLADloadproc)(glfwGetProcAddress)))
	{
		cerr << "GLAD Initialization Failed." << endl;
		glfwTerminate();

		return -1;
	}

	// Configure global OpenGL state
	//-------------------------------------------------------------------------
	glEnable(GL_DEPTH_TEST);

	// Vertex & Fragment Shaders
	//-------------------------------------------------------------------------
	GLuint vertexShader = buildShader(GL_VERTEX_SHADER, "triangle_vert.glsl");
	if (!vertexShader) {
		cerr << "No Shader Found." << endl;
		glfwTerminate();

		return -1;
	}

	GLuint fragmentShader = buildShader(GL_FRAGMENT_SHADER, "triangle_frag.glsl");
	if (!fragmentShader) {
		cerr << "No Shader Found." << endl;
		glfwTerminate();

		return -1;
	}


	GLuint shaderProgram = glCreateProgram();

	if (!shaderProgram)
	{
		cerr << "Shader Program Creation Failed." << endl;
		glfwTerminate();

		return -1;
	}

	glAttachShader(shaderProgram, vertexShader);
	glAttachShader(shaderProgram, fragmentShader);
	glLinkProgram(shaderProgram);

	GLint programStatus;
	glGetProgramiv(shaderProgram, GL_LINK_STATUS, &programStatus);

	if (!programStatus)
	{
		char programLog[512];
		glGetProgramInfoLog(shaderProgram, 512, NULL, programLog);

		cerr << programLog << endl;
	}

	glDeleteShader(vertexShader);
	glDeleteShader(fragmentShader);

	// Import Data
	//-------------------------------------------------------------------------
	float vertices[] = {
		// positions          // texture coords
		-0.5f, -0.5f, -0.5f,  0.0f, 0.0f,
		 0.5f, -0.5f, -0.5f,  1.0f, 0.0f,
		 0.5f,  0.5f, -0.5f,  1.0f, 1.0f,
		 0.5f,  0.5f, -0.5f,  1.0f, 1.0f,
		-0.5f,  0.5f, -0.5f,  0.0f, 1.0f,
		-0.5f, -0.5f, -0.5f,  0.0f, 0.0f,

		-0.5f, -0.5f,  0.5f,  0.0f, 0.0f,
		 0.5f, -0.5f,  0.5f,  1.0f, 0.0f,
		 0.5f,  0.5f,  0.5f,  1.0f, 1.0f,
		 0.5f,  0.5f,  0.5f,  1.0f, 1.0f,
		-0.5f,  0.5f,  0.5f,  0.0f, 1.0f,
		-0.5f, -0.5f,  0.5f,  0.0f, 0.0f,

		-0.5f,  0.5f,  0.5f,  1.0f, 0.0f,
		-0.5f,  0.5f, -0.5f,  1.0f, 1.0f,
		-0.5f, -0.5f, -0.5f,  0.0f, 1.0f,
		-0.5f, -0.5f, -0.5f,  0.0f, 1.0f,
		-0.5f, -0.5f,  0.5f,  0.0f, 0.0f,
		-0.5f,  0.5f,  0.5f,  1.0f, 0.0f,

		 0.5f,  0.5f,  0.5f,  1.0f, 0.0f,
		 0.5f,  0.5f, -0.5f,  1.0f, 1.0f,
		 0.5f, -0.5f, -0.5f,  0.0f, 1.0f,
		 0.5f, -0.5f, -0.5f,  0.0f, 1.0f,
		 0.5f, -0.5f,  0.5f,  0.0f, 0.0f,
		 0.5f,  0.5f,  0.5f,  1.0f, 0.0f,

		-0.5f, -0.5f, -0.5f,  0.0f, 1.0f,
		 0.5f, -0.5f, -0.5f,  1.0f, 1.0f,
		 0.5f, -0.5f,  0.5f,  1.0f, 0.0f,
		 0.5f, -0.5f,  0.5f,  1.0f, 0.0f,
		-0.5f, -0.5f,  0.5f,  0.0f, 0.0f,
		-0.5f, -0.5f, -0.5f,  0.0f, 1.0f,

		-0.5f,  0.5f, -0.5f,  0.0f, 1.0f,
		 0.5f,  0.5f, -0.5f,  1.0f, 1.0f,
		 0.5f,  0.5f,  0.5f,  1.0f, 0.0f,
		 0.5f,  0.5f,  0.5f,  1.0f, 0.0f,
		-0.5f,  0.5f,  0.5f,  0.0f, 0.0f,
		-0.5f,  0.5f, -0.5f,  0.0f, 1.0f
	};

	glm::vec3 cubePositions[] = {
		glm::vec3(0.0f,  0.0f,  0.0f),
		glm::vec3(2.0f,  5.0f, -15.0f),
		glm::vec3(-1.5f, -2.2f, -2.5f),
		glm::vec3(-3.8f, -2.0f, -12.3f),
		glm::vec3(2.4f, -0.4f, -3.5f),
		glm::vec3(-1.7f,  3.0f, -7.5f),
		glm::vec3(1.3f, -2.0f, -2.5f),
		glm::vec3(1.5f,  2.0f, -2.5f),
		glm::vec3(1.5f,  0.2f, -1.5f),
		glm::vec3(-1.3f,  1.0f, -1.5f)
	};

	// VAO, VBO, EBO
	//-------------------------------------------------------------------------
	GLuint VAO;
	glGenVertexArrays(1, &VAO);
	glBindVertexArray(VAO);

	GLuint VBO = allocateBuffer(GL_ARRAY_BUFFER, vertices, sizeof(vertices), GL_STATIC_DRAW);

	if (!VBO)
	{
		cerr << "Buffer Object Creation Failed." << endl;

		glfwTerminate();

		return -1;
	}

	// Load Texture
	//-------------------------------------------------------------------------
	GLuint texture0;
	glGenTextures(1, &texture0);

	glActiveTexture(GL_TEXTURE0);
	glBindTexture(GL_TEXTURE_2D, texture0);
	glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_WRAP_S, GL_REPEAT);
	glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_WRAP_T, GL_REPEAT);
	glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_MIN_FILTER, GL_LINEAR_MIPMAP_LINEAR);
	glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_MAG_FILTER, GL_LINEAR);

	int txWidth, txHeight, txChannels;
	unsigned char* imgData = stbi_load("textures/container.jpg", &txWidth, &txHeight, &txChannels, 0);

	if (imgData)
	{
		glTexImage2D(GL_TEXTURE_2D, 0, GL_RGB, txWidth, txHeight, 0, GL_RGB, GL_UNSIGNED_BYTE, imgData);
		glGenerateMipmap(GL_TEXTURE_2D);
	}
	else
	{
		cerr << "Failed to load texture" << endl;
	}

	stbi_image_free(imgData);

	// Vertex Attributes
	//-------------------------------------------------------------------------
	GLsizei stride = 5 * sizeof(float); // X,Y,Z,S,T -> 5 floats
	unsigned int txCoordOffset = 3 * sizeof(float);

	// Position
	glVertexAttribPointer(0, 3, GL_FLOAT, GL_FALSE, stride, (void*)0);
	glEnableVertexAttribArray(0);

	// Texture Coordinates
	glVertexAttribPointer(1, 2, GL_FLOAT, GL_FALSE, stride, (void*)txCoordOffset);
	glEnableVertexAttribArray(1);

	// Uniforms
	//-------------------------------------------------------------------------
	glUseProgram(shaderProgram);
	glUniform1i(glGetUniformLocation(shaderProgram, "texture0"), 0);

	// Matrix Transformation
	// TIP: order matters. Rotate -> Scale -> Translate
	//-------------------------------------------------------------------------
	//model = glm::rotate(model, glm::radians(-55.0f), glm::vec3(1.0f, 0.0f, 0.0f));
	GLuint modelLoc = glGetUniformLocation(shaderProgram, "model");

	//view = glm::translate(view, glm::vec3(0.0f, 0.0f, -3.0f));
	GLuint viewLoc = glGetUniformLocation(shaderProgram, "view");

	float fovy = 45.0f;
	float aspect = static_cast<float>(viewWidth) / static_cast<float>(viewHeight);
	float zNear = 0.1f;
	float zFar = 100.0f;
	glm::mat4 projection = glm::perspective(glm::radians(fovy), aspect, zNear, zFar);
	GLuint projectionLoc = glGetUniformLocation(shaderProgram, "projection");

	glfwSetKeyCallback(window, keyCallback);
	glfwSetCursorPosCallback(window, mouseCallback);

	// Render Loop
	//-------------------------------------------------------------------------
	while (!glfwWindowShouldClose(window))
	{
		float currentFrame = static_cast<float>(glfwGetTime());
		deltaTime = currentFrame - lastFrame;
		lastFrame = currentFrame;

		frameCount += 1;
		deltaTimeTotal += deltaTime;
		deltaTimeAvg = deltaTimeTotal / frameCount;
		frameRate = 1 / deltaTimeAvg;

		processInput(window);

		glClearColor(0.0f, 0.0f, 0.0f, 1.0f);
		glClear(GL_COLOR_BUFFER_BIT | GL_DEPTH_BUFFER_BIT);

		glUseProgram(shaderProgram);

		//glUniformMatrix4fv(modelLoc, 1, GL_FALSE, glm::value_ptr(model));
		glUniformMatrix4fv(projectionLoc, 1, GL_FALSE, glm::value_ptr(projection));

		glm::mat4 view = glm::lookAt(cameraPosition, cameraPosition + cameraFront, cameraUp);
		glUniformMatrix4fv(viewLoc, 1, GL_FALSE, glm::value_ptr(view));

		for (unsigned int i = 0; i < 10; i++)
		{
			model = glm::mat4(1.0f);
			model = glm::translate(model, cubePositions[i]);
			float angle = 20.0f * i;
			model = glm::rotate(model, glm::radians(angle), glm::vec3(1.0f, 0.3f, 0.5f));
			glUniformMatrix4fv(modelLoc, 1, GL_FALSE, glm::value_ptr(model));

			glDrawArrays(GL_TRIANGLES, 0, 36);
		}

		//glDrawArrays(GL_TRIANGLES, 0, 36);

		glfwSwapBuffers(window);
		glfwPollEvents();
	}

	glfwTerminate();

	return 0;
}


void framebufferSizeCallback(GLFWwindow* window, GLsizei width, GLsizei height)
{
	glViewport(0, 0, width, height);
	viewWidth = width;
	viewHeight = height;
}


GLuint buildShader(GLenum shaderType, string filename)
{
	ifstream file(filename);
	if (!file)
	{
		cerr << "Shader Source File Not Found." << endl;

		return 0;
	}

	stringstream ss;
	ss << file.rdbuf();

	string shaderSource = ss.str();
	const GLchar* shaderSource_c = shaderSource.c_str();

	file.close();

	GLuint shader = glCreateShader(shaderType);

	glShaderSource(shader, 1, &shaderSource_c, NULL);

	glCompileShader(shader);

	int success;
	glGetShaderiv(shader, GL_COMPILE_STATUS, &success);

	if (!success)
	{
		GLchar infoLog[512];
		glGetShaderInfoLog(shader, 512, NULL, infoLog);
		cerr << "ERROR::SHADER::COMPILATION_FAILED\n" << infoLog << endl;

		return 0;
	}

	return shader;
}


GLuint allocateBuffer(GLenum bufferTarget, const void* bufferData, unsigned int dataSize, GLenum bufferUsuage)
{
	GLuint bufferObject;

	glGenBuffers(1, &bufferObject);
	glBindBuffer(bufferTarget, bufferObject);
	glBufferData(bufferTarget, dataSize, bufferData, bufferUsuage);

	GLint bufferSize = 0;
	glGetBufferParameteriv(bufferTarget, GL_BUFFER_SIZE, &bufferSize);

	if (bufferSize != dataSize)
	{
		GLenum error = glGetError();

		while (error != GL_NO_ERROR)
		{
			cerr << "OpenGL Error: " << error << endl;
			error = glGetError();
		}

		// returns 0
		glDeleteBuffers(1, &bufferObject);
	}

	return bufferObject;
}


void processInput(GLFWwindow* window)
{
	if (glfwGetKey(window, GLFW_KEY_ESCAPE) == GLFW_PRESS)
	{
		glfwSetWindowShouldClose(window, GLFW_TRUE);
	}

	if (glfwGetKey(window, GLFW_KEY_1) == GLFW_PRESS)
	{
		glPolygonMode(GL_FRONT_AND_BACK, GL_FILL);
	}

	if (glfwGetKey(window, GLFW_KEY_2) == GLFW_PRESS)
	{
		glPolygonMode(GL_FRONT_AND_BACK, GL_LINE);
	}

	if (glfwGetKey(window, GLFW_KEY_3) == GLFW_PRESS)
	{
		glPolygonMode(GL_FRONT_AND_BACK, GL_POINT);
	}

	float speed = 3.0f * deltaTime;
	if (glfwGetKey(window, GLFW_KEY_UP) == GLFW_PRESS)
		cameraPosition += speed * cameraFront;
	if (glfwGetKey(window, GLFW_KEY_DOWN) == GLFW_PRESS)
		cameraPosition -= speed * cameraFront;
	if (glfwGetKey(window, GLFW_KEY_LEFT) == GLFW_PRESS)
		cameraPosition -= glm::normalize(glm::cross(cameraFront, cameraUp)) * speed;
	if (glfwGetKey(window, GLFW_KEY_RIGHT) == GLFW_PRESS)
		cameraPosition += glm::normalize(glm::cross(cameraFront, cameraUp)) * speed;

	float rotationSpeed = speed * 10;
	if (glfwGetKey(window, GLFW_KEY_W) == GLFW_PRESS)
	{
		pitch += rotationSpeed;
		updateCameraVectors();
	}
	if (glfwGetKey(window, GLFW_KEY_S) == GLFW_PRESS)
	{
		pitch -= rotationSpeed;
		updateCameraVectors();
	}
	if (glfwGetKey(window, GLFW_KEY_D) == GLFW_PRESS)
	{
		yaw += rotationSpeed;
		updateCameraVectors();
	}
	if (glfwGetKey(window, GLFW_KEY_A) == GLFW_PRESS)
	{
		yaw -= rotationSpeed;
		updateCameraVectors();
	}

}

void keyCallback(GLFWwindow* window, int key, int scancode, int action, int mods)
{
	//float speed = 3.0f * deltaTime;
	//cout << speed << endl;

	//if (action == GLFW_PRESS || action == GLFW_REPEAT)
	//{
	//	switch (key)
	//	{
	//		case GLFW_KEY_W:
	//			cameraPosition += cameraFront * speed;
	//			break;
	//		case GLFW_KEY_S:
	//			cameraPosition -= cameraFront * speed;
	//			break;
	//		case GLFW_KEY_D:
	//			cameraPosition += cameraRight * speed;
	//			break;
	//		case GLFW_KEY_A:
	//			cameraPosition -= cameraRight * speed;
	//			break;
	//	}
	//}
}

void updateCameraVectors()
{
	cameraFront.x = cos(glm::radians(yaw)) * cos(glm::radians(pitch));
	cameraFront.y = sin(glm::radians(pitch));
	cameraFront.z = sin(glm::radians(yaw)) * cos(glm::radians(pitch));
	cameraFront = glm::normalize(cameraFront);
	cameraRight = glm::normalize(glm::cross(cameraFront, worldUp));
	cameraUp = glm::normalize(glm::cross(cameraRight, cameraFront));
}

void mouseCallback(GLFWwindow* window, double xPos, double yPos)
{
	if (firstMouse)
	{
		xPosLast = xPos;
		yPosLast = yPos;
		firstMouse = false;
	}

	float xOffset = xPos - xPosLast;
	float yOffset = yPosLast - yPos;
	xPosLast = xPos;
	yPosLast = yPos;

	xOffset *= sensitivity;
	yOffset *= sensitivity;

	yaw += xOffset;
	pitch += yOffset;

	updateCameraVectors();
}
```

Vertex Shader
```C
#version 330 core
layout (location = 0) in vec3 a_pos;
layout (location = 1) in vec2 a_txCoord;

uniform mat4 model;
uniform mat4 view;
uniform mat4 projection;

out vec2 v_txCoord;

void main()
{
	gl_Position = projection * view * model * vec4(a_pos, 1.0f);
	v_txCoord = a_txCoord;
}
```

Fragment Shader
```C
#version 330 core
in vec2 v_txCoord;

uniform sampler2D texture0;

out vec4 f_color;

void main()
{
	f_color = texture(texture0, v_txCoord);
}
```