This is an example code to draw a simple rectangle with OpenGL, as per the guide [[study_LearnOpenGL_GettingStarted]].

```C++
#include <iostream>
#include <fstream>
#include <sstream>
#include <string>
#include <glad/glad.h>
#include <GLFW/glfw3.h>
using namespace std;

void framebuffer_size_callback(GLFWwindow* window, int width, int height);
void processInput(GLFWwindow* window);
string LoadShader(const string& filepath);
unsigned int buildShader(GLenum shaderType, const char* shaderSource);

// settings
const unsigned int SCR_WIDTH = 800;
const unsigned int SCR_HEIGHT = 600;

int main()
{
	// glfw: init and config
	// ----------------------------------------
	glfwInit();
	glfwWindowHint(GLFW_CONTEXT_VERSION_MAJOR, 3);
	glfwWindowHint(GLFW_CONTEXT_VERSION_MINOR, 3);
	glfwWindowHint(GLFW_OPENGL_PROFILE, GLFW_OPENGL_CORE_PROFILE);

	// glfw window creation
	// ----------------------------------------
	GLFWwindow* window = glfwCreateWindow(SCR_WIDTH, SCR_HEIGHT, "LearnOpenGL", NULL, NULL);
	if (window == NULL)
	{
		cerr << "Failed to create GLFW window" << endl;
		glfwTerminate();
		return -1;
	}
	glfwMakeContextCurrent(window);
	glfwSetFramebufferSizeCallback(window, framebuffer_size_callback);

	// glad: load all OpenGL function Poinsters
	// ----------------------------------------
	//gladLoadGL(); // equivalent?
	if (!gladLoadGLLoader((GLADloadproc)glfwGetProcAddress))
	{
		cerr << "Failed to initialize GLAD" << endl;
		return -1;
	}

	// build & compile shaders
	// ----------------------------------------
	// Vertex Shader
	string vertexShaderSource = LoadShader("triangle_vertex.glsl");
	unsigned int vertexShaderID = buildShader(GL_VERTEX_SHADER, vertexShaderSource.c_str());
	
	// Fragment Shader
	string fragmentShaderSource = LoadShader("triangle_fragment.glsl");
	unsigned int fragmentShaderID = buildShader(GL_FRAGMENT_SHADER, fragmentShaderSource.c_str());

	// link shaders
	unsigned int shaderProgram = glCreateProgram();
	glAttachShader(shaderProgram, vertexShaderID);
	glAttachShader(shaderProgram, fragmentShaderID);
	glLinkProgram(shaderProgram);
	
	int success;
	char infoLog[512];
	glGetProgramiv(shaderProgram, GL_LINK_STATUS, &success);

	if (!success) {
		glGetProgramInfoLog(shaderProgram, 512, NULL, infoLog);
		std::cout << "ERROR::SHADER::PROGRAM::LINKING_FAILED\n" << infoLog << std::endl;
	}
	glDeleteShader(vertexShaderID);
	glDeleteShader(fragmentShaderID);


	// set up vertex data (and buffer(s)) and configure vertex attributes
	// ------------------------------------------------------------------
	float vertices[] = {
		 0.5f,  0.5f, 0.0f,  // top right
		 0.5f, -0.5f, 0.0f,  // bottom right
		-0.5f, -0.5f, 0.0f,  // bottom left
		-0.5f,  0.5f, 0.0f   // top left 
	};
	unsigned int indices[] = {  // note that we start from 0!
		0, 1, 3,  // first Triangle
		1, 2, 3   // second Triangle
	};

	unsigned int VBO, VAO, EBO;
	glGenVertexArrays(1, &VAO);
	glGenBuffers(1, &VBO);
	glGenBuffers(1, &EBO);
	// bind the Vertex Array Object first, then bind and set vertex buffer(s),
	// and then configure vertex attributes(s).
	glBindVertexArray(VAO);

	glBindBuffer(GL_ARRAY_BUFFER, VBO);
	glBufferData(GL_ARRAY_BUFFER, sizeof(vertices), vertices, GL_STATIC_DRAW);

	glBindBuffer(GL_ELEMENT_ARRAY_BUFFER, EBO);
	glBufferData(GL_ELEMENT_ARRAY_BUFFER, sizeof(indices), indices, GL_STATIC_DRAW);

	glVertexAttribPointer(0, 3, GL_FLOAT, GL_FALSE, 3 * sizeof(float), (void*)0);
	glEnableVertexAttribArray(0);

	// unbind VBO
	glBindBuffer(GL_ARRAY_BUFFER, 0);

	// common practice to unbind the VAO once initialization is complete,
	// to prevent unintentional modification
	glBindVertexArray(0);


	// render loop
	// ----------------------------------------
	while (!glfwWindowShouldClose(window))
	{
		// input
		// ----------------------------------------
		processInput(window);

		// clear the buffer at the beginning of every frame
		glClearColor(0.2f, 0.3f, 0.3f, 1.0f);
		glClear(GL_COLOR_BUFFER_BIT);

		glUseProgram(shaderProgram);
		glBindVertexArray(VAO);
		glDrawElements(GL_TRIANGLES, 6, GL_UNSIGNED_INT, 0);
		glBindVertexArray(0);


		// glfw: swap buffers and poll IO events (key press/release, mouse move, etc.)
		// ----------------------------------------
		glfwSwapBuffers(window);
		glfwPollEvents();
	}

	// optional: de-allocate all resources
	glDeleteVertexArrays(1, &VAO);
	glDeleteBuffers(1, &VBO);
	glDeleteBuffers(1, &EBO);
	glDeleteProgram(shaderProgram);

	// only necessary if there are multiple windows
	//glfwDestroyWindow(window);

	glfwTerminate();

	return 0;
}

// process all input: query GLFW whether relevant keys are pressed/released this frame,
// and react accordingly
void processInput(GLFWwindow* window)
{
	if (glfwGetKey(window, GLFW_KEY_ESCAPE) == GLFW_PRESS)
		glfwSetWindowShouldClose(window, true);

	if (glfwGetKey(window, GLFW_KEY_1) == GLFW_PRESS)
		glPolygonMode(GL_FRONT_AND_BACK, GL_FILL);

	if (glfwGetKey(window, GLFW_KEY_2) == GLFW_PRESS)
		glPolygonMode(GL_FRONT_AND_BACK, GL_LINE);

	if (glfwGetKey(window, GLFW_KEY_3) == GLFW_PRESS)
		glPolygonMode(GL_FRONT_AND_BACK, GL_POINT);
}

// glfw: this callback functione executes whenever the window size changes
// (by OS or user resize)
void framebuffer_size_callback(GLFWwindow* window, int width, int height)
{
	glViewport(0, 0, width, height);
}

// shader file loader
// make sure to use c_str() to convert the string to const char*
string LoadShader(const string& filepath)
{
	ifstream shaderFile(filepath);
	stringstream shaderStream;

	// Read file's buffer contents into streams
	shaderStream << shaderFile.rdbuf();

	// close file handlers
	shaderFile.close();

	// Convert stream into string
	return shaderStream.str();
}


unsigned int buildShader(GLenum shaderType, const char* shaderSource)
{
	unsigned int shaderIndex = glCreateShader(shaderType);
	glShaderSource(shaderIndex, 1, &shaderSource, NULL);
	glCompileShader(shaderIndex);

	int success;
	char infoLog[512];
	glGetShaderiv(shaderIndex, GL_COMPILE_STATUS, &success);

	if (!success)
	{
		glGetShaderInfoLog(shaderIndex, 512, NULL, infoLog);
		cerr << "ERROR::SHADER::VERTEX::COMPILATION_FAILED\n" << infoLog << endl;
	}

	return shaderIndex;
}
```