This is an example code to draw a simple rectangle with OpenGL, as per the guide [[study_LearnOpenGL]].

OpenGL Code
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

glm::mat4 transform(1.0f);

void framebufferSizeCallback(GLFWwindow* window, GLsizei width, GLsizei height);
GLuint buildShader(GLenum shaderType, string filename);
GLuint allocateBuffer(GLenum bufferTarget, const void* bufferData, unsigned int dataSize, GLenum bufferUsuage);
void processInput(GLFWwindow* window);
void keyCallback(GLFWwindow* window, int key, int scancode, int action, int mods);

int main()
{
	//Initialization
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

	if (!gladLoadGLLoader((GLADloadproc)(glfwGetProcAddress)))
	{
		cerr << "GLAD Initialization Failed." << endl;
		glfwTerminate();

		return -1;
	}

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
		// positions          // colors           // texture coords
		 0.5f,  0.5f, 0.0f,   1.0f, 0.0f, 0.0f,   1.0f, 1.0f,   // top right
		 0.5f, -0.5f, 0.0f,   0.0f, 1.0f, 0.0f,   1.0f, 0.0f,   // bottom right
		-0.5f, -0.5f, 0.0f,   0.0f, 0.0f, 1.0f,   0.0f, 0.0f,   // bottom left
		-0.5f,  0.5f, 0.0f,   1.0f, 1.0f, 0.0f,   0.0f, 1.0f    // top left 
	};

	unsigned int indices[] = {
		0, 1, 3,
		1, 2, 3
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

	GLuint EBO = allocateBuffer(GL_ELEMENT_ARRAY_BUFFER, indices, sizeof(indices), GL_STATIC_DRAW);

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
	GLsizei stride = 8 * sizeof(float); // X,Y,Z,R,G,B,S,T -> 8 floats
	unsigned int colorOffset = 3 * sizeof(float);
	unsigned int txCoordOffset = 6 * sizeof(float);

	// Position
	glVertexAttribPointer(0, 3, GL_FLOAT, GL_FALSE, stride, (void*)0);
	glEnableVertexAttribArray(0);

	// Color
	glVertexAttribPointer(1, 3, GL_FLOAT, GL_FALSE, stride, (void*)colorOffset);
	glEnableVertexAttribArray(1);

	// Texture Coordinates
	glVertexAttribPointer(2, 2, GL_FLOAT, GL_FALSE, stride, (void*)txCoordOffset);
	glEnableVertexAttribArray(2);

	// Uniforms
	//-------------------------------------------------------------------------
	glUseProgram(shaderProgram);
	glUniform1i(glGetUniformLocation(shaderProgram, "texture0"), 0);

	// Matrix Transformation
	// TIP: order matters. Rotate -> Scale -> Translate
	//-------------------------------------------------------------------------
	glm::mat4 model(1.0f);
	model = glm::rotate(model, glm::radians(-55.0f), glm::vec3(1.0f, 0.0f, 0.0f));
	GLuint modelLoc = glGetUniformLocation(shaderProgram, "model");
	glUniformMatrix4fv(modelLoc, 1, GL_FALSE, glm::value_ptr(model));

	glm::mat4 view(1.0f);
	view = glm::translate(view, glm::vec3(0.0f, 0.0f, -3.0f));
	GLuint viewLoc = glGetUniformLocation(shaderProgram, "view");
	glUniformMatrix4fv(viewLoc, 1, GL_FALSE, glm::value_ptr(view));

	glfwSetKeyCallback(window, keyCallback);

	// Render Loop
	//-------------------------------------------------------------------------
	while (!glfwWindowShouldClose(window))
	{
		processInput(window);

		glClearColor(0.0f, 0.0f, 0.0f, 1.0f);
		glClear(GL_COLOR_BUFFER_BIT);

		glUseProgram(shaderProgram);

		GLuint transformLoc = glGetUniformLocation(shaderProgram, "transform");
		glUniformMatrix4fv(transformLoc, 1, GL_FALSE, glm::value_ptr(transform));

		float fovy = 45.0f;
		float aspect = static_cast<float>(viewWidth) / static_cast<float>(viewHeight);
		float zNear = 0.1f;
		float zFar = 100.0f;
		glm::mat4 projection = glm::perspective(glm::radians(fovy), aspect, zNear, zFar);
		GLuint projectionLoc = glGetUniformLocation(shaderProgram, "projection");
		glUniformMatrix4fv(projectionLoc, 1, GL_FALSE, glm::value_ptr(projection));

		glDrawElements(GL_TRIANGLES, 6, GL_UNSIGNED_INT, (void*)0);

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
}

void keyCallback(GLFWwindow* window, int key, int scancode, int action, int mods)
{
	float speed = 0.05f;

	if (action == GLFW_PRESS || action == GLFW_REPEAT)
	{
		if (key == GLFW_KEY_Q)
			transform = glm::translate(transform, glm::vec3(0.0f, 0.0f, -speed));
		else if (key == GLFW_KEY_E)
			transform = glm::translate(transform, glm::vec3(0.0f, 0.0f, speed));
		else if (key == GLFW_KEY_A)
			transform = glm::translate(transform, glm::vec3(-speed, 0.0f, 0.0f));
		else if (key == GLFW_KEY_D)
			transform = glm::translate(transform, glm::vec3(speed, 0.0f, 0.0f));
		else if (key == GLFW_KEY_W)
			transform = glm::translate(transform, glm::vec3(0.0f, speed, 0.0f));
		else if (key == GLFW_KEY_S)
			transform = glm::translate(transform, glm::vec3(0.0f, -speed, 0.0f));
	}
}
```

Vertex Shader
```C
#version 330 core
layout (location = 0) in vec3 a_pos;
layout (location = 1) in vec3 a_color;
layout (location = 2) in vec2 a_txCoord;

uniform mat4 transform;
uniform mat4 model;
uniform mat4 view;
uniform mat4 projection;

out vec3 v_color;
out vec2 v_txCoord;

void main()
{
	gl_Position = projection * transform * view * model * vec4(a_pos, 1.0f);
	v_color = a_color;
	v_txCoord = a_txCoord;
}
```

Fragment Shader
```C
#version 330 core
in vec3 v_color;
in vec2 v_txCoord;

uniform sampler2D texture0;

out vec4 f_color;

void main()
{
	f_color = texture(texture0, v_txCoord) * vec4(v_color, 1.0);
}
```