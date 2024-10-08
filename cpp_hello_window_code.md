This is boilerplate code to create a simple window with OpenGL, as per the guide [[study_LearnOpenGL_GettingStarted]].

```C++
#include <iostream>
#include <glad/glad.h>
#include <GLFW/glfw3.h>
using namespace std;

void framebuffer_size_callback(GLFWwindow* window, int width, int height);
void processInput(GLFWwindow* window);

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
```