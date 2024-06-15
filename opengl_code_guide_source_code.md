```C++
#include <iostream>
#include <fstream>
#include <sstream>
#include <string>
#include <glad/glad.h>
#include <GLFW/glfw3.h>
using namespace std;

const unsigned int SCR_WIDTH = 960;
const unsigned int SCR_HEIGHT = 540;
const char* SCR_TITLE = "OpenGL Application";

void framebuffer_size_callback(GLFWwindow* window, GLsizei width, GLsizei height);
GLuint buildShader(GLenum shaderType, string filename);
GLuint allocateBuffer(GLenum bufferTarget, const void* bufferData, unsigned int dataSize, GLenum bufferUsuage);
void processInput(GLFWwindow* window);

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

	glfwSetFramebufferSizeCallback(window, framebuffer_size_callback);

	if (!gladLoadGLLoader((GLADloadproc)(glfwGetProcAddress)))
	{
		cerr << "GLAD Initialization Failed." << endl;
		glfwTerminate();

		return -1;
	}

	// Vertex & Fragment Shaders
	//-------------------------------------------------------------------------
	GLuint vertexShader = buildShader(GL_VERTEX_SHADER, "triangle_vertex.glsl");
	if (!vertexShader) {
		cerr << "No Shader Found." << endl;
		glfwTerminate();

		return -1;
	}

	GLuint fragmentShader = buildShader(GL_FRAGMENT_SHADER, "triangle_fragment.glsl");
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
		 0.5f,  0.5f, 0.0f,  // top right
		 0.5f, -0.5f, 0.0f,  // bottom right
		-0.5f, -0.5f, 0.0f,  // bottom left
		-0.5f,  0.5f, 0.0f   // top left 
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

	glVertexAttribPointer(0, 3, GL_FLOAT, GL_FALSE, 3 * sizeof(float), (void*)0);
	glEnableVertexAttribArray(0);

	// Render Loop
	//-------------------------------------------------------------------------
	while (!glfwWindowShouldClose(window))
	{
		processInput(window);

		glClearColor(0.0f, 0.0f, 0.0f, 1.0f);
		glClear(GL_COLOR_BUFFER_BIT);

		glUseProgram(shaderProgram);
		glDrawElements(GL_TRIANGLES, 6, GL_UNSIGNED_INT, (void*)0);

		glfwSwapBuffers(window);
		glfwPollEvents();
	}

	glfwTerminate();

	return 0;
}


void framebuffer_size_callback(GLFWwindow* window, GLsizei width, GLsizei height)
{
	glViewport(0, 0, width, height);
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
```