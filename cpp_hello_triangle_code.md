This is an example code to draw a simple triangle with OpenGL, as per the guide [[study_LearnOpenGL_GettingStarted]].

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
		-0.5f, -0.5f, 0.0f, // left  
		 0.5f, -0.5f, 0.0f, // right 
		 0.0f,  0.5f, 0.0f  // top   
	};

	unsigned int VBO, VAO;
	glGenVertexArrays(1, &VAO);
	glGenBuffers(1, &VBO);
	// bind the Vertex Array Object first, then bind and set vertex buffer(s), and then configure vertex attributes(s).
	glBindVertexArray(VAO);

	glBindBuffer(GL_ARRAY_BUFFER, VBO);
	glBufferData(GL_ARRAY_BUFFER, sizeof(vertices), vertices, GL_STATIC_DRAW);

	glVertexAttribPointer(0, 3, GL_FLOAT, GL_FALSE, 3 * sizeof(float), (void*)0);
	glEnableVertexAttribArray(0);

	// note that this is allowed, the call to glVertexAttribPointer registered VBO as the vertex attribute's bound vertex buffer object so afterwards we can safely unbind
	glBindBuffer(GL_ARRAY_BUFFER, 0);

	// You can unbind the VAO afterwards so other VAO calls won't accidentally modify this VAO, but this rarely happens. Modifying other
	// VAOs requires a call to glBindVertexArray anyways so we generally don't unbind VAOs (nor VBOs) when it's not directly necessary.
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
		glDrawArrays(GL_TRIANGLES, 0, 3);


		// glfw: swap buffers and poll IO events (key press/release, mouse move, etc.)
		// ----------------------------------------
		glfwSwapBuffers(window);
		glfwPollEvents();
	}

	//glfwDestroyWindow(window); // not necessary?

	glfwTerminate();

	return 0;
}

// process all input: query GLFW whether relevant keys are pressed/released this frame,
// and react accordingly
void processInput(GLFWwindow* window)
{
	if (glfwGetKey(window, GLFW_KEY_ESCAPE) == GLFW_PRESS)
		glfwSetWindowShouldClose(window, true);
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