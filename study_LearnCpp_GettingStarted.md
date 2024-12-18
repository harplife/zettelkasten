# Getting Started
- Following the guide https://www.learncpp.com

## Introduction to C/C++
### Before C++, there was C
- The C language was developed in 1972 by <mark class="hltr-trippy">Dennis Ritchie</mark> at Bell Telephone laboratories, primarily as a systems programming language (a language to write operating systems with).
- C ended up being so efficient and flexible that in 1973, Ritchie and <mark class="hltr-trippy">Ken Thompson</mark> rewrote most of the Unix operating systems using C (as opposed to Assembly).
	- Unlike Assembly, which produces programs that can only run on specific CPUs, C has excellent portability, allowing Unix to be easily recompiled on many different types of computers.
	- C and Unix had their fortunes tied together.
- In 1978, <mark class="hltr-trippy">Brian Kernighan</mark> and Dennis Ritchie published a book called "The C Programming Language".
	- This book was commonly known as K&R.
	- This book provided an informal specification for the language and became a de facto standard.
- In 1983, the <mark class="hltr-trippy">American National Standards Institute (ANSI)</mark> formed a committee to establish a formal standard for C.
	- In 1989, the C89 standard was released. It's more commonly known as ANSI C.
	- In 1990, the International Organization for Standardization (ISO) adopted ANSI C. This became known as C90.
- In 1999, the ISO committee released a new version of C called C99.
	- C99 adopted many features which had already made their way into compilers as extensions, or had been implemented in C++.

### C++
- In 1979, C++ was developed by <mark class="hltr-trippy">Bjarne Stroustrup</mark> at Bell Labs as an extension to C.
- C++ adds many new feature to the C language, and is perhaps best thought of as a superset of C (though not strictly true).
- C++ is an object-oriented language. More on this will be covered later.
- C++ was standardized in 1998 by the ISO committee.
	- A minor update to the language was released in 2003, called C++03.
- Five major updates to the C++ language (C++11, 14, 17, 20, and 23) have been made since then, each adding additional functionality.
	- C++11 in particular added a huge number of new capabilities, and is widely considered to be the new baseline version of the language.
- Each new formal release of the language is called a <mark class="hltr-trippy">Language Standard</mark> or **Language Specification**.
	- Standards are named after the year they are released in.

### C/C++'s Philosophy
- The underlying design philosophy of C and C++ can be summed up as "Trust the Programmer".
- C++ is designed to allow the programmer a high degree of freedom to do what they want.
	- However, this also means the language often won't stop the programmer from doing things that doesn't make sense.
	- Knowing what shouldn't be done in C/C++ is just as important as knowing what should be done.

>[!important] What is C++ good at?
>C++ excels in situations where high performance and precise control over memory and other resources is needed. Here are a few common types of application that most likely would be written in C++:
>- Video games
>- Real-time systems (e.g. transportation, manufacturing, etc.)
>- High-performance financial applications
>- Graphical applications and simulations
>- Productivity / office applications
>- Embedded software
>- Audio and video processing
>- AI/ML

## Introduction to C++ development
- There are 7 steps to C++ development:
	1. Define the problem to solve
	2. Design a solution
	3. Write a program that implements the solution
	4. Compile the program
	5. Link object files
	6. Test program
	7. Debug

### Step 4: Compiling your source code
- A C++ compiler is used to compile C++ source code files.
- The C++ compiler sequentially goes through each source code (`.cpp`) file in your program, and does two important tasks:
	- The compiler checks your C++ code to make sure it follows the rules of the C++ language. If it does not, the compiler will give you an error. The compilation process will also be aborted until the error is fixed.
	- The compiler translates your C++ code into machine language instructions. These instructions are stored in an intermediate file called an <mark class="hltr-trippy">object file</mark>. The object file also contains metadata that is required or useful in subsequent steps.
- Object files are typically named `name.o` or `name.obj`, where the `name` is the same name as the `name.cpp` file it was produced from.
- Installing a compiler will be covered later.

### Step 5: Linking object files and libraries
- After the compiler has successfully finished, another program called the <mark class="hltr-trippy">linker</mark> kicks in.
	- The linker's job is to combine all of the object files and produce the desired output file (typically an executable file). This process is called <mark class="hltr-trippy">linking</mark>.
- The linker has three main functionalities:
	- The linker reads in each of the object files generated by the compiler and makes sure they are valid.
	- The linker ensures all cross-file dependencies are resolved properly. For example, if you define something in one `.cpp` file, and then use it in a different `.cpp` file, the linker connects the two together. If the linker is unable to connect a reference to something with its definition, you'll get a linker error, and the linking process will abort.
	- The linker also is capable of linking library files. A <mark class="hltr-trippy">library file</mark> is a collection of precompiled code that has been "packaged up" for reuse in other programs.
- C++ comes with an extensive library called the <mark class="hltr-trippy">C++ Standard Library</mark> that provides a set of useful capabilities for use in your programs.
	- Almost every C++ program written utilizes the standard library in some form, so it's very common for the standard library to get linked into your programs. Most linkers will automatically link in the standard library as soon as you use any part of it, so this generally isn't something you need to worry about.
- You can also optionally link other libraries.
- Once the linker has finished linking all the object files and libraries successfully, then you will have an executable file that you can run.

>[!important] Definition: Building
>Because there are multiple steps involved, the term **building** is often used to refer to the full process of converting source code files into an executable that can be run. A specific executable produced as the result of building is sometimes called a **build**.
>For complex projects, build automation tools (such as make or build2) are often used to help automate the process of building programs and running automated tests.

### Steps 6 & 7: Testing and Debugging
- You run the executable and see whether it produces the output you were expecting. If not, it's time for some debugging to figure out what's wrong.
- We'll cover more on this topic later on.

>[!important] Integrated Development Environment (IDE)
>Note that steps 3, 4, 5, and 7 all involve software programs that must be installed; such as editor, compiler, linker, and debugger. While you can use separate programs for each of these activities, a software package known as an Integrated Development Environment (IDE) bundles and integrates all of these features together.


## Installing an IDE
- An <mark class="hltr-trippy">Integrated Development Environment (IDE)</mark> is a piece of software designed to make it easy to develop, build, and debug your programs.
- A typical modern IDE will include:
	- Some way to easily load and save your code files.
	- A code editor that has programming-friendly features, such as line numbering, syntax highlighting and such.
	- A basic build system that will allow you to compile and link your program into an executable, and then run it.
	- An integrated debugger.
	- Some way to install plugins.
- Some C++ IDEs will install and configure a C++ compiler and linker for you. Others will allow you to plug in a compiler and linker of your choice (installed separately).

### Choosing an IDE
- It's recommended to select an IDE that comes with a compiler that supports at least C++17.
- You should NOT be using any compiler that does not support at least C++11 (which is typically considered the modern minimum spec for C++).
- These are the absolute minimum compiler versions with C++17 support:
	- GCC/G++ 7
	- Clang++ 8
	- Visual Studio 2017 15.7
- This guide recommends using Visual Studio 2022.
- Do not use Visual Studio Code unless you are an experienced user.

## Compiling your first program
- To write a C++ program inside an IDE, we typically start by creating a new project.
- A <mark class="hltr-trippy">project</mark> is a container that holds all of your source code files, images, data files, and etc., that are needed to produce an executable that you can run or use.
- The project also saves various IDE, compiler, and linker settings, as well as remembering where you left off.
- When you choose to compile your program, all of the `.cpp` files in the project will get compiled and linked.
- Each project corresponds to one program.
- Project files are generally IDE specific, so a project created for one IDE will need to be recreated in a different IDE.
	- CMAKE is a tool that's typically used to convert a project from another environment to a project that's suited for the current environment.

### Workspaces / solutions
- When you create a new project for your program, many IDEs will automatically add your project to a "workspace" or a "solution" (the term varies by IDE).
- A <mark class="hltr-trippy">workspace/solution</mark> is a container that can hold one or more related projects.
	- For example, if you were writing a game and wanted to have a separate executable for single player and multiplayer, you'd need to create two projects. It wouldn't make sense for both of these projects to be completely independent - after all, they are part of the same game. Most likely, each would be configured as a separate project within a single workspace/solution.
- Although you can add multiple projects to a single solution, we generally recommend creating a new workspace or solution for each program, especially while learning. It's simpler and there's less chance of something going wrong.

### Writing your first program
- Skipping this part

### Options: Compile, build, rebuild, clean, and run/start?
- When a code file is compiled, your IDE may cache the resulting object file. That way, if the program is compiled again in the future, any code file that hasn't been modified doesn't need to be recompiled - the cached object file from last time can be used. This can speed up compilation times significantly.
- **Build** : compiles all modified code files in the project/workspace/solution.
- **Clean** : removes all cached objects and executables.
- **Rebuild** : does a clean followed by build.
- **Compile** : recompiles a single code file (regardless of caching). This option does not invoke the linker or produce an executable.
- **Run/start** : executes the executable from a prior build. Some IDEs will invoke a build before doing a run.

## Configuring your compiler: Build configurations
- A <mark class="hltr-trippy">build configuration</mark> (also called a **build target**) is a collection of project settings that determines how your IDE will build your project.
- The build configuration typically includes things like what the executable will be named, what directories the IDE will look in for other code and library files, where to keep or strip out debugging info, how much to have the compiler optimize your program, etc.
- When you create a new project in your IDE, most IDEs will set up two different build configurations for you: a release configuration, and a debug configuration.
- The <mark class="hltr-trippy">debug configuration</mark> is designed to help you debug your program, and is generally the one you will use when writing your programs.
	- This config turns off all optimizations, and includes debugging info - which makes your programs larger and slower but much easier to debug.
	- The debug config is usually selected as the active config by default.
- The <mark class="hltr-trippy">release configuration</mark> is designed to be used when releasing your program to the public.
	- This version is typically optimized for size and performance, and doesn't contain the extra debugging info.
	- Because the release config includes all optimizations, this mode is also useful for testing the performance of your code.

## Configuring your compiler: Compiler extensions
- The C++ standard defines rules about how programs should behave in specific circumstances. In most cases, compilers will follow these rules. However, many compilers implement their own changes to the language, often to enhance compatibility with other versions of the language, or for historical reasons. These compiler-specific behaviors are called <mark class="hltr-trippy">compiler extensions</mark>.
- Programs using non-standard extensions generally will not compile on other compilers, and even if they do, they may not run correctly.
- Be warned that compiler extensions are often enabled by default - this is not good for beginners.
- Compiler extensions are never necessary; it's recommended to turn them off.
	- Refer to IDE documentation on how to turn the compiler extensions off.
- Note that these settings are applied on a per-project basis.

## Configuring your compiler: Warning and error levels
- When you write your programs, the compiler will check to ensure you've followed the rules of the C++ language.
	- If any of the rules are violated, the compiler is required to emit a <mark class="hltr-trippy">diagnostic message</mark>.
	- The C++ standard does not define how diagnostics should be categorized or worded. However, there are some common conventions that compilers have adopted.
- If compilation cannot continue due to the violation, then the compiler will emit an error.
- If compilation can continue despite the violation, the compiler may decide to emit either an <mark class="hltr-trippy">error</mark> or a **warning**. Warnings are similar to errors, but they do not halt compilation.
	- In some cases, the compiler may identify code that does not violate the rules of the language, but that it believes could be incorrect. In such cases, the compiler may decide to emit a warning as a notice to the programmer that something seems amiss.
- In most cases, warnings can be resolved by fixing the issue. In rare cases, it may be necessary to explicitly tell the compiler to not generate a particular warning.
	- C++ does not support an official way to do this, but many compilers offer solutions (via `#pragma` directives).

### Increasing your warning levels
- By default, most compilers will only generate warnings about the most obvious issues. However, you can request your compiler to be more assertive about proving warnings for things it finds strange.
- If you are learning, turn your warning levels up to the maximum.
- For setting up max warning level for Visual Studio (All Configurations):
	- Project Properties > Configuration Properties > C/C++ > General > Warning Level : `Level4 (/W4)`
	  ![[VS-EnableAllWarnings-min.webp]]
	- .. > C/C++ > Command Line > Additional Options : `/w44365` (turns on signed/unsigned conversion warnings)
	- .. > C/C++ > External Includes > External Header Warning Level : `Level3 (/external:W3)`

### Treat warnings as errors
- It is possible to set compiler to treat all warnings as if they were errors; meaning, the compiler will halt if it finds any warnings.
- For Visual Studio:
	- Project Properties > Configuration Properties > C/C++ > General > Treat Warnings As Errors : `Yes (/WX)`
	  ![[Pasted image 20240723145052.png]]


### (personal note) Ignore Warnings
- Setting warning levels to 3~4 and treating warning as error definitely puts a wench in things when libraries are used. Use `#pragma` directive to tell the compiler to ignore warnings from a library, like so:

```c++
#pragma warning(push, 0)
#define STB_IMAGE_IMPLEMENTATION
#include "stb_image.h"
#pragma warning(pop)
```

## Configuring your compiler: Choosing a language standard
- In professional environments, it's common to chose a language standard that is one or two versions back from the latest standard (e.g. if C++20 is the latest, then C++14 or C++17).
	- This is typically done to ensure the compiler makers have had a chance to resolve defects, and that best practices for new features are well understood.
	- Where relevant, this also helps ensure better cross-platform compatibility, as compilers on some platforms may not provide full support for newer language standards immediately.
- For personal projects and while learning, choosing the latest finalized standard is fine, as there is little downside to doing so.
- This guide recommends using C++17 or higher.

### Setting a language standard in Visual Studio
![[Pasted image 20240723171123.png]]

### Exporting your configuration
- Having to reselect all of the settings each time you make a new project is burdensome - and so most IDEs provide a way to export your settings.
- For Visual Studio, Project > Export Template > Select Project Template, Add name, etc. > Finish
	- Once saved, the template will be shown when you make a new project

## Statements and the structure of a program

### Statements
- A <mark class="hltr-trippy">computer program</mark> is a sequence of instructions that tell the computer what to do.
- A <mark class="hltr-trippy">statement</mark> is a type of instruction that causes the program to perform some action.
- Statements are the smallest independent unit of computation in the C++ language, which makes it the most common type of instruction.
- Most (but not all) statements in C++ end in a semicolon.
- In a high-level language like C++, a single statement may compile into many machine language instructions.
- There are many different kinds of statements in C++:
	- Declaration
	- Jump
	- Expression
	- Compound
	- Selection (conditionals)
	- Iteration (loops)
	- Try
- Statements are typically grouped into units called functions.
- A <mark class="hltr-trippy">function</mark> is a collection of statements that get executed sequentially (top to bottom).
- Every C++ program must have a special function named `main`.
	- Programs typically terminate after the last statement inside `main` function has been executed.
- The name of a function (or object, type, template, etc.) is called its <mark class="hltr-trippy">identifier</mark>.

### Syntax and syntax errors
- The rules that govern how sentences are constructed in a language is called a <mark class="hltr-trippy">syntax</mark>.
	- If you violate a rule, the compiler will issue you a <mark class="hltr-trippy">syntax error</mark>.
- A common syntax error is when a semicolon is missing at the end of a statement.

## Comments
- A comment is a programmer-readable note that is inserted directly into the source code of the program, which gets ignored by the compiler and are for the programmer's use only.
- Single line comment begins with `//`.
- Multi-line comment begins with `/*` and ends with `*/`.

## Intro to objects and variables
### Data and values
- <mark class="hltr-trippy">Data</mark> is any info that can be moved, processed, or stored by a computer
- A single piece of data is called a <mark class="hltr-trippy">value</mark>.

### Random Access Memory
- The main memory in a computer is called <mark class="hltr-trippy">Random Access Memory (RAM)</mark>. When a program is ran, the OS loads the program into RAM.
- The OS reserves some additional RAM for the program to use while it is running. Common uses for this memory are to store values entered by the user, to store data read in from a file or network, or to store values calculated while the program is running so they can be used again later.

### Objects and variables
- In C++, direct memory access is discouraged. Instead, we access memory through an object.
- An <mark class="hltr-trippy">object</mark> is a region of storage (usually memory) that can store a value, and has other associated properties.
	- How the compiler and OS work to assign memory to objects is beyond the scope of this guide.
- Although objects in C++ can be unnamed (anonymous), more often we name our objects using an identifier. An object with a name is called a <mark class="hltr-trippy">variable</mark>.
- In general programming, the term *object* typically refers to an unnamed object in memory, a variable, or a function. In C++, the term *object* has a narrow definition that excludes functions.\

### Variable instantiation
- In order to create a variable, we use a special kind of declaration statement called a <mark class="hltr-trippy">definition</mark>.
	- Example: `int x;`
- When the program is run (called <mark class="hltr-trippy">runtime</mark>), the variable will be instantiated. <mark class="hltr-trippy">Instantiation</mark> means the object will be created and assigned a memory address.
	- Variables must be instantiated before they can be used to store values.
- An instantiated object is sometimes called an <mark class="hltr-trippy">instance</mark>.

### Data types
- A <mark class="hltr-trippy">data type</mark> determines what kind of value the object will store.
	- Types include `int`, `double`, `float`, `char`, `string`, `bool`, and etc.

### Defining multiple variables
- It is possible to define multiple variables of the same type in a single statement:

```C++
int a;
int b;
int c, d;
```

- Although the language allows it, it is best to avoid defining multiple variables in a single line.

## Variable assignment and initialization

### Variable assignment
- After a variable has been defined, a value can be given to the variable by using the `=` operator. This process is called an <mark class="hltr-trippy">assignment</mark>, and the `=` operator is called the <mark class="hltr-trippy">assignment operator</mark>.
	- Example: `int width; width = 5;`
- By default, assignment copies the value on the right-hand side of the `=` operator to the variable on the left-hand side of the operator. This is called <mark class="hltr-trippy">copy assignment</mark>.

### Initialization
- The process of specifying an initial value for an object is called <mark class="hltr-trippy">initialization</mark>.
- Definition and assignment can be combined into one with initialization.
	- Example: `int width = 5;`
- The syntax used to initialize an object is called an <mark class="hltr-trippy">initializer</mark>

### Different forms of initialization
- There are 6 basic ways to initialize variables in C++:

```C++
int a; // default initialization
int b = 5; // copy initialization
int c(6); // direct init

// List init methods (C++11) (preferred)
int d{7}; // direct list init
int e = {8}; // copy list init
int f{}; // value initialization
```

#### Default initialization
- When no initializer is provided, this is called <mark class="hltr-trippy">default initialization</mark>. In most cases, default init performs no init, and leaves a variable with an indeterminate value (garbage data).

#### Copy initialization
- <mark class="hltr-trippy">Copy initialization</mark> had fallen out of favor in modern C++ due to being less efficient than other forms of init for some complex types. However, C++ remedied the bulk of these issues, and copy init is now finding new advocates.
- Copy init is also used whenever values are implicitly copied or converted, such as when passing arguments to a function by value, returning from a function by value, or catching exceptions by value.

#### Direct initialization
- <mark class="hltr-trippy">Direct initialization</mark> refers to when an initial value is provided inside parenthesis.
- Direct initialization was initially introduced to allow for more efficient initialization of complex objects. It had fallen out of favor in modern C++, being superseded by list init.
	- Another reason why it had fallen out is because it makes it hard to differentiate variables from functions.
	- List init has a few quirks of its own, and so direct init is once again finding use in certain cases.

#### List initialization
- <mark class="hltr-trippy">List initialization</mark> (aka **uniform initialization**/**brace initialization**) refers to when curly braces are used; which comes in three forms:

```C++
int width{5};
int height = {6};
int depth{};
```

- Prior to the introduction of list initialization, some types of init required using copy init, and other types of init required using direct init. List init was introduced to provide a more consistent init syntax (which is why it is sometimes called "uniform initialization") that works in most cases.
- List initialization also provides a way to initialize objects with a list of values. More on this later.
- The primary benefit of list initialization is that "narrowing conversions" are disallowed.
	- Narrowing conversion is a potentially unsafe numeric conversion where the destination type may not be able to hold all the values of the source type (e.g. float to int).
	- For example, `int w1{4.5};` will produce a compile error.
- Note that this restriction on narrowing conversions only applies to the list initialization, not to any subsequent assignments to the variable.
	- For example, `w1 = 4.5;` is allowed.

#### Value initialization and zero initialization
- When a variable is initialized using empty braces, <mark class="hltr-trippy">value initialization</mark> takes place. In most cases, value init will init the variable to zero (or empty, if that's more appropriate for a given type).
	- In such cases where zeroing occurs, this is called <mark class="hltr-trippy">zero initialization</mark>.
- Use value initialization if the value is temporary and will be replaced.

### Ignoring unused variable warning
- In C++17, it's possible to ignore unused variable warning by placing `[[maybe_unused]]` in front of the variable. For example:

```C++
[[maybe_unused]] double pi {3.14};
```

## Introduction to iostream
### The input/output library
- The <mark class="hltr-trippy">input/output library</mark> (io library) is part of the C++ standard library that deals with basic input and output.
- To use the functionality defined within the iostream library, we need to include the iostream header at the top of any code file that uses the content defined in iostream, like so:

```C++
#include <iostream>

// rest of the code
```

### std::cout
- One of the most useful in the iostream is `std::cout`, which allows us to send data to the console to be printed out as text.
	- cout stands for character output.
- A simple program to print out `Hello World!`:

```C++
#include <iostream>

int main()
{
	std::cout << "Hello World!";

	return 0;
}
```

---

The `cout` object in C++ uses the insertion operator (`<<`) as a way to format output. This is part of the design of the C++ Standard Library’s stream I/O facilities.

Here’s why:

1. **Chainability**: The insertion operator returns a reference to the stream, allowing chained insertions into the same stream. For example:
    
    ```cpp
    std::cout << "Hello, " << "World!" << std::endl;
    ```
    
2. **Type Safety**: The insertion operator is overloaded for many different types, ensuring that the correct formatting is used for each type. This makes it safer and easier to use than C-style I/O functions like `printf`, which require the programmer to specify the type of each argument.
    
3. **Extensibility**: You can overload the insertion operator for your own types, allowing them to be printed using the same syntax as built-in types.
    

In essence, the use of the insertion operator with `cout` provides a consistent, type-safe, and extensible interface for formatted output in C++. It’s one of the features that make C++ a powerful and flexible language for a wide range of programming tasks.

---

### std::cout is buffered
- `std::cout` does not sent its output to the console immediately. Instead, the requested output is stored in a region of memory (called a buffer) first, and then the buffer gets flushed out periodically.
	- This means that if your program crashes/aborts/pauses before the buffer is flushed, any output still waiting in the buffer will not be displayed.
- Writing data to a buffer is typically fast, whereas transferring a batch of data to an output device is comparatively slow. Buffering can significantly increase performance by batching multiple output requests together to minimize the number of times output has to be sent to the output device.

### std::endl
- A way to end a line of text and start a new line is to use `std::endl`, like so:

```C++
#include <iostream>

int main()
{
	std::cout << "Hello World!" << std::endl;
	std::cout << "Bye World!" << std::endl;

	return 0;
}
```

console
```text
Hello world!
Bye World!
```

- `std::endl` may not be necessary after the last line, but it is good practice to do so because some OS do not output a new line before showing the command prompt again.
- `std::endl` not only outputs a newline, it also flushes the buffer.

### Newlines
- Another way to end a line and start a new line other than `std::endl`, is to use `\n` within the text.
	- `\n` can be better in situation where multiple lines of text is to be outputted. Because `std::endl` flushes the buffer, it is slow and inefficient - especially so when multiple lines mean multiple flushes (which is unnecessary).
- `\n` can be used, like so:

```C++
#include <iostraem>

int main()
{
	int x = 5;
	std::cout << "x is equal to: " << x << '\n'; // single quoted, by itself
	std::cout << "Yep." << "\n"; // double quoted, by itself
	std::cout << "And that's all, folks!\n"; // double quoted, part of text
}
```

console
```text
x is equal to: 5
Yep.
And that's all, folks!
```

### std::cin
- `std::cin` is another predefined variable in the `iostream` library.
- `std::cin`, which stands for "character input", reads input from keyboard.
- `>>` operator is typically used along side `std::cin`, like so:

```C++
#include <iostream>

int main()
{
    std::cout << "Enter a number: ";

    int x{};
    std::cin >> x;

    std::cout << "You entered " << x << '\n';
    return 0;
}
```

- Note that `std::endl` was not called after `std::cin`; this is due to the user pressing enter key to have their input accepted.
	- If accepting keyboard input without the user having to press enter, there are third party libraries that specialize in Terminal User Interface (TUI); pdcurses, FXTUI, cpp-terminal, or notcurses.

### std::cin is buffered
- Similarly to `std::cout`, the user input is stored inside a buffer for `std::cin` and then extracted with `>>` operator.
- `std::buffer` is buffered because it allows us to separate the entering of input from the extract of input. We can enter input once and then perform multiple extraction request on it.
- Note that extraction stops at space; whatever is left in the buffer will be extracted on the next iteration of `std::cin`. For example:

```C++
#include <iostream>  // for std::cout and std::cin

int main()
{
    std::cout << "Enter two numbers: ";

    int x{};
    std::cin >> x;

    int y{};
    std::cin >> y;

    std::cout << "You entered " << x << " and " << y << '\n';

    return 0;
}
```

Entering `4 5` first will first print out `4`, and then skip the next input. Instead, it will print out `5`.

## Uninitialized variables and undefined behavior

### Uninitialized variables
- A variable that has not been given a known value (through initialization or assignment) is called an <mark class="hltr-trippy">uninitialized variable</mark>.
- This lack of initialization is a performance optimization inherited from C, as it prevents from creating a lot of data to match creation of many variables (like 100,000 or more).
- Best practice is to always initialize your variables; omit the initialization only if it's intentional and purposeful.

>[!warning]
>Some compilers, such as Visual Studio, will initialize the contents of memory to some preset value when you're using a debug build configuration. This will not happen when using a release build configuration. Therefore, do not be confused when uninitialized variable returns a same value (instead of random garbage data).

- Most modern compilers can detect if a variable is being used without being given a value. If they do, they will generally issue a compile-time warning or error.

>[!warning]
>Using uninitialized variables is one of the most common mistakes that novice programmers make. It can also be one of the most challenging to debug because the program may run fine anyway if the uninitialized variable happened to get assigned to a spot of memory that had a reasonable value in it, like 0.

### Undefined behavior
- Undefined behavior (UB) is the result of executing code whose behavior is not well-defined by the C++ language. In this case, the C++ language doesn't have any rules determining what happens if you use the value of a variable that has not been given a known value.
	- Using the value from an uninitialized variable is an example of undefined behavior.
- Code implementing undefined behavior may exhibit any of the following symptoms:
	- Your program produces different results every time it is run.
	- Your program consistently produces the same incorrect result.
	- Your program behaves inconsistently (sometimes produces the correct result, sometimes not).
	- Your program seems like it’s working but produces incorrect results later in the program.
	- Your program crashes, either immediately or later.
	- Your program works on some compilers but not others.
	- Your program works until you change some other seemingly unrelated code.
- The worst is when undefined behavior actually produces the correct behavior.
- Always do what's necessary to avoid undefined behavior.

### Implementation-defined behavior and unspecified behavior
- Implementation-defined behavior means the behavior of some syntax is left up to the implementation (the compiler) to define. Such behaviors must be consistent and documented, but different compilers may produce different results.
- Example:

```C++
#include <iostream>

int main()
{
	std::cout << sizeof(int) << '\n'; // print how many bytes of memory an int value takes

	return 0;
}
```

- Above examples shows that different compilers (sometimes different OS) may treat the size of an integer differently; the printed value may be `4` or `2`.
- Unspecified behavior means the behavior of some syntax is left up to the implementation (the compiler) to define, but such implementation is not required to document the behavior.
- Best practice is to avoid both implementation-defined behavior and unspecified behavior.

## Keywords and naming identifiers
- C++ reserves a set of 92 words (as of C++23) for its own use - called the <mark class="hltr-trippy">keywords</mark>.
	- Keywords include data types like int, float, double, and etc.
	- Keywords include statements like if/else, case/switch, while, and etc.
- For a full list of keywords, refer to https://en.cppreference.com/w/cpp/keyword

### Identifier naming rules
- There's a lot of flexibility when it comes to naming identifiers. However, there are a few rules that must be followed:
	- No keywords
	- Only letters, numbers, and underscore character.
	- Must begin with a letter (lower/upper) or an underscore.
	- Case sensitive

### Identifier naming best practices
- Variable and function name should start with a lower case letter.
- If variable and function name requires multiple words, combine the words together as camelCase or snake_case.
- Note that when working with someone else's code, it's best to match the style of the existing code than to follow the naming convention above.
- Avoid naming identifiers starting with an underscore, as these names are typically reserved for OS, library, and/or compiler use.
- Identifiers should make clear what the value they are holding means.
- Good rule of thumb is to make the length of an identifier proportional to how widely it is used.
	- An identifier with a trivial use can have a short name (e.g. such as i).
	- An identifier that is used more broadly (e.g. a function that is called from many places) should have a longer and more descriptive name (e.g. instead of open, try openFileOnDisk).
- In any case, avoid abbreviations.
- Use comments to describe what a variable is going to be used for.

## Whitespace and basic formatting
- Whitespace is a term that refers to characters that are used for formatting purposes, such as spaces, tabs, and newlines.

### Whitespace separation
- Data type and variable name must be whitespace separated.
- Return type and function name must be whitespace separated.
- Single-line comments are terminated by a newline.
- Preprocessor directives must be placed on separate lines.

### Quoted text and whitespace
- Amount of whitespace is taken literally inside quoted text.
- Newlines are not allowed in quoted text.
	- However, newline character `\n` is fine.
- Quoted text separated by nothing but whitespace will be concatenated:

```C++
std::cout << "Hello "
	"world!"; // prints "Hello world!"
```

### Basic formatting
- C++ does not enforce any kind of formatting restrictions on the programmer. Which means whitespace is generally ignored. This means we can use whitespace wherever we like to format our code in order to make it easier to read.
	- Other languages like Python does enforce restrictions. Indentation errors if violation.
- It's fine to use either tabs or spaces for indentation - there is a debate on it.
- Most IDEs will convert a tab to 4 spaces. This is the recommended way.
- There are two conventional styles for function braces:
	- Opening curly brace on the same line as the statement.
	- Opening curly brace on its own line and same indentation with the closing curly brace (recommended).
- Each statement within curly braces should start one tab in from the closing brace of the function it belongs to.
- Lines should be limited to 80 characters or less.
- If a long line is split with an operator (e.g. `<<` or `+`), the operator should be placed at the beginning of the next line:

```C++
std::cout << 3 + 4
    + 5 + 6
    * 7 * 8;
```

- Use whitespace to align values or comments:

```C++
cost          = 57;  // align
pricePerItem  = 24;  // the comments
value         = 5;   // for
numberOfItems = 17;  // readability

// cout lives in the iostream library
std::cout << "Hello world!\n";

// these comments are easier to read
std::cout << "It is very nice to meet you!\n";

// when separated by whitespace
std::cout << "Yeah!\n";
```

- Best practice is to be consistent with whatever style that has already been established.

### Automatic formatting
- Most modern IDEs will help you format your code.
- In Visual Studio, Edit > Advanced > Format Document/Selection (ctrl+k, ctrl+d)

### Style guides
- A **style guide** is a concise, opinionated document containing programming conventions, formatting guidelines, and best practices.
- Some commonly referenced C++ style guides include:
	- [C++ Core Guidelines](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines) - maintained by Bjarne Stroustrup and Herb Sutter
	- Google
	- LLVM
	- GCC/GNU

## Intro to literals and operators
- A <mark class="hltr-trippy">literal (literal constant)</mark> is a fixed value that has been inserted directly into the source code.
- Literals and variables both have a value and a type. Unlike a variable, the value of a literal is fixed.
- Refer to this example:

```C++
#include <iostream>

int main()
{
    std::cout << 5 << '\n'; // print the value of a literal

    int x { 5 };
    std::cout << x << '\n'; // print the value of a variable
    return 0;
}
```
 
- In the above example, both output statements do the same thing (prints 5). But in the case of literal, the value is printed out directly, as opposed to being fetched from the memory.
- Literals are values that are inserted directly into the source code. These values usually appear directly in the executable code (unless they are optimized out).

### Operators and operands
- In mathematics, an <mark class="hltr-trippy">operation</mark> is a process involving zero or more input values (called <mark class="hltr-trippy">operands</mark>) that produces a new value (called an <mark class="hltr-trippy">output value</mark>). The specific operation to be performed is denoted by a symbol called an <mark class="hltr-trippy">operator</mark>.
	- For example, for a statement like `int x = 1 + 2;`, 1 and 2 are operands and the + is the operator.
- Common operators:
	- addition `+`
	- subtraction `-`
	- multiplication `*`
	- division `/`
	- equality `==` / inequality `!=`
	- assignment `=`
	- insertion `<<` / extraction `>>`
- The number of operands that an operator takes as input is called the operator's <mark class="hltr-trippy">arity</mark>.
	- Not a common word, don't use this word willy nilly
- Operators come in four different arities:
	- <mark class="hltr-trippy">Unary</mark> : acts on one operand. For example, given `-5`, the `operator-` takes literal operand `5` and flips its sign to produce new output value `-5`.
	- <mark class="hltr-trippy">Binary</mark> : acts on two operands placed on left and right. For example, given `1 + 2`, the `operator+` takes the left operand `1` and the right operand `2` and outputs `3`. The insertion `<<` and extraction `>>` operators are also binary operators.
	- <mark class="hltr-trippy">Ternary</mark> : acts on three operands. There is only one, which is the conditional operator. This will be covered later.
	- <mark class="hltr-trippy">Nullary</mark> : operators act on zero operands. There is only one, which is the throw operator. This will be covered later.
- Note that some operators have more than one meaning depending on how they are used. For example, `operator-` has two contexts: used in unary form to invert a number's sign, and used in binary form to do subtraction.

### Chaining operators
- Operators can be chained together such that the output of one operator can be used as the input for another operator.
	- For example, given `2 * 3 + 4`, the multiplication goes first (`2 * 3`) and then the result of that is fed to the plus operator (`6 + 4)`.
- The order in which operators execute is a topic that will be covered more later on. For now, it's enough to know that the arithmetic operators execute in the same order as they do in standard math: <mark class="hltr-trippy">PEMDAS</mark>.
	- Parenthesis > Exponents > Multiplication/Division > Addition/Subtraction
	- "Please Excuse My Dear Aunt Sally"

### Return values and side effects
- Some operators have additional behaviors. An operator (or function) that has some observable effect beyond producing a return value is said to have a <mark class="hltr-trippy">side effect</mark>.
	- For example, given `x = 5;`, the changed value of `x` is observable even after the operator has finished executing.
	- Another example, given `std::cout << 5;`, the number `5` gets printed to console and stays there even if the statement has finished executing.

## Intro to expressions

### Expressions
- An <mark class="hltr-trippy">expression</mark> is a non-empty sequence of literals, variables, operators, and function calls that calculates a single value.
- The process of executing an expression is called <mark class="hltr-trippy">evaluation</mark>.
- When an expression is evaluated, each of the terms inside the expression are evaluated, until a single value remains - referred to as the <mark class="hltr-trippy">result</mark> of the expression.
- Expressions are always evaluated as part of statements.
	- For example, given `int x = 2+3;`, the expression `2+3` is part of a statement that assigns a value to `x`.
	- Above statement broken down into its syntax would look like this: `type identifier operator expression`.
- A statement that consists of an expression followed by a semicolon is called an <mark class="hltr-trippy">expression statement</mark>.
- Expression statement that produces a value only to discard it, is considered useless (some compilers may produce warnings).
- <mark class="hltr-trippy">Subexpression</mark> : an expression used as an operand.
	- For example, subexpressions of `x = 4 + 5` are `x` and `4 + 5`.
- <mark class="hltr-trippy">Full expression</mark> : an expression made up of subexpression(s).
	- For example, `2`, `2 + 3`, and `x = 4 + 5` are all full expressions.
- <mark class="hltr-trippy">Compound expression</mark> : an expression that contains two or more uses of operators.
	- For example, `x = 4 + 5` is a compound expression because it contains `operator=` and `operator+`.

## Intro to functions
- A <mark class="hltr-trippy">function</mark> is a reusable sequence of statements designed to do a particular job.
- Functions that you write yourself are called <mark class="hltr-trippy">user-defined functions</mark>.
- The structure of a function looks like this:

```C++
returnType functionName() // function header
{
	// function body
}
```

- Unlike some other programming languages, C++ does not allow for functions to be defined inside other functions. The following program is NOT legal:

```C++
#include <iostream>

int main()
{
    void foo() // Illegal: this function is nested inside function main()
    {
        std::cout << "foo!\n";
    }

    foo(); // function call to foo()
    return 0;
}
```

- "foo" is a meaningless word that is often used as a placeholder name for a function or variable when the name is unimportant to the demonstration of some concept.
	- Such words are called <mark class="hltr-trippy">metasyntactic variables</mark>, though they're often called <mark class="hltr-trippy">placeholder names</mark> instead.
	- Other common metasyntactic variables include `bar`, `baz`, and 3-letter words that end in oo, such as `goo`, `moo`, and `boo`.

## Function return values
### Return values
- A function can return a value or none at all.
- A function has to indicate what type of value will be returned - which is done by setting the function's <mark class="hltr-trippy">return type</mark> which is defined before the function's name.
	- For example, if the function returns an integer value, then `int` needs to be indicated before the function name.
- If the function does not return a value, it has to indicate that it doesn't, which can be done by setting the function's return type as `void`.
	- Do not put a return statement at the end of a void function.
- It's always a good idea to leave a comment indicating what the return values mean.

### Status codes
- The return value from `main()` is sometimes called a <mark class="hltr-trippy">status code</mark> (aka **exit code**), which is passed back to the caller of the program to indicate that the program has run successfully (or not).
- If the status code is `0`, then the program ran normally.
	- A non-zero status code is often used to indicate failure.
- The C++ standard only defines the meaning of 3 status codes:
	- `0`
	- `EXIT_SUCCESS`
	- `EXIT_FAILURE`

### A value-returning function / no return value
- A function that returns a value is called a <mark class="hltr-trippy">value-returning function</mark>.
	- Any function that is not `void` function is value-returning.
- A value-returning function MUST return a value of that type, otherwise undefined behavior will result.
- `main()` is the only exception to the rule, where it will implicitly return `0` if a return statement is not provided.

### Functions return a single value
- A value-returning function can only return a single value back to the caller each time it is called.
- Note that the value provided in a return statement doesn't need to be literal - it can be the result of any valid expression, including a variable or even a call to another function that returns a value.
- There are various ways to work around the single value limitation, which will be covered later on.

### Don't Repeat Yourself
- One of the central tenets of good programming and the main point of a function is "Don't Repeat Yourself" (DRY).
	- If it takes several lines of code to complete a task and it needs to be repeated, it's better to turn it into a function so that only one line of code is repeated.
- DRY is meant to be a guideline, not an absolute rule. DRY can harm overall comprehension when code is broken into pieces that are too small.

## Intro to function parameters/arguments
### Function parameters and arguments
- A <mark class="hltr-trippy">function parameter</mark> is a variable used in the header of a function which is initialized with a value provided by the caller of the function.
- For example:

```C++
void printValue(int x)
{
	std::cout << x << std::endl;
}
```

- In the example above, `int x` is the function parameter for the function `printValue()`. 
- An argument is a value that is passed from the caller to the function when a function call is made.
- For example:

```C++
printValue(5);
```

- In the example above, `5` is the argument passed to `printValue()`.

### How parameters and arguments work together
- When a function is called, all of the parameters of the function are created as variables, and the value of each of the arguments is copied into the matching parameter (using copy initialization). This process is called <mark class="hltr-trippy">pass-by-value</mark>.
	- Function parameters that utilize pass-by-value are called <mark class="hltr-trippy">value parameters</mark>.
- Note that the number of arguments must generally match the number of function parameters. Otherwise, the compiler will throw an error.
- The argument passed to a function can be any valid expression, as the argument is essentially just an initializer for the parameter, and initializers can be any valid expression.

### Using return values as arguments
- A function can be called inside function header, using return values as arguments.
	- For example, `foo(bar());`.

### Unreferenced parameters
- When a parameter is not used inside the function body, compiler sends out a warning that says <mark class="hltr-trippy">unreferenced parameter</mark>.
- In cases where a function parameter needs to exist but is not used in the function body, the name of the function parameter can be omitted (bypasses the warning).
	- A parameter without a name is called an <mark class="hltr-trippy">unnamed parameter</mark>.
	- It's recommended to use a comment to indicate what the name would've been.
	- For example, `void doSomething(int /*count*/);`

## Intro to local scope

### Local variables
- Variables defined inside a function are called <mark class="hltr-trippy">local variables</mark>.
- Function parameters are created and initialized when the function is entered, and variables within the function body are created and initialized at the point of definition.
	- Local variables are destroyed in the opposite order of creation.
- An object's <mark class="hltr-trippy">lifetime</mark> is defined to be the time between its creation and destruction.
	- Note that variable creation/destruction happen during runtime, not at compile time. Therefore, lifetime is a runtime property.
- In most cases, the destroyed object becomes invalid, and any further use of the object will result in undefined behavior.
	- At some point after destruction, the memory used by the object will be freed up.

### Local scope
- An identifier's scope determines where the identifier can be seen and used within the source code.
- When an identifier can be seen and used, we say it is <mark class="hltr-trippy">in scope</mark>.
	- When an identifier cannot be seen nor used, we say it is <mark class="hltr-trippy">out of scope</mark>.
- Scope is a compile-time property, and trying to use an identifier outside its scope will result in a compile error.
- Local variables defined in one function are not in scope in other functions.

### Functional separation
- Variables with duplicate names but in different scopes does not conflict with each other - meaning, variable `x` defined in `foo()` is not the same as `x` defined in `bar()`.

### Temporary objects
- A <mark class="hltr-trippy">temporary object</mark> (aka **anonymous object**) is an unnamed object that is created by the compiler to store a value temporarily.
- There are many different ways that temporary values can be created. For example:

```C++
#include <iostream>

int getValueFromUser()
{
 	std::cout << "Enter an integer: ";
	int input{};
	std::cin >> input;

	return input;
}

int main()
{
	std::cout << getValueFromUser() << '\n';

	return 0;
}
```

- In the example above, variable `input` is destroyed at the end of the function, and the caller receives a copy of the value. This copy of the value is stored in a temporary object, which is then passed to `std::cout` to be printed.
- Temporary objects have no scope at all. They are destroyed at the end of the full expression in which they are created.

## Forward declarations and definitions
### Forward declarations
- The compiler compiles the contents of code files **sequentially**. When the compiler reaches a function that is not defined (before it's called), the compiler will raise an error.
- Having functions defined before it is called is a simple solution for a simple program, but in a larger complex program, it can be tedious trying to figure out which functions call which other functions (in what order).
	- In fact, it becomes a problem when there are two or more functions that call upon each other. For example, if `foo()` calls `bar()` and `bar()` calls `foo()`, there is no way to order the functions to make it work.
- A <mark class="hltr-trippy">forward declaration</mark> allows us to tell the compiler about the existence of an identifier before actually defining the identifier.
	- When the compiler encounters a call to the function that is not yet defined but declared instead, it'll check to make sure the function is being called correctly but won't execute the function call until the function definition is found.
- A <mark class="hltr-trippy">function declaration</mark> (**function prototype**) is, as it sounds, declaring a function (but without definition). Its statement consists of the function's return type, name, and parameter types, terminated with a semicolon.
	- The function body is not included in the declaration.
	- The function declaration statement must match the function that is defined later on.
	- Forward declaration is simply a function declaration that is done before definition. Think "paying it forward".
- Example of forward declaration:

```C++
#include <iostream>

int add(int x, int y); // forward declaration of add()

int main()
{
    std::cout << "The sum of 3 and 4 is: " << add(3, 4) << '\n';
    return 0;
}

int add(int x, int y)
{
    return x + y;
}
```

>[!important]
>Main advantage of using forward declaration is that it allows us to use a function that is defined in a different code file.

### Forgetting the function body
- One of the common mistakes that new programmers do is forgetting to define the function after the forward declaration has been made.
	- In such case, the program may compile and run fine as long as the function is not called. However, if the function is called, the linker will raise error.

### Declarations vs. definitions
- A <mark class="hltr-trippy">declaration</mark> tells the compiler about the existence of an identifier and its associated type information.
	- Example: `int add(int x, int y);`, `int x;`
- A <mark class="hltr-trippy">definition</mark> is a declaration that actually implements or instantiates the identifier.
	- Note that `int x;` is both a definition and a declaration.
- Declarations that aren't definitions are called <mark class="hltr-trippy">pure declarations</mark>.
	- In common language, the term declaration is typically used to mean a pure declaration, and a definition is used to mean a definition that also serves as a declaration.

### The one definition rule (ODR)
- The <mark class="hltr-trippy">one definition rule (ODR)</mark> is a well-known rule in C++ that consists of three parts:
	1. Within a file, each function, variable, type or template in a given scope can only have one definition. Definitions occurring in different scopes do not violate this rule.
	2. Within a program, each function or variable in a given scope can only have one definition. This rule exists because programs can have more than one file. Functions and variables not visible to the linker are excluded from this rule.
	3. Types, templates, inline functions, and inline variables are allowed to have duplicate definitions in different files, so long as each definition is identical.
- Violating part 1 of the ODR will cause the compiler to issue a redefinition error.
- Violating ODR part 2 will cause the linker to issue a redefinition error.
- Violating ODR part 3 will cause undefined behavior.
- Functions that share an identifier but have different sets of parameters are considered to be distinct functions. This is called <mark class="hltr-trippy">overloading</mark>, and such definitions do not violate the ODR. More on this topic discussed later on.

## Programs with multiple code files
- As programs get larger, it is common to split them into multiple files for organizational or reusability purposes.
- IDEs provide functionalities to manage files in a project.
- The compiler compiles each file individually. It does not know about the contents of other code files, or remember anything it has been from previously compiled code files.
- The limited visibility and short memory is intentional, for a few reasons:
	- It allows the source files of a project to be compiled in any order.
	- When we change a source file, only that source file needs to be recompiled.
	- It reduces the possibility of naming conflicts between identifiers in different files.
- In order to call a function that is defined in another file, forward declaration of the function needs to be made (in current file).

>[!warning]
>Even if you create a file in the same project folder via File Explorer (Windows), some IDEs may ignore that file. It's best to create to create a new file by using the IDE, or add the file to the project manually.

## Naming collisions and an introduction to namespaces

### Naming collisions
- When a compiler or linker can't tell apart two identical identifiers, they will produce an error - referred to as <mark class="hltr-trippy">naming collision/conflict</mark>.
	- Note that this error will occur even if these two functions are defined in separate files.
	- This error will occur even if the function is not called.

### Namespaces
- A namespace provides another type of scope region (called <mark class="hltr-trippy">namespace scope</mark>) that allows you to declare names inside of it for the purpose of disambiguation. Any names declared inside the namespace won't be mistaken for identical names in other scopes.
- Only declarations and definitions can appear in the scope of a namespace (not executable statements).
- Namespaces are often used to group related identifiers in a large project to help ensure they don't inadvertently collide with other identifiers.

### The global namespace
- Any name that is not defined inside a class, function, or a namespace is considered to be part of an implicitly-defined namespace called the <mark class="hltr-trippy">global namespace</mark> (**global scope**).
- `main()` is defined inside the global namespace.
- Although variables can be defined in the global namespace, this should generally be avoided.
- If global variables have to be used, it's strongly encouraged to use a global constant variable.

#### Sharing variables between multiple functions
There are several ways for multiple functions to share a variable without using a global variable in C++. Here are a few methods:

1. **Passing by Reference**: You can pass the variable as a reference to the functions that need to access or modify it. This allows the functions to share the same variable.
    ```cpp
    void func1(int& x) {
        x += 5;
    }

    void func2(int& x) {
        x *= 2;
    }

    int main() {
        int a = 10;
        func1(a);
        func2(a);
        std::cout << a << std::endl; // Outputs 30
        return 0;
    }
    ```

2. **Static Local Variables**: You can declare a variable as `static` inside a function. A static local variable retains its value between function calls and is shared by all calls to that function.
    ```cpp
    void func() {
        static int x = 0;
        x += 5;
        std::cout << x << std::endl;
    }

    int main() {
        func(); // Outputs 5
        func(); // Outputs 10
        return 0;
    }
    ```

3. **Class Members**: If the functions are methods of the same class, they can share a variable by making it a member of the class.
    ```cpp
    class MyClass {
    public:
        int x;

        void func1() {
            x += 5;
        }

        void func2() {
            x *= 2;
        }
    };

    int main() {
        MyClass obj;
        obj.x = 10;
        obj.func1();
        obj.func2();
        std::cout << obj.x << std::endl; // Outputs 30
        return 0;
    }
    ```

Remember, each of these methods has its own use cases and trade-offs. It's important to choose the one that best fits your needs based on the specific requirements of your program.

### Explicit namespace qualifier ::
- The `::` symbol is an operator called the <mark class="hltr-trippy">scope resolution operator</mark>.
	- The identifier to the left of the `::` symbol identifies the namespace that the name to the right is contained within (e.g. `namespace::variable`).
	- If no identifier on the left is provided, the global namespace is assumed.
- For example, `std::cout` means `cout` that is declared in namespace `std`.
- When an identifier includes a namespace prefix, the identifier is called a <mark class="hltr-trippy">qualified name</mark>.

### Using namespace std
- There is a way to omit a namespace whenever a function/variable is used from that namespace, and that is to use a <mark class="hltr-trippy">using directive</mark>.
- The using directive statement is structured like `using namespace namespaceIdentifier;`.
	- For example, `using namespace std;`. Once this is in place, `cout` can be called instead of `std::cout`.

>[!warning]
>Avoid using-directives at the top of your program or in header files. They violate the reason why namespaces were added in the first place.

### Curly braces and indented code
- In C++, curly braces are often used to delineate a scope region that is nested within another scope region.
	- For example, a function defined inside the global scope uses curly braces to separate the scope region of the function from the global scope.
- In certain cases, identifiers defined outside the curly braces may still be part of the scope defined by the curly braces rather than the surrounding scope.
	- Function parameters are a good example of this.

## Intro to preprocessor
- Prior to compilation, each code file (`.cpp`) goes through a <mark class="hltr-trippy">preprocessing</mark> phase, where a program called the `preprocessor` makes various changes to the text of the code file according to the directives (instructions).
- The preprocessor does not actually modify the original code files in any way; all changes happen either temporarily in-memory or using temporary files.
- Some of the things that the preprocessor do:
	- Strips out comments
	- Ensures each code file ends in a newline
	- Processes `#include` directives (more on this later)
- When the preprocessor has finished processing a code file, the result is called a <mark class="hltr-trippy">translation unit</mark>.
	- The translation unit is then compiled by the compiler.
- The entire process of preprocessing, compiling, and linking is called <mark class="hltr-trippy">translation</mark>.

### Preprocessor directives
- When the preprocessor runs, it scans through the code file to find <mark class="hltr-trippy">preprocessor directives</mark>, which tells the preprocessor to perform certain text manipulation tasks.
	- Preprocessor directive start with a `#` symbol and end with a newline (no semicolon).
- The preprocessor directives have their own syntax.
- Although the term "directive" often means preprocessor directive, it is not always the case; the `using` directive is NOT a preprocessor directive.

### Include directive
- The `#include` directive tells the preprocessor to replace the directive with the contents of the included file.
	- For example, `#include <iostream>` replaces the line with the contents of the `iostream`.
- The included contents are then preprocessed, then the rest of the file is preprocessed.
	- When the included contents are being preprocessed, the preprocessor directives in the included contents will be preprocessed too; this becomes a recursive process.

### Macro defines
- The `#define` directive can be used to create a <mark class="hltr-trippy">macro</mark>, which is a rule that defines how input text is converted into replacement output text.
- There are two basic types of macros: object-like macros, and function-like macros.
- <mark class="hltr-trippy">Function-like macros</mark> act like functions, and serve a similar purpose. Their use is generally considered unsafe, and almost anything they can do can be done by a normal function.
- <mark class="hltr-trippy">object-like macros</mark> can be defined in one of two ways:
	1. `#define IDENTIFIER`
	2. `#define IDENTIFIER substitution_text`
- The identifier for a macro can use letters, numbers, and underscores. But it cannot start with a number, and should not start with an underscore.
	- By convention, macro names are typically all upper-case, separated by underscores.

### Object-like macros with substitution text
- When the preprocessor encounters this directive, any further occurrence of the identifier is replaced by `substitution_text`. The identifier is traditionally typed in all capital letters, using underscores to represent spaces.
- Consider the following program:

```C++
#include <iostream>

#define MY_NAME "Alex"

int main()
{
    std::cout << "My name is: " << MY_NAME << '\n';

    return 0;
}
```

- The preprocessor converts the above into the following:

```C++
// The contents of iostream are inserted here

int main()
{
    std::cout << "My name is: " << "Alex" << '\n';

    return 0;
}
```

>[!warning]
>Object-like macros with substitution text were used (in C) as a way to assign names to literals. This is no longer necessary, as better methods are available in C++. Object-like macros with substitution text are now typically only seen in legacy code, and it's best to avoid using them.

### Object-like macros without substitution text
- Macros of this form work like you'd expect - any further occurrence of the identifier is removed and replaced by nothing.
- Unlike object-like macros with substitution text, macros of this form are generally acceptable to use; especially so with conditional compilation.

### Conditional compilation
- The <mark class="hltr-trippy">conditional compilation</mark> preprocessor directives allow you to specify under what conditions something will or won't compile. There are quite a few different conditional compilation directives, but the three most used are: `#ifdef`, `#ifndef`, and `#endif`.
- The `#ifdef` preprocessor directive allows the preprocessor to check whether an identifier has been previously `#defined`. If so, the code between the `#ifdef` and matching `#endif` is compiled. If not, the code is ignored.
- Consider the following program:

```C++
#include <iostream>

#define PRINT_JOE

int main()
{
#ifdef PRINT_JOE
    std::cout << "Joe\n"; // will be compiled
#endif

#ifdef PRINT_BOB
    std::cout << "Bob\n"; // will be excluded
#endif

    return 0;
}
```

- The code example above prints `Joe\n` because `PRINT_JOE` is defined.
- `#ifndef` is the opposite of `#ifdef`.

>[!important]
>Conditional compilation in C++ is primarily used for the following purposes:
>
>1. **Platform-Specific Code**: You can use conditional compilation to include or exclude code based on the platform (operating system, processor type, etc.) the program is being compiled on. This is useful when certain code is only applicable or optimal for specific platforms.
>
>2. **Debugging and Testing**: Conditional compilation is often used to include debugging or testing code that should not be part of the final release version of the program. For example, you might have additional logging or assertions in a debug build that are disabled in a release build.
>
>3. **Feature Flags**: You can use conditional compilation to enable or disable features in your program. This can be useful for gradually rolling out new features, or for disabling features that aren't ready yet.
>
>4. **Backward Compatibility**: If you're working with different versions of a library or a language feature, conditional compilation can help manage code that should only be compiled with certain versions.
>
>Remember, while conditional compilation is a powerful tool, it can also make code harder to read and maintain if overused. It's generally a good idea to minimize the amount of conditionally compiled code in your program.

### \#if 0
- One way to use conditional compilation is to comment out a block of code, which can be done by using `#if 0` directive.
- Note that multi-line comments cannot be nested; meaning, a code block that already contains a multi-line comment cannot be commented out using another multi-line comment.
	- `#if 0` provides a convenient way to circumvent this issue.
- Example:

```C++
#include <iostream>

int main()
{
    std::cout << "Joe\n";

#if 0 // Don't compile anything starting here
    std::cout << "Bob\n";
    /* Some
     * multi-line
     * comment here
     */
    std::cout << "Steve\n";
#endif // until this point

    return 0;
}
```

### object-like macros don't affect other preprocessor directives
- Macros only cause text substitution for non-preprocessor commands.

### The scope of \#defines
- Directives are resolved before compilation, from top to bottom on a file-by-file basis.
- Because `#include` directive replaces the `#include` directive with the content of the included file, the directives from the included file are copied into the current file. These directives will then be processed in order.
- Consider this example:

Alex.h:
```C++
#define MY_NAME "Alex"
```

main.cpp:
```C++
#include "Alex.h" // copies #define MY_NAME from Alex.h here
#include <iostream>

int main()
{
	std::cout << "My name is: " << MY_NAME << '\n';

	return 0;
}
```

- In the example above, `MY_NAME` is replaced with `"Alex"`.
- Once the preprocessor has finished, all defined identifiers from that file are discarded. This means that directives are only valid from the point of definition to the end of the file in which they are defined.
	- In other words, directives defined in one file do not have any impact on other files (unless they are included into another file).

## Header files

### Headers and their purpose
- Along with C++ code files (with `.cpp` extension), there is another type of file called a **header file** with an extension `.h`, `.hpp`, or none at all.

>[!important]
>In C++, a header file (with the `.h` or `.hpp` extension) serves several important purposes:
>
>1. **Function Declarations**: Header files are commonly used to declare functions. This allows these functions to be used (called) in other source files that include the header file.
>
>2. **Type Definitions**: You can define new types (like `struct`, `class`, `enum`, `typedef`, etc.) in a header file. These types can then be used in other source files that include the header file.
>
>3. **Constant Definitions**: Constants that are used in multiple source files are often defined in a header file.
>
>4. **Template Definitions**: Unlike function and class declarations, template definitions (the actual implementation of a template function or class) have to be in the header file, because the compiler needs to have access to the entire template definition to generate code for each instantiation of the template.
>
>5. **Inline Function Definitions**: Definitions of inline functions must be in the header file. Like templates, the compiler needs to have access to the entire function definition to generate inline code.
>
>Remember, when you define something in a header file, you should use include guards (`#ifndef`, `#define`, `#endif`) or `#pragma once` to prevent multiple inclusion of the same header file, which could lead to redefinition errors.

### Using standard library header files
- Functions such as `std::cout` has been forward declared in the `iostream` header file, and defined somewhere else depending on the compiler being used.

### Forward declaration with header files
- One of the most common usage of the header files is to propagate forward declarations by including headers
- Example:

add.h
```
int add(int x, int y);
```

main.cpp
```C++
#include "add.h"
#include <iostream>

int main()
{
    std::cout << "The sum of 3 and 4 is " << add(3, 4) << '\n';
    return 0;
}
```

add.cpp
```C++
#include "add.h"

int add(int x, int y)
{
    return x + y;
}
```

- Reminder that function definitions inside header files is highly discouraged.

### Do not include source files
- `#include` directives should always be used to include header files - and never source files `.cpp`.
	- The preprocessor will allow including source files, but this invites many troubles along the way.

### Angled brackets vs. double quotes
- The way you specify the file to be included with `#include` directive can affect how the compiler searches for it.
- If you use quotation marks, the compiler first looks for the file in the same directory as the current file. If it doesn't find the file there, it then searches in the directories specified by the include path. This is typically used for including project-specific headers.
	- `#include "my_header.h"`
- If you use angled brackets, the compiler only searches in the directories specified by the include path. It does not look in the same directory as the current file. This is typically used for including headers from the standard library or other libraries installed on your system.
	- `#include <iostream>`

### Including header files from other directories
- One way to include header files from other directories is to use the relative path.
	- For example, `#include "../others/otherHeader.h"`
- Absolute path works too.
- Another way to include header files is to add the path to the header folder in the IDE's setting.
	- Visual Studio has a setting called "Include Directories"
- It's recommended to use the IDE's settings because it'd become a hassle to fix the code in every code file if there's ever a structural change to the project.

### Headers may include other headers
- It's common that a header file will need a declaration/definition that lives in a different header file. Because of this, header files will often include other header files.
- The additional header files that are included by other header files is called **transitive includes**.
- The content of the transitive includes are available for use in your code file. However, you generally should not rely on the content of headers that are included transitively. The implementation of header files may change over time, or be different across different systems.
	- This is easily avoided by explicitly including all of the header files the content of your code file requires.
- Unfortunately, there is no easy way to detect when your code file is accidentally relying on content of a header file that has been included by another header file.

### The include order of header files
- If your header files are written properly and includes everything they need, the order of inclusion shouldn't matter. What matters is if there is a missing include, it should be flagged by the compiler.
- To maximize the chance that missing includes will be flagged by compiler, order the `#include` directives as follows:
	1. The paired header files (header that pairs with a code file) from your project
	2. Other header files from your project
	3. 3rd party library headers
	4. Standard library headers

## Header guards
- A **header guard (aka include guard)** is a way to prevent a header file from being included multiple times in the same file or in other files that include it. This is important because including the same declarations multiple times can lead to redefinition errors.
- Here's how a typical header guard looks:

```C++
#ifndef MY_HEADER_H
#define MY_HEADER_H

// declarations here

#endif // MY_HEADER_H
```

- It's best practice to set the identifier as all caps, full filename, and ending with `_H` to indicate a header file is being included.
	- For example, `my_header.h` is referred to as `MY_HEADER_H`.
- Because there is a possibility that two separate header files from different directories may have a same filename (in large projects), it's recommended to use more complex/unique name in header guards. Examples:
	- `PROJECT_PATH_FILE_H`
	- `FILE_LARGE-RANDOM-NUMBER_H`
	- `FILE_CREATION-DATE_H`
- As an alternative to the `#ifndef`, `#define`, and `#endif` pattern, some compilers also support `#pragma once`, which serves the same purpose and is placed at the top of the file.
	- However, this method is not part of the C++ standard.

### Header guards do not prevent a header from being included into different code files
- As a reminder from previous lessons, the lifetime of a definition ends with the file. Meaning, a compiler will not consider a function defined in a file to be defined in another file.
- Taking the fact above into consideration, a header file that is included in multiple files will invoke a `define` directive even if the header guard is in place.
	- This means that if a function is defined in the header file and the header file is included in multiple code files, then the function will be defined multiple times - which leads to redefinition error that the linker raises.
	- The `#ifndef` directive will not stop a macro from being defined because the definition only lasts until the end of file.
- Note that main usage for the header guard is to prevent redefinition of a function within the same file.

### Custom type definition in header files
- While it's generally recommended not to define anything in header files, there are some cases where it's necessary to put the definitions in a header file.

>[!important]
>Defining custom types (like classes, structs, enums, typedefs, etc.) in header files is a common practice in C++ for several reasons:
>
>1. **Reusability**: By defining a custom type in a header file, you can `#include` that header file in any source file that needs to use the type. This promotes code reusability and helps keep your code organized.
>
>2. **Separation of Interface and Implementation**: It's a common practice in C++ to declare the interface (i.e., the class definition) in a header file and the implementation (i.e., the method definitions) in a corresponding source file. This helps to hide the implementation details and only expose the interface to the users of the class.
>
>3. **Compilation Efficiency**: When a type is defined in a header file, the compiler only needs to parse the type definition once, even if the header file is included in multiple source files. This can make the compilation process more efficient.
>
>4. **Linking**: When you define a type in a header file and include that header in multiple source files, the linker ensures that all the source files are referring to the same type. This is important for maintaining consistency and avoiding errors.
>
>Remember, when you define a type in a header file, you should use include guards or `#pragma once` to prevent multiple inclusion of the same header file, which could lead to redefinition errors.

## How to design a program
Skipped - refer to https://www.learncpp.com/cpp-tutorial/how-to-design-your-first-programs/

## Syntax and semantic errors
- A **syntax error** occurs when a statement is not valid according to the grammar of the C++ language.
	- Includes errors such as missing semicolons, using undeclared variables, mismatched parentheses, and etc.
- A **semantic error (aka logic error)** occurs when code is grammatically correct but does not produce the desired behavior or outcome. Unlike syntax errors which are easily identified and resolved by the compiler, semantic errors are not detected during the compilation process.
	- Division by 0 is an example of semantic error.
	- Using variables that are not initialized (therefore returns garbage) is an example of semantic error.
	- Having a function named `add()` only to have its result being a subtraction is an example of semantic error.
	- Statements that do not execute because it's placed after a return statement is an example of semantic error.

## Debugging tactics
- While printing out information in between steps is useful for debugging, it clutters the code and the output of the program. Additionally, it may require modification of your code which can introduce new bugs.
- There are ways to improve debug statements, such as using conditional compilation and using a logger.

### Debugging with conditional compilation
- Using conditional compilation (`#define`, `#ifdef`, and `#endif`), debugging statements can be turned on or off. For example:


```C++
#include <iostream>

#define ENABLE_DEBUG // comment out to disable debugging

int getUserInput()
{
#ifdef ENABLE_DEBUG
std::cerr << "getUserInput() called\n";
#endif
	std::cout << "Enter a number: ";
	int x{};
	std::cin >> x;
	return x;
}

int main()
{
#ifdef ENABLE_DEBUG
std::cerr << "main() called\n";
#endif
    int x{ getUserInput() };
    std::cout << "You entered: " << x << '\n';

    return 0;
}
```

- In the example above, debugging statements using `std::cerr` can be toggled on/off by un/commenting out `#define ENABLE_DEBUG`.
- Downside of this approach is that it creates more code clutter, and introduces possibility of human errors where debug features only work partially or none at all.

### Using a logger
- An alternative approach to conditionalized debugging is to send the debugging information to a a log.
- A **log** is a sequential record of events that have happened, usually time-stamped.
- The process of generating a log is called **logging**.
- Typically, logs are written to a file on a disk (called a **log file**) so they can be reviewed later.
- Log files have a few advantages:
	- Debug output is separated from normal output, therefore less cluttering and more readability.
	- Log files can be easily sent to other people for diagnosis.
- There are many logger libraries:
	- [plog](https://github.com/SergiusTheBest/plog): one recommended by the guide. It is a header-only logging library.
	- **spdlog**: This is a very fast, header-only/compiled, C++ logging library. It supports various log targets like rotating log files, daily log files, console logging, and more.
	- **easyloggingpp**: This is an extremely powerful, extendable, light-weight, fast performing, thread and type safe C++ logging library. It provides the ability to write logs in your own customized format.
	- **glog**: This is Google's C++ logging module. It provides application-level logging based on C++-style streams and various helper macros.
	- **Apache Log4cxx**: This is a logging framework for C++ patterned after Apache log4j. It uses Apache Portable Runtime for most platform-specific code and should be usable on any platform supported by APR.
	- **CppLogging**: This C++ Logging Library provides functionality to log different events with a high throughput in a multithreaded environment into different sinks (console, files, rolling files, syslog, etc.).
- An example of using `plog` for logging:

```C++
#include <plog/Log.h> // Step 1: include the logger headers
#include <plog/Initializers/RollingFileInitializer.h>
#include <iostream>

int getUserInput()
{
	PLOGD << "getUserInput() called"; // PLOGD is defined by the plog library

	std::cout << "Enter a number: ";
	int x{};
	std::cin >> x;
	return x;
}

int main()
{
	plog::init(plog::debug, "Logfile.txt"); // Step 2: initialize the logger

	PLOGD << "main() called"; // Step 3: Output to the log as if you were writing to the console

	int x{ getUserInput() };
	std::cout << "You entered: " << x << '\n';

	return 0;
}
```

- Note that debugging can be toggled on/off by replacing `plog::debug` with `plog::none` in step 2.

## Integrated debugger
Skipping, refer to https://www.learncpp.com/cpp-tutorial/using-an-integrated-debugger-stepping/

## Intro to fundamental data types
### Bits, bytes, and memory address
- To recap briefly, computers have RAM that is available for programs to use. When a variable is defined, a piece of that memory is set aside for that variable.
- The smallest unit of memory is a **binary digit (aka bit)**, which can hold a value of 0 or 1.
- Memory is organized into sequential units called **memory addresses**, where we can find and access the contents of memory at a particular location.
- In modern computer architectures, memory address is not assigned to each bit; instead, it gets assigned to each **byte** (8 sequential bits).
	- This isn't quite correct, but more on this later.

### Data types
- A **data type** is a sequence of bits that are arranged in a meaningful way.
	- For example, a sequence of bits `01000001` can be interpreted as an integer value of `65`.

### Fundamental data types
- C++ comes with built-in support for many different data types - such are called fundamental data types, basic types, primitive types, or built-in types.
- Fundamental data types include:
	- `float`
	- `double`
	- `bool`
	- `char`
	- `int`
	- `nullptr_t`
	- `void`
- Note that `string` is not a fundamental data type, instead it is considered a compound type. More on this later.
- Many of the types defined in newer versions of C++ use a `_t` suffix. This suffix means "type".

## Object sizes and the sizeof operator
- Although it's been stated before that each byte of memory gets assigned a unique address, it's not quite true - it's just an analogy to help understand memory better. The truth is that the amount of memory that an object uses is based on its data type, and most data types take up more than 1 byte of memory.

>[!important]
>Although we typically access memory through variable names and not directly via memory addresses, there are several reasons it is useful to know how much memory an object uses.
>
>1. **Memory Management**: When you're working on systems with limited memory resources, such as embedded systems or mobile devices, knowing the size of objects helps you manage memory more efficiently. This can prevent memory overflows and optimize the use of available memory.
>
>2. **Performance Optimization**: In performance-critical applications, such as game development or high-frequency trading systems, knowing the size of objects can help you optimize memory access patterns. Smaller objects can lead to better cache utilization and faster access times.
>
>3. **Data Structures**: When designing data structures, such as linked lists, trees, or hash tables, knowing the size of the objects stored in these structures can help you estimate the overall memory footprint and choose the most appropriate data structure for your needs.
>
>4. **Serialization and Networking**: When sending data over a network or saving it to a file, knowing the size of objects helps you allocate the correct amount of memory for serialization and deserialization. This ensures that data is transmitted or stored efficiently.
>
>5. **Debugging and Profiling**: When debugging memory-related issues, such as memory leaks or buffer overflows, knowing the size of objects can help you identify the source of the problem. Profiling tools often provide information about the memory usage of objects, which can be used to optimize your code.
>
>6. **Custom Allocators**: In scenarios where you implement custom memory allocators, knowing the size of objects is crucial for allocating and deallocating memory blocks correctly. This is often used in real-time systems or applications with specific memory management requirements.
>
>7. **Interfacing with Hardware**: When interfacing with hardware devices, such as graphics cards or network interfaces, knowing the size of objects can help you correctly configure memory buffers and ensure efficient data transfer between the CPU and the hardware.

- New programmers often focus too much on optimizing their code to use as little memory as possible. In most cases, this makes a negligible difference. Focus on writing maintainable code, and optimize only when and where the benefit will be substantive.

### Fundamental data type sizes
- The C++ standard does not define the exact size (in bits) for any of the fundamental types; it does define what minimum size should be under some assumptions:
	- A byte is 8 bits
	- Memory is byte addressable, so the smallest object is 1 byte
	- Floating point support is IEEE-754 compliant
	- Either 32-bit or 64-bit architecture computer is being used
- With the assumptions above, it can be said that:

![[Pasted image 20240731154252.png]]

- If a program must assume that a type has a certain size, it's possible to have the compiler fail a build if it is compiled on an architecture where this assumption is not true. More on this later.

### The sizeof operator
- C++ provides an operator named `sizeof()` that takes either a type or a variable and returns its size in bytes. For example:
	- `sizeof(bool)` should return `1` (byte).
	- `int x = 8; sizeof(x);` should return `4` (bytes).
- Note that using `sizeof()` on an incomplete type (such as `void`) will result in a compilation error.

>[!important]
>Types that use less memory is not always faster to process than types that use more memory.
>CPUs are often optimized to process data of a certain size (e.g. 32 bits), and types that match that size may be processed quicker.

## Signed integers
- An integer is an integral type that can represent positive and negative whole numbers, including 0.
- C++ has 4 primary fundamental integer types available:
	- `short` - 16 bits
	- `int` - 16 bits
	- `long` - 32 bits
	- `long long` - 32 bits
- Note that the larger integers can hold bigger range of numbers.
- Technically, the `bool` and `char` types are considered to be integral types because they store values as integer values. But for now, these will be excluded from discussion.
- The attribute of a number being positive, negative, or zero is called the number's **sign**.
- By default, integers are **signed**, meaning that the number's sign is stored as part of the number. It also means that it can hold both positive and negative numbers (and 0).
- In binary representation, a single bit is used for a **sign bit**, which stores the sign of the number. The non-sign bits are called the **magnitude bits** which determine the magnitude of the number.

### Defining signed integers
- Here is the preferred way to define the four types of signed integers:

```C++
short x;
int y;
long z;
long long w;
```

- The integer types can take an optional `signed` keyword, which by convention is typically placed before the type name:

```C++
signed short x;
signed int y;
signed long z;
signed long long w;
```

- The `signed` keyword should not be used though, as it is redundant since integers are signed by default.

### Signed integer ranges
- A variable with `n` bits can hold $2^n$ possible values.
- The set of specific values that a data type can hold is called **range**.
- The range of an integer variable is determined by two factors: its size in bits, and its sign.
- By definition, an 8-bit signed integer has a range of `-128` to `127` (inclusive).
	- An 8-bit integer can hold `256` possible values. Because `1` bit is used for sign, `7` bits are used for the magnitude - which means `128` values for each sign.
- An n-bit signed variable has a range of $[-(2^{n-1}), 2^{n-1}-1]$.

### Overflow
- When a value greater than its range is assigned to an integer, an undefined behavior called **overflow** occurs.
	- For example, assigning `140` to an 8-bit signed integer causes an overflow.

>[!important]
>An overflow occurs when a calculation produces a result that exceeds the maximum value that can be stored in a given data type. This can lead to several types of errors and unexpected behavior:
>
>1. **Wraparound**: In many systems, when an overflow occurs, the value wraps around to the minimum value of the data type. For example, if an `unsigned int` exceeds its maximum value, it wraps around to zero. This can lead to incorrect calculations and logic errors.
>
>2. **Data Corruption**: Overflow can cause data corruption, where the value stored in a variable is not what was intended. This can lead to unpredictable behavior and bugs that are difficult to trace.
>
>3. **Security Vulnerabilities**: Overflow can be exploited by attackers to cause buffer overflows, which can lead to security vulnerabilities such as arbitrary code execution or denial of service attacks.
>
>4. **Program Crashes**: In some cases, overflow can cause a program to crash or terminate unexpectedly. This can happen if the overflow leads to invalid memory access or other critical errors.
>
>5. **Loss of Precision**: Overflow can result in a loss of precision, especially in floating-point calculations. This can lead to inaccurate results and affect the reliability of numerical computations.
>
>6. **Undefined Behavior**: In some programming languages, overflow can lead to undefined behavior, where the program's behavior is unpredictable and may vary depending on the compiler or runtime environment.
>
>To prevent overflow, it's important to use appropriate data types, perform bounds checking, and use libraries or language features that provide safe arithmetic operations.

### Integer division
- When doing division with two integers (called **integer division**), C++ always produces an integer result. Since integers can't hold fractional values, any fractional portion is simply dropped (NOT rounded).
- Integer division is safe to use and desirable in certain cases.

## Unsigned integers
- **Unsigned integers** are integers that can only hold non-negative whole numbers (0 and up).
	- It does not use a sign bit, which means all bits are magnitude bits.
- To define an unsigned integer, `unsigned` keyword is placed before the type.
	- For example, `unsigned int x;`
- An n-bit unsigned variable has a range of $[0, 2^n-1]$.
	- The range of an 8-bit unsigned integer is `0` to `255`.

>[!warning] Unsigned integer overflow?
>There isn't technically an overflow for unsigned integer. When a number beyond the type's range is given, the number simply "wraps around"; that is to say, the number is divided by one greater than the largest number of the type and only the remainder is kept.
>
>For example, assigning a value of `280` for 8-bit unsigned integer results in `280 % 256 = 24`.
>
>Wrap around works with negative numbers a bit differently. The result is the sum of the number and one greater than the largest number of the type.
>
>For example, assigning a value of `-1` for 8-bit unsigned integer results in `256 + (-1) = 255`.
>
>Most compilers will give a warning when an overflow occurs, with context such as "the integer literal is out-of-range for the given type".

>[!sidenote] Nuclear Gandhi Meme
>In computer science, an example of unsigned integer overflow often includes a meme known as "Nuclear Gandhi". In a PC game Civilization, Gandhi was known for being nuke crazy despite his expected passive nature. People speculated that Gandhi's aggression setting was related to unsigned integer overflow; however, the devs denied this to be true.
>
>For fun reading, refer to https://en.wikipedia.org/wiki/Nuclear_Gandhi

- Because of the wrap-around behavior of unsigned integers, it's recommended to avoid using unsigned integers.

---

Unsigned integers are useful in several real-life scenarios where negative values are not meaningful or allowed. Here are some examples:

1. **Counting and Indexing**: When you need to count items or index arrays, negative values don't make sense. Using unsigned integers ensures that your counts and indices are always non-negative.

```cpp
std::vector<int> myVector(10);
for (unsigned int i = 0; i < myVector.size(); ++i) {
    // Do something with myVector[i]
}
```

2. **Memory Addresses**: Memory addresses are inherently non-negative. Using unsigned integers to represent memory addresses ensures that you don't accidentally use negative values.

```cpp
uintptr_t address = reinterpret_cast<uintptr_t>(ptr);
```

3. **Bit Manipulation**: When performing bitwise operations, unsigned integers are often used because they provide a clear representation of the bits without the complications of sign bits.

```cpp
unsigned int flags = 0b1010;
flags |= 0b0100; // Set a bit
```

4. **File Sizes and Offsets**: File sizes and offsets are always non-negative. Using unsigned integers to represent these values ensures that you don't accidentally use negative values.

```cpp
std::ifstream file("example.txt", std::ios::binary);
file.seekg(0, std::ios::end);
unsigned int fileSize = file.tellg();
```

5. **Network Protocols**: Many network protocols use unsigned integers to represent various fields, such as packet lengths, sequence numbers, and port numbers. Using unsigned integers ensures that these values are always non-negative.

```cpp
unsigned short port = 8080;
```

6. **Graphics and Game Development**: In graphics and game development, unsigned integers are often used to represent color values, texture coordinates, and other attributes that are inherently non-negative.

```cpp
unsigned char red = 255;
unsigned char green = 128;
unsigned char blue = 64;
```

These are just a few examples of where unsigned integers are necessary and useful. Using unsigned integers in these scenarios helps to prevent errors and ensures that your code behaves as expected.

---

## Fixed-width integers and size_t
### Fixed-width integers
- Although most data types do not have definitive memory sizes, there are some that are guaranteed to be the same size on any architecture.
- ![[Pasted image 20240801063805.png]]
- C++ officially adopted these fixed-width integers as part of C++11. They can be accessed by including the `<cstdint>` header, where they are defined inside the `std` namespace.
- An example:

```C++
#include <cstdint> // for fixed-width integers
#include <iostream>

int main()
{
    std::int16_t i{5};
    std::cout << i << '\n';
    return 0;
}
```

- The fixed-width integers have two downsides that are typically raised:
	- They are not guaranteed to be defined on all architectures, though this is highly unlikely.
	- They may be slower to process on some architectures depending on width (32-bit/64-bit), though it's hard to know without actually measuring.

### Fast and least integers
- As alternative to fixed-width integers, C++ also defines two sets of integers that are guaranteed to be defined: the fast integers, and least integers.
- The fast integers provide the fastest signed/unsigned integer type with at least a certain width.
	- For example, `std::int_fast32_t` will give the fastest signed integer type that's at least 32 bits.
	- By fastest, it means the integral type that can be processed most quickly by the CPU.
- The least integers provide the smallest signed/unsigned integer type with at least a certain width.
	- For example, `std::uint_least32_t` will give the smallest unsigned integer type that's at least 32 bits.
- The fast and least integers have their own downsides:
	- Not many programmers actually use them, and a lack of familiarity can lead to errors.
	- The fast types can lead to memory wastage, as their actual size may be larger than indicated.
	- Because the size of the fast/least integers can vary, it's possible your program may exhibit different behaviors on different architectures (think overflow and wrap around).

#### Fast integers : usage and trade-offs

>[!important] Fast integers usage
>In C++, fast integers, such as `int_fast32_t` or `uint_fast32_t`, are used when you need the fastest possible integer type that is at least a certain width (e.g., 32 bits). These types are particularly useful in performance-critical applications where the speed of integer operations is crucial. Here are some scenarios where fast integers might be necessary:
>
>1. **High-Performance Computing**: In applications like scientific computing, simulations, or real-time data processing, where every millisecond counts, using fast integers can help optimize performance.
>2. **Embedded Systems**: In resource-constrained environments, such as microcontrollers or embedded systems, fast integers can help improve the efficiency of the code.
>3. **Game Development**: When developing games, especially those with complex physics or graphics calculations, using fast integers can help achieve smoother and more responsive gameplay.
>4. **Algorithm Optimization**: In algorithms that involve a large number of integer operations, such as sorting, searching, or mathematical computations, fast integers can help reduce the overall execution time.
>
>Fast integers are typically chosen by the compiler to be the most efficient type for the target architecture, ensuring that operations on these integers are as fast as possible.

>[!important] Fast integers trade-offs
>Using fast integers in C++ comes with several trade-offs:
>
>Advantages:
>1. **Performance**: Fast integers are optimized for the target architecture, which can lead to faster execution of integer operations.
>2. **Clarity**: Using types like `int_fast32_t` clearly indicates the intent to use the fastest available integer type of at least 32 bits.
>
>Disadvantages:
>1. **Portability**: The actual size of fast integers can vary between different platforms. For example, `int_fast32_t` might be 32 bits on one platform and 64 bits on another. This can lead to inconsistencies when porting code.
>2. **Memory Usage**: Fast integers might use more memory than their fixed-width counterparts. For instance, on a 64-bit system, `int_fast32_t` could be 64 bits, which uses more memory than a 32-bit integer.
>3. **Predictability**: The size and behavior of fast integers are determined by the compiler and the target architecture, which can make it harder to predict their performance characteristics.
>
>In summary, while fast integers can provide performance benefits, they may introduce challenges related to portability, memory usage, and predictability. It's essential to consider these trade-offs based on the specific requirements of your application.

#### Least integers : usage and trade-offs

>[!important] Least integers usage
>In C++, least integers, such as `int_least32_t` or `uint_least32_t`, are used when you need the smallest integer type that is at least a certain width (e.g., 32 bits). These types are particularly useful in scenarios where memory efficiency is more critical than speed. Here are some common use cases:
>
>1. **Memory-Constrained Environments**: In systems with limited memory, such as embedded systems or IoT devices, using the smallest possible integer type helps conserve memory.
>2. **Data Storage**: When storing large amounts of data, such as in databases or file formats, using the smallest integer type can reduce the overall storage requirements.
>3. **Network Communication**: In network protocols, where data needs to be transmitted efficiently, using the smallest integer type can help minimize the amount of data sent over the network.
>
>For example, if you need to store a large array of integers and memory usage is a concern, using `int_least32_t` ensures that each integer uses the minimum amount of memory while still being at least 32 bits wide.

>[!important] Least integers trade-offs
>Using least integers in C++ comes with its own set of trade-offs:
>
>Advantages:
>1. **Memory Efficiency**: Least integers, such as `int_least32_t`, ensure that you are using the smallest possible integer type that meets the required width. This can help conserve memory, especially in memory-constrained environments.
>2. **Portability**: Least integers provide a consistent minimum width across different platforms, which can help ensure that your code behaves consistently when ported to different systems.
>
>Disadvantages:
>1. **Performance**: Since least integers prioritize memory efficiency over speed, they might not be the fastest integer type available on a given platform. This can lead to slower execution times compared to using fast integers.
>2. **Predictability**: The actual size of least integers can vary between platforms. For example, `int_least32_t` might be 32 bits on one platform and 64 bits on another. This variability can make it harder to predict the performance characteristics of your code.
>3. **Complexity**: Using least integers can add complexity to your code, as you need to be aware of the potential differences in integer sizes across platforms and handle them appropriately.
>
>In summary, while least integers can help optimize memory usage and ensure portability, they may introduce challenges related to performance, predictability, and complexity. It's essential to weigh these trade-offs based on the specific requirements of your application.

### 8-bit fixed-width integers behave like chars
- Due to an oversight in the C++ specification, most compilers define and treat `std::int8_t` and `std::uint8_t` (and the corresponding fast and least fixed-width types) identically to types `signed char` and `unsigned char` respectively.
	- This means that 8-bit fixed-width integers may behave differently than the rest of the fixed-width types, which can lead to errors.
	- This behavior is system-dependent, so a program that behaves correctly on one architecture may not compile or behave correctly on another architecture.
- When storing integral values where a specific size is important, it's generally best to avoid these 8-bit fixed-width integers (use 16-bit instead).

>[!important]
>The behavior of 8-bit fixed-width integers (`int8_t` and `uint8_t`) being treated like `char` types in C++ is due to an oversight in the C++ specification. Most compilers define and treat `std::int8_t` and `std::uint8_t` (and their corresponding fast and least fixed-width types) identically to `signed char` and `unsigned char`, respectively³.
>
>Reasons for This Behavior:
>1. **Historical Context**: The C and C++ standards have historically treated `char` as a distinct type that can be used for both character data and small integers. This dual-purpose nature of `char` has carried over to fixed-width integer types.
>2. **Compiler Implementation**: Compilers often implement `int8_t` and `uint8_t` as aliases for `signed char` and `unsigned char` to maintain compatibility with existing code and to simplify the implementation³.
>
>Why It Hasn't Been Fixed:
>1. **Backward Compatibility**: Changing the behavior of 8-bit fixed-width integers would break a significant amount of existing code that relies on the current behavior. Maintaining backward compatibility is a crucial consideration in the evolution of programming languages.
>2. **Limited Impact**: The impact of this behavior is relatively limited to specific use cases involving 8-bit integers. In most scenarios, the behavior does not cause significant issues, so there has been less urgency to address it.
>3. **Standardization Process**: Any changes to the C++ standard go through a rigorous standardization process, which involves extensive discussion and consensus-building among the community. Given the limited impact and the need for backward compatibility, this issue has not been prioritized for change.

### Best practices for integral types
- It's better to be correct than fast, and better to fail at compile time than runtime.
	- If an integral type with a fixed size is needed, use the fixed-width type; avoid fast/least types.
- <mark class="hltr-green">Prefer</mark> `int` when the size of the integer doesn't matter.
- <mark class="hltr-green">Prefer</mark> `std::int#_t` when storing a quantity that needs a guaranteed range.
- <mark class="hltr-green">Prefer</mark> `std::uint#_t` when doing bit manipulation or where well-defined wrap-around behavior is required.
- <mark class="hltr-red">Avoid</mark> `short` and `long` integers; use a fixed-width integers instead.
- <mark class="hltr-red">Avoid</mark> unsigned types for holding quantities.
- <mark class="hltr-red">Avoid</mark> 8-bit fixed-width integers
- <mark class="hltr-red">Avoid</mark> the fast/least fixed-width types
- <mark class="hltr-red">Avoid</mark> compiler-specific fixed-width integers

### what is std::size_t?
- The `sizeof()` returns the size (in bytes) of a given variable/type; the type of the value that it returns is `std::size_t`, which is an alias for an implementation-defined unsigned integral type.
	- In other words, the compiler decides if `std::size_t` is an unsigned int, an unsigned long, an unsigned long long, etc.
- `std::size_t` is used to represent the byte-size or length of objects.
- `std::size_t` is defined in a number of different headers; the best header to include is `<cstddef>`, as it contains the least number of other defined identifiers.
- Using a `sizeof()` does not require a header, even though it returns a value whose type is `std::size_t`.
- `std::size_t` is guaranteed to be unsigned and at least 16 bits, but on most systems will be equivalent to the address-width of the application.
	- For example, for 32-bit application, it will be 32-bit unsigned integer.

>[!note] `std::size_t` and upper limit on the size of an object
>Because `std::size_t` has a maximum value that it can return, it means that `sizeof()` cannot be used on an object that is larger than the maximum value (in bytes). Compilers will use this value (sometimes a half of it) as the upper limit on the size of an object that can be created.
>
>On 32/64 bit applications, this is hardly an issue. However, on 8/16 bit applications, this imposes a significant constraint on the size of objects.


## Floating point numbers
### Floating point data types
- A floating point type is a data type that can hold a number with a fractional component.
- There are three standard floating point types:
	- A single-precision `float`, typical width of 4 bytes
	- A double-precision `double`, typical width of 8 bytes
	- An extended-precision `long double`, typical width of 8, 12, or 16 bytes
- The **precision** of a floating point type defines how many significant digits it can represent without information loss.
	- `float` has 6 to 9 digits of precision. This means number with 6 significant digits are represented exactly, but beyond that is questionable.
	- `double` has 15 and 18 digits of precision.
	- `long double` has 15, 18, or 33 digits of precision.
- On modern architectures, floating point representation for `float` and `double` almost always follows IEEE 754 binary format; meaning, a `float` is 4 bytes and a `double` is 8 bytes.
- It's recommended to avoid `long double`.

>[!warning]
>From this point on, the guide will continue with the assumption that the compiler is using IEEE 754 format for `float` and `double`.

- Note that suffix `f` is attached to the value that is assigned to a `float` variable. For example, `float x = 1.0f;`.
	- The `f` suffix is not attached to the value that is assigned to a `double` variable.
	- The `f` suffix distinction is important because implicit conversion can occur - which is unnecessary.

### Floating point range
- Assuming IEEE 754 representation for 4, 8, and 16 byte representations:
	- 4 bytes :: $±1.18 \times 10^{-38}$ to $±3.4 x 10^{38}$ and $0.0$ :: with precision 6-9 significant digits (typically 7)
	- Skipping the rest.. this should just be looked up whenever it's necessary.

### Printing floating point numbers
- Consider the following example:

```C++
#include <iostream>

int main()
{
	std::cout << 5.0 << '\n';
	std::cout << 6.7f << '\n';
	std::cout << 9876543.21 << '\n';

	return 0;
}
```

- The results of the above example:

```
5
6.7
9.876543e+06
```

- Note that `std::cout` does not print the fractional part that is `0`.
- Note that `std::cout` prints numbers in scientific notation.
	- Scientific notation being representing values as $x * 10^n$, where `e+n`.
- `std::cout` has a default precision of 6, which matches with the minimum precision of a `float`. Significant digits beyond this limit will be truncated.
- Consider the following example:

code
```C++
#include <iostream>

int main()
{
    std::cout << 9.87654321f << '\n';
    std::cout << 987.654321f << '\n';
    std::cout << 987654.321f << '\n';
    std::cout << 9876543.21f << '\n';
    std::cout << 0.0000987654321f << '\n';

    return 0;
}
```

result
```C++
9.87654
987.654
987654
9.87654e+006
9.87654e-005
```

- In the above example, it can be seen that all the numbers are printed up to only 6 significant digits, and the rest are truncated (excluding the scientific notation).
- The default precision of `std::cout` can be overridden by using an output manipulator function called `std::setprecision()`, which is defined in the `<iomanip>` header. For example:

code
```C++
#include <iomanip> // for output manipulator std::setprecision()
#include <iostream>

int main()
{
    std::cout << std::setprecision(17); // show 17 digits of precision
    std::cout << 3.33333333333333333333333333333333333333f <<'\n';
    std::cout << 3.33333333333333333333333333333333333333 << '\n';

    return 0;
}
```

result
```C++
3.3333332538604736
3.3333333333333335
```

- In the example above, note that the precision of the result is limited/differs by the data types, `float` and `double`.

>[!important]
>Output manipulators (and input manipulators) are sticky; meaning that they will remain set after being set once.
>
>The one exception is `std::setw`, which sets the width of the printed text. Some IO operations reset this width, so `std::setw` should be used every time it is needed.

- Note that the precision don't just impact fractional numbers, they also impact whole numbers.

### Rounding errors & comparisons
- When precision is lost because a number can't be stored precisely, it is called a **rounding error**.
- Comparing floating point numbers can get tricky because rounding errors often give unexpected result.
- Take below example:

code
```C++
#include <iomanip> // for std::setprecision()
#include <iostream>

int main()
{
    double d{0.1};
    std::cout << d << '\n'; // use default cout precision of 6
    std::cout << std::setprecision(17);
    std::cout << d << '\n';

    return 0;
}
```

result
```C++
0.1
0.10000000000000001
```

- In the above example, note that the variable `d` outputs slightly different values - which is caused by rounding error.
	- In this case, `double` has precision up to 16 significant digits. When `std::cout` outputs the value with default precision of 6, it simply truncates the value and outputs `0.1`. However, when the precision for `std::cout` is set to 17, it went beyond the precision for `double` - which caused the rounding error, outputting `0.10000000000000001`.
- There are cases when the rounding error is even more imperceptible:

code
```C++
#include <iomanip> // for std::setprecision()
#include <iostream>

int main()
{
    std::cout << std::setprecision(17);

    double d1{ 1.0 };
    std::cout << d1 << '\n';

    double d2{ 0.1 + 0.1 + 0.1 + 0.1 + 0.1 + 0.1 + 0.1 + 0.1 + 0.1 + 0.1 };
    std::cout << d2 << '\n';

    return 0;
}
```

result
```C++
1
0.99999999999999989
```

- In the above example, variable `d2` should add up to `1.0` but it does not.
	- It's important to note that mathematical operations (such as addition and multiplication) tend to make rounding errors grow.
- It's always best to be wary of using floating point numbers for financial or currency data.

---

Handling floating-point rounding errors in C++ can be challenging due to the inherent limitations of representing decimal numbers in binary format. Here are some best practices to minimize and manage these errors:

Use Higher Precision Types
- **Double Precision**: Use `double` instead of `float` for higher precision. `double` provides more significant digits and a larger range.
- **Long Double**: For even higher precision, consider using `long double`.

Use Arbitrary-Precision Libraries
- **GMP (GNU Multiple Precision Arithmetic Library)**: This library provides arbitrary-precision arithmetic, allowing you to perform calculations with very high precision¹.
- **Boost.Multiprecision**: Part of the Boost C++ Libraries, it offers support for high-precision arithmetic¹.

Avoid Subtracting Nearly Equal Numbers
- **Catastrophic Cancellation**: Subtracting two nearly equal numbers can lead to significant loss of precision. Try to reformulate the problem to avoid such operations.

Use Kahan Summation Algorithm
- **Kahan Summation**: This algorithm helps reduce the error when summing a sequence of floating-point numbers by keeping a running compensation for lost low-order bits².

Normalize Values
- **Scaling**: Normalize values to a similar range before performing arithmetic operations. This can help reduce rounding errors.

Use Decimal Fixed-Point Arithmetic
- **Fixed-Point Representation**: For applications requiring precise decimal representation, consider using fixed-point arithmetic, where numbers are represented as integers scaled by a fixed factor².

Properly Format Output
- **Set Precision**: Use `std::setprecision` and `std::fixed` to control the number of significant digits when outputting floating-point numbers².
  ```cpp
  #include <iostream>
  #include <iomanip>

  int main() {
      double value = 0.1;
      std::cout << std::fixed << std::setprecision(17) << value << std::endl;
      return 0;
  }
  ```

Understand Floating-Point Arithmetic
- **Educational Resources**: Read "What Every Computer Scientist Should Know About Floating-Point Arithmetic" by David Goldberg to gain a deeper understanding of floating-point behavior².

By following these practices, you can minimize the impact of floating-point rounding errors in your C++ programs. If you have any specific scenarios or further questions, feel free to ask!

¹: [Stack Overflow](https://stackoverflow.com/questions/3420009/avoid-rounding-error-floating-specifically-c)
²: [Learn Microsoft](https://learn.microsoft.com/en-us/cpp/build/why-floating-point-numbers-may-lose-precision?view=msvc-170)

Source: Conversation with Copilot, 2024. 8. 2.
(1) avoid rounding error (floating specifically) c++ - Stack Overflow. https://stackoverflow.com/questions/3420009/avoid-rounding-error-floating-specifically-c.
(2) c++ - What is a simple example of floating point/rounding error .... https://stackoverflow.com/questions/249467/what-is-a-simple-example-of-floating-point-rounding-error?noredirect=1.
(3) c++ - Float point numbers and incorrect result due to rounding behavior .... https://stackoverflow.com/questions/40372148/float-point-numbers-and-incorrect-result-due-to-rounding-behavior.
(4) Why Floating-Point Numbers May Lose Precision. https://learn.microsoft.com/en-us/cpp/build/why-floating-point-numbers-may-lose-precision?view=msvc-170.
(5) floating point - Analyzing Numerical Error in C++ Function .... https://scicomp.stackexchange.com/questions/1007/analyzing-numerical-error-in-c-function.
(6) undefined. http://www.learncpp.com/cpp-tutorial/25-floating-point-numbers/.

---

### NaN and Inf
- There are two special categories of floating point numbers:
	- `Inf` : represents infinity, which can be positive or negative.
	- `NaN` : represents a value that is "Not a Number".
- `NaN` and `Inf` are only available if the compiler uses a specific format (IEEE 754) for floating point numbers.
- Consider the following example:

code
```C++
#include <iostream>

int main()
{
    double zero {0.0};
    double posinf { 5.0 / zero }; // positive infinity
    std::cout << posinf << '\n';

    double neginf { -5.0 / zero }; // negative infinity
    std::cout << neginf << '\n';

    double nan { zero / zero }; // not a number (mathematically invalid)
    std::cout << nan << '\n';

    return 0;
}
```

result
```console
1.#INF
-1.#INF
1.#IND
```

- Note that the results of printing `Inf` and `NaN` are platform specific, so results may vary.
	- Like in the example above, `IND` (for indeterminate) was printed for `NaN`.
- It's best practice to avoid division by zero.

## Boolean values
- Boolean values are values that are either `ture` or `false`, represented by a type called `bool`.
- The logical NOT operator `!` reverses the boolean value.
	- For example, `!false` is `true`.
- Boolean values are not actually stored as the words "true" or "false". Instead, they are stored as integral values; `1` for `true`, and `0` for `false`.
	- Boolean values are evaluated as such; `std::cout << true;` will print `1`.
- In order to print the boolean words `true` or `false`, `std::boolalpha` must be called (once).
	- e.g. `std::cout << std::boolalpha;`
	- Use `std::noboolalpha` to turn it back off.
- `bool` can be initialized using `true`/`false` or `1`/`0`.
	- e.g. `bool machineOn = 1;`
	- Uniform initialization with integral values other than 0 or 1 causes an error.
	- Copy initialization with integral values other than 0 or 1 does NOT cause an error, and is converted to `true`.
- When using `std::cin` to get user input for a boolean value, note that it only accepts `0` or `1` instead of full words like `true` or `false`.
- Boolean values are often used to as the return values for functions that check whether something is true or not.
	- Such functions are typically named starting with the word `is` (e.g. `isEqual`), or `has` (e.g. `hasCommonDivisor`).
- Comparison operators such as `==`, `!=`, `>`, `<`, and etc. will return a `bool` value.

## Intro to if statements
- A **condition** (also called a conditional expression) is an expression that evaluates to a Boolean value.
	- e.g. `true`, `1 == 1`, `1 != 0`, `(1+1) == 2`
- An **if statement** is a conditional statement that executes a code if some condition is true.
	- e.g. `if (condition==true) executeCodeA();`
- If statement can also execute when some condition is false, by using `else`.
	- e.g. `else executeCodeB();`
- If statement can be chained so that several conditions are checked one by one, by using `else if`.
	- e.g. `else if (condition==true) executeCodeC();`
- Integral values `0` and `1` can be used for conditional expression; they'll be implicitly converted to boolean values.
	- Values higher than `1` can be used too, but it will cause a warning.
- A return statement that is not the last statement in a function is called an **early return**.
	- Such a statement will cause the function to return to the caller wen the return statement is executed.
- If statements and early returns pair up well together.

>[!warning] Conditional statements have their own scope
>When a variable is declared within a conditional statement (such as if/else block), that variable is only accessible within the scope of that block.
>
>While a variable declared outside the conditional statement can be initialized inside the conditional statement, it cannot be initialized with a reference to the variable that's defined within the conditional statement.



## Chars
- The `char` data type is designed to hold a single character.
	- A **character** can be a single letter, number, symbol, or whitespace.
- The `char` type is an integral type, meaning the underlying value is stored as an integer.
- The integer stored by a `char` type is interpreted as an ASCII character, which defines a particular way to represent English characters (plus a few other symbols) as numbers between 0 and 127 (called ASCII code).
	- ASCII stands for American Standard Code for Information Interchange
	- For example, ASCII code 97 is interpreted as the character 'a'
- Character literals are always placed between single quotes.
- ASCII codes 0~31 and 127 are called the unprintable chars - due to the fact that they are now obsolete.
- `char` can be initialized by using character literals.
	- e.g. `char letterA = 'a';`
- `char` can also be initialized by using integers as well, but it should be avoided if possible.
- `char` is defined by C++ to always be 1 byte in size.
	- By default, a char may be signed or unsigned (though it's usually unsigned).
- **Escape sequences** are special characters that always starts with backlash `\`.
	- ![[Pasted image 20240802123930.png]]

- Reminder: [[#8-bit fixed-width integers behave like chars]]

### Single vs double quotes
- Single chars are always put in single quotes (e.g. `'a'`, `'+'`, `'5'`).
	- A `char` can only represent one symbol.
- Text between double quotes (e.g. `"hello world!"`) is treated as a string of multiple characters.
	- More on strings later.

### Avoid multicharacter literals
- For backwards compatibility reasons, many C++ compilers support **multicharacter literals**, which are char literals that contain multiple characters (e.g. `'56'`). If supported, these have an implementation-defined value (meaning it varies depending on the compiler).
	- Multicharacter literals should be avoided because they are NOT part of the C++ standard, and their value is NOT strictly defined.
- Multicharacter literal support sometimes causes confusion for novice programmers. Consider the following example:

```C++
#include <iostream>

int add(int x, int y)
{
	return x + y;
}

int main()
{
	std::cout << add(1, 2) << '/n';

	return 0;
}
```

- In the above example, `3` followed by a newline is expected to print but instead, `312142` might be printed. This is because the newline character was mistyped with forward slash instead of backward slash, and `/n` multicharacter literals has implementation-defined value of `12142`.

### Other char types
- There are other variations of `char`:
	- `wchar_t`
	- `char8_t`, `char16_t`, `char32_t`
- `wchar_t` should be avoided in almost all cases (except when interfacing with the Windows API).
	- Its size is implementation defined, and is not reliable.
	- It has largely been deprecated.

#### Unicode support
- The most well-known mapping outside of ASCII is the **Unicode standard**, which maps over 144,000 integers to characters in many different languages.
	- Because Unicode contains so many code points, a single Unicode code point needs 32-bits to represent a character (called **UTF-32**).
	- Unicode characters can also be encoded using multiple 16-bit or 8-bit characters (called **UTF-16** and **UTF-8** respectively).
- `char8_t`, `char16_t`, and `char32_t` are data types that support Unicode characters.
- `char16_t` and `char32_t` were added to C++11 to provide explicit support for 16-bit and 32-bit Unicode characters.
	- These char types have the same size as `std::uint_least16_t` and `std::uint_least32_t` respectively (but are distinct types).
- `char8_t` were added in C++20 to provide support for 8-bit Unicode.
	- It is a distinct type that uses the same representation as `unsigned char`.

>[!important]
>The differences between UTF-8, UTF-16, and UTF-32 primarily lie in how they encode Unicode characters and their efficiency in terms of space and processing:
>
>UTF-8
>- **Encoding**: Uses 8, 16, 24, or 32 bits (1 to 4 bytes) to encode a character.
>- **Advantages**: 
>    - Efficient for texts with a lot of ASCII characters, as it uses only 1 byte for these characters.
>    - No issues with endianness (byte order).
>    - Widely used in web and network protocols.
>- **Disadvantages**: 
>    - Can be less efficient for texts with many non-ASCII characters, as it may require up to 4 bytes per character.
>
>UTF-16
>- **Encoding**: Uses 16 or 32 bits (2 or 4 bytes) to encode a character.
>- **Advantages**: 
>    - More efficient than UTF-8 for texts with many non-ASCII characters, as it uses 2 bytes for most characters.
>    - Commonly used in environments like Windows and JavaScript.
>- **Disadvantages**: 
>    - Can be less efficient for texts with many ASCII characters, as it uses at least 2 bytes per character.
>    - Endianness can be an issue, requiring byte order marks (BOM) to indicate the byte order.
>
>UTF-32
>- **Encoding**: Uses 32 bits (4 bytes) to encode a character.
>- **Advantages**: 
>    - Fixed-width encoding, making it simple to calculate the number of characters.
>    - No need for decoding to access individual characters.
>- **Disadvantages**: 
>    - Very space-inefficient, as it uses 4 bytes for every character, regardless of its actual size.
>    - Rarely used due to its high memory consumption.
>
>Summary
>- **UTF-8** is best for texts with many ASCII characters and is widely used in web and network protocols.
>- **UTF-16** is more efficient for texts with many non-ASCII characters and is used in environments like Windows and JavaScript.
>- **UTF-32** is simple but space-inefficient, making it less commonly used.

## Intro to type conversion and static_cast
### Intro to implicit type conversion
- The process of converting a value from one type to another type is called **type conversion**.
- When the compiler does type conversion on our behalf without us explicitly asking, we call this **implicit type conversion**.
- Refer to [[#Implicit type conversion]]

>[!important]
>Implicit type conversion, also known as automatic type conversion or coercion, is performed automatically by the compiler when one data type is required, but a different data type is supplied. This process allows for seamless integration of different data types in expressions and function calls without requiring explicit casts from the programmer.
>
>Common Occurrences of Implicit Type Conversion:
>
>1. **Arithmetic Operations**:
>    - When performing arithmetic operations between different data types, the compiler automatically converts the operands to a common type. For example, when adding an `int` and a `double`, the `int` is converted to a `double` before the addition.
>   ```cpp
>   int a = 5;
>   double b = 3.2;
>   double result = a + b; // 'a' is implicitly converted to double
>   ```
>
>2. **Function Calls**:
>    - When passing arguments to a function, if the argument types do not match the parameter types, the compiler performs implicit conversions to match the parameter types.
>   ```cpp
>   void printDouble(double value) {
>       std::cout << value << std::endl;
>   }
>   int x = 10;
>   printDouble(x); // 'x' is implicitly converted to double
>   ```
>
>3. **Assignment Operations**:
>    - When assigning a value of one type to a variable of another type, the compiler performs implicit conversion to match the variable's type.
>   ```cpp
>   double y = 7; // '7' is implicitly converted to double
>   ```
>
>4. **Boolean Contexts**:
>    - When using non-boolean values in boolean contexts (e.g., conditions in `if` statements), the compiler implicitly converts the values to `bool`.
>   ```cpp
>   int z = 0;
>   if (z) { // 'z' is implicitly converted to bool
>       std::cout << "This won't print." << std::endl;
>   }
>   ```
>
>Summary
>Implicit type conversions help simplify code by allowing different data types to interact seamlessly. However, it's essential to be aware of potential pitfalls, such as loss of precision or unintended behavior, especially when dealing with mixed data types.

### Type conversion produces a new value
- Important thing to note is that the type conversion does not change the type of the variable, but rather the type of the input value gets converted to match the type of the variable.
	- For example, if `float` value of `5.0f` is being assigned to `int x`, the value change from `5.0f` to `5` and then gets assigned to `x`.

### Implicit type conversion warnings
- Whenever implicit conversions occur, the compiler will generate some kind of a warning.
- Warnings can be dealt with by either suppressing it, or explicitly converting the values.

### Explicit type conversion - static_cast
- Explicit type conversion is, quite literally, a type conversion that is done explicitly, by using an operator that converts the value.
- There are several different operators for converting a value; the most common one is `static_cast`.
- `static_cast` is a casting operator that is used to perform explicit type conversions at compile time.
	- It is primarily used for safe and well-defined conversions, such as converting between related types, performing implicit conversions explicitly, and calling explicit conversion functions.
- The syntax for `static_cast` looks like this: `static_cast<new_type>(expression)`.
	- `static_cast` takes the value from an expression as input, and returns that value converted into the type specified by `new_type` (e.g. `int`, `bool`, `char`, etc.).
	- Example: `int x = static_cast<int>(5.5);`
- When explicit type conversion is used, the compiler will not generate any warning.

---

In C++, casting is the process of converting a value from one data type to another. There are several types of casts in C++, each serving different purposes and providing varying levels of safety and flexibility. Here are the main types of casts:

1. **C-Style Cast**
    - **Syntax**: `(new_type)expression` or `new_type(expression)`
    - **Usage**: This is the most basic form of casting and can perform any type of cast (static, dynamic, const, or reinterpret). However, it is not recommended because it lacks the safety and clarity of the C++-style casts⁷.

2. **`static_cast`**
    - **Syntax**: `static_cast<new_type>(expression)`
    - **Usage**: Used for compile-time type conversions that are considered safe. It can be used to convert between related types, such as numeric types or pointers within the same inheritance hierarchy¹.
    - **Example**:

```cpp
int num = 10;
double numDouble = static_cast<double>(num); // Converts int to double
```

3. **`dynamic_cast`**
    - **Syntax**: `dynamic_cast<new_type>(expression)`
    - **Usage**: Used for safe downcasting in inheritance hierarchies. It performs a runtime check to ensure the validity of the conversion. If the conversion is not possible, it returns a null pointer (for pointers) or throws a `bad_cast` exception (for references)¹⁴.
    - **Example**:
	
```cpp
Animal* animalPtr = new Dog();
Dog* dogPtr = dynamic_cast<Dog*>(animalPtr); // Downcasting
if (dogPtr) {
    dogPtr->speak();
}
```

4. **`const_cast`**
    - **Syntax**: `const_cast<new_type>(expression)`
    - **Usage**: Used to add or remove the `const` qualifier from a variable. It is primarily used to cast away constness, allowing modification of a variable that was originally declared as `const`⁸.
    - **Example**:
	
```cpp
const int* ptr = &num;
int* modifiablePtr = const_cast<int*>(ptr); // Removes constness
```

5. **`reinterpret_cast`**
    - **Syntax**: `reinterpret_cast<new_type>(expression)`
    - **Usage**: Used for low-level reinterpreting of bit patterns. It can cast any pointer type to any other pointer type, even if the types are unrelated. This cast is the most dangerous and should be used with caution⁸.
    - **Example**:
	
```cpp
int num = 10;
void* ptr = &num;
int* intPtr = reinterpret_cast<int*>(ptr); // Reinterprets void* as int*
```

Summary
- **C-Style Cast**: Basic and flexible, but not recommended due to lack of safety.
- **`static_cast`**: Safe compile-time conversions.
- **`dynamic_cast`**: Safe runtime downcasting.
- **`const_cast`**: Adds or removes `const` qualifier.
- **`reinterpret_cast`**: Low-level bit pattern reinterpreting.

Each cast serves a specific purpose and should be used appropriately to ensure code safety and clarity.

¹: [GeeksforGeeks](1)
⁴: [LearnCpp](4)
⁷: [LearnCpp](7)
⁸: [GeeksforGeeks](8)

Source: Conversation with Copilot, 2024. 8. 4.
(1) 10.6 — Explicit type conversion (casting) and static_cast. https://www.learncpp.com/cpp-tutorial/explicit-type-conversion-casting-and-static-cast/.
(2) Casting Operators in C++     - GeeksforGeeks. https://www.geeksforgeeks.org/casting-operators-in-cpp/.
(3) 25.10 — Dynamic casting – Learn C++     - LearnCpp.com. https://www.learncpp.com/cpp-tutorial/dynamic-casting/.
(4) const_cast in C++ | Type Casting operators     - GeeksforGeeks. https://www.geeksforgeeks.org/const_cast-in-c-type-casting-operators/.
(5) Type conversions     - C++ Users. https://cplusplus.com/doc/tutorial/typecasting/.
(6) C/C++ What does casting do in the low level?     - Stack Overflow. https://stackoverflow.com/questions/64573971/c-c-what-does-casting-do-in-the-low-level.
(7) Dynamic _Cast in C++     - GeeksforGeeks. https://www.geeksforgeeks.org/dynamic-_cast-in-cpp/.
(8) c++     - Regular cast vs. static_cast vs. dynamic_cast     - Stack Overflow. https://stackoverflow.com/questions/28002/regular-cast-vs-static-cast-vs-dynamic-cast.
(9) static_cast in C++     - GeeksforGeeks. https://www.geeksforgeeks.org/static_cast-in-cpp/.

---

### Unsigned to signed number
- `static_cast` can be used to convert an unsigned number to a signed number.
- Example:

```C++
#include <iostream>

int main()
{
    unsigned int u { 5 };
    int s { static_cast<int>(u) }; // return value of variable u as an int

    std::cout << s << '\n';
    return 0;
}
```

>[!warning]
>The `static_cast` does not do any range checking, so if you cast a value to a type whose range doesn't contain that value, undefined behavior will result.

### 8-bit int (char) demonstration
- As previously mentioned before at [[#8-bit fixed-width integers behave like chars]], most compilers treat fixed-width 8-bit integer types such as `std::int8_t` and `std::uint8_t` (and corresponding fast/least types) identically to types `signed char` and `unsigned char`.
- Consider this example:

```C++
#include <cstdint>
#include <iostream>

int main()
{
    std::int8_t myInt{65};      // initialize myInt with value 65
    std::cout << myInt << '\n'; // you're probably expecting this to print 65

    return 0;
}
```

- In the above example, most compilers will print the result as `A` instead of `65`.
- `static_cast` can be used on these 8-bit integers to convert them to `int` type.
- It's best to avoid using 8-bit integers as input for `std::cin` because it may behave like it's getting `char` value from the user.

## Constant variables (named constants)
### Intro to constants
- A **constant** is a value that may not be changed during the program's execution.
- C++ supports two different kinds of constants.
	- **Named constants (symbolic constants)** : constant values that are associated with an identifier.
	- **Literal constants** : constant values that are not associated with an identifier.

### Types of named constants
- There are three ways to define a named constant.
	- Constant variables
	- [[#Object-like macros with substitution text]]
	- Enumerated constants (covered later)

### Constant variables
- A **constant variable** is a variable whose value cannot be changed during the program's execution.
- Constant variables are useful for reflecting things in the real world that does not change; such as the Earth's gravity, PI, speed of light, and etc.
- To declare a constant variable, simply place `const` keyword (called a **const qualifier**) adjacent to the object's type.
	- e.g. `const double gravity = 9.8;`, `float const PI = 3.14f;`
	- It's common to put const qualifier before the type.
- Constant variables must be initialized when it's defined, and then the value cannot be changed via assignment - going against any of these will result in error.
	- e.g. `const double gravity;` will result in error.
	- e.g. `float const PI = 3.14f; PI = 3.141f;` will result in error.
- There are a number of different naming conventions for const variables.
	- All caps with snake_case (e.g. `EARTH_GRAVITY`)
	- `k` prefix camelCase (e.g. `kEarthGravity`)
	- Same as normal variables (e.g. `earthGravity`)

>[!important]
>A **type qualifier** (qualifier for short) is a keyword that is applied to a type that modifies how that type behaves. The `const` used to declare a constant variable is called a const type qualifier (or const qualifier). There is also another qualifier named `volatile`.

### Const function parameters
- Function parameters can be made constants via the `const` keyword. For example:

```C++
#include <iostream>

void printInt(const int x)
{
    std::cout << x << '\n';
}

int main()
{
    printInt(5); // 5 will be used as the initializer for x
    printInt(6); // 6 will be used as the initializer for x

    return 0;
}
```

---

Using `const` function parameters in C++ is necessary and beneficial in several scenarios:

1. **Preventing Modification**
	- **Read-Only Parameters**: When you want to ensure that a parameter passed to a function is not modified within the function, you can declare it as `const`. This helps prevent accidental changes and makes the code safer³.

```cpp
void printValue(const int value) {
	std::cout << value << std::endl;
	// value = 10; // Error: value is read-only
}
```

2. **Self-Documentation**
	- **Code Clarity**: Using `const` makes it clear to anyone reading the code that the parameter is not intended to be modified. This improves code readability and maintainability¹.

```cpp
void displayMessage(const std::string& message) {
	std::cout << message << std::endl;
}
```

3. **Enabling Compiler Optimizations**
	- **Optimization**: The compiler can sometimes optimize code better when it knows that certain variables are `const`. This can lead to more efficient code³.

```cpp
void calculate(const int a, const int b) {
	int result = a + b; // Compiler knows a and b won't change
	std::cout << result << std::endl;
}
```

4. **Passing by Reference**
	- **Const References**: When passing large objects or complex data structures to a function, using `const` references avoids unnecessary copying while ensuring the object is not modified².

```cpp
void processData(const std::vector<int>& data) {
	for (const auto& item : data) {
		std::cout << item << std::endl;
	}
}
```

Summary
Using `const` function parameters is a good practice to ensure safety, clarity, and potential optimizations in your code. It is especially useful when you want to prevent modifications, improve readability, and pass large objects efficiently.

¹: [Stack Overflow](1)
²: [Stack Overflow](2)
³: [EDUCBA](3)

Source: Conversation with Copilot, 2024. 8. 4.
(1) Const Keyword in C++ | Declaring a Variable or Function Parameter - EDUCBA. https://www.educba.com/const-keyword-in-c-plus-plus/.
(2) c++ - Does using const on function parameters have any effect? Why does .... https://stackoverflow.com/questions/117293/does-using-const-on-function-parameters-have-any-effect-why-does-it-not-affect.
(3) When to use const and const reference in function args?. https://stackoverflow.com/questions/3967177/when-to-use-const-and-const-reference-in-function-args.
(4) const (C++) | Microsoft Learn. https://learn.microsoft.com/en-us/cpp/cpp/const-cpp?view=msvc-170.

---

- It's generally best to avoid const function parameter unless it's pass-by-reference, which will be covered later on.

### Const return values
- It's possible to define a function and have its return value be a constant. However, it's no purpose for that and it may even generate a warning. It's best not to do it.

### Constant : object-like macros with substitution text
- In the earlier lesson [[#Object-like macros with substitution text]], we learned about preprocessing and how an identifier defined with `#define` directive can replace the identifier with a substitute text.
- The substitution text is considered a constant value, and so the object-like macros with substitution text is also named constants.
	- The value will be set on compile, and will not change during runtime.

>[!warning]
>It's best to just use constant variables over object-like macros w/ substitution text.

## Literals
- Literals are values that are inserted directly into the code (functions and such).
	- For example, `std::cout << "Hello World!";`
- Literals are sometimes called **literal constants** because their meaning cannot be redefined.
- Just like objects have a type, all literals have a type. The type of a literal is deduced from the literal's value.
	- e.g. `5` is an `int` type.
- More types can be expressed by adding a suffix to the value.
	- `f` suffix is used to indicate a literal of `float` type (e.g. `5.0f`).
	- `u` for `unsigned int`
	- `l` for `long`
	- etc..
- ![[Pasted image 20240805123926.png]]
- Most of the suffixes are not case sensitive, except:
	- `s` and `sv` must be lower case
	- Two consecutive `l` or `L` must have the same casing
- For integral types, it's generally fine to use non-suffixed `int` literals, even when initializing non-`int` types:
	- e.g. `unsigned int x = 6;` is fine, the compiler will convert it without a problem.
- By default, floating point literals have a type of `double`. To make them `float`, the `f` suffix should be used.
	- e.g. `float x = 5.1f;`
- Floating point literals can be expressed with scientific notation by using `e` followed by the power.
	- e.g. `double electronChange = 1.6e-19;` means $1.6 \times 10^{-19}$

>[!important]
>A **string** is a collection of sequential characters used to represent text. **String literals** are placed between double quotes to identify them as string (e.g. `"Hello World!"`).
>
>Because strings are commonly used in programs, most modern programming languages include a fundamental string data type. _For historical reasons, strings are not fundamental type in C++._ Rather, they have a strange, complicated type that is hard to work with (more on this in future lesson). Such strings are often called **C strings (C-Style strings)**, as they are inherited from the C-language.
>
>All C-style string literals have an implicit **null terminator** `\0`, which is used to indicate the end of the string. For example, `"Hello World!"` is actually `"Hello World!\0`". This means that the length of the string literal is longer (by one) than the characters typed (13 instead of 12 in the previous example).
>
>There are other string types such as `std::string`, which will be covered in future lessons.

- A **magic number** is a literal that either has an unclear meaning or may need to be changed later.
	- It's best practice to use variables with assigned values for readability and control. Literals, especially numbers, can seem like they came from out of nowhere, hence the "magic".

## Numeral systems (decimal, binary, hex, octal)
- **Numerical system** is a collection of symbols (e.g. digits) used to represent numbers.
- The ordinary numeral system that we use in everyday life is called **decimal numbers**, where each numerical digit can be `0` through `9`. Because there are 10 possible digits, it is called also called a **base 10**.
	- By default, numbers are assumed to be decimal.
- **Binary numbers** use two possible digits `0` or `1` per numerical digit, which makes it a **base 2**.
	- It is the numerical system that computers use internally.
	- Binary numbers are written like this: `0`, `1`, `10`, `11`, `100`, `101`, and so on.
- **Octal numbers** is **base 8**. Each numerical digit ranges from `0` to `7`
	- To use an octal literal, prefix the literal with a `0`. For example, `int x = 012;`. When this example is printed out, it prints out `10` instead because output is in decimal by default.
- **Hexadecimal** is **base 16**. Each numerical digit ranges from `0` to `F` (0123456789ABCDEF).
	- To use a hex literal, prefix the literal with `0x`. For example, `int x = 0xF;`. When this example is printed out (as decimal), it prints out `15`.

>[!important]
>Two bits are called a **crumb**, four bits are called a **nibble**, and 8 bits are called a **byte**.

### Using hexadecimal to represent binary
- Because there are 16 different values for a hexadecimal digit, we can say that a single hex digit encompasses 4 bits. Consequently, a pair of hex digits can be used to exactly represent a full byte.
	- Hex to 4 bits binary: `0x0` is `0000`, `0xF` is `1111`.
	- Hex to 8 bits binary: `0x00` is `0000 0000`, `0xFF` is `1111 1111`.
- Representing a 32-bit integer with binary numbers is rather lengthy and repetitive. In hex, however, it boils down to 8 numerical digits (which is more concise). For this reason, hex values are often used to represent memory addresses or raw data in memory.

>[!important]
>Base16, Base32, and Base64 are encoding schemes used to represent binary data in a text format. Each has its own characteristics, advantages, and trade-offs:
>
>Base16 (Hexadecimal)
>- **Encoding**: Uses 16 symbols (0-9 and A-F) to represent binary data.
>- **Efficiency**: Each byte of binary data is represented by two hexadecimal characters, resulting in a 100% increase in size.
>- **Advantages**: 
>    - Simple and easy to read.
>    - Commonly used in programming and debugging.
>- **Disadvantages**: 
>    - Less space-efficient compared to Base32 and Base64.
>    - Larger encoded size².
>
>Base32
>- **Encoding**: Uses 32 symbols (A-Z and 2-7) to represent binary data.
>- **Efficiency**: Converts five bytes (40 bits) of binary data into eight ASCII characters, resulting in a 60% increase in size.
>- **Advantages**: 
>    - More space-efficient than Base16.
>    - Case-insensitive and eliminates commonly confused characters.
>- **Disadvantages**: 
>    - Less space-efficient than Base64.
>    - Slightly more complex encoding and decoding process¹³.
>
>Base64
>- **Encoding**: Uses 64 symbols (A-Z, a-z, 0-9, +, /) to represent binary data.
>- **Efficiency**: Converts three bytes (24 bits) of binary data into four ASCII characters, resulting in a 33% increase in size.
>- **Advantages**: 
>    - Most space-efficient among the three.
>    - Widely used in email attachments, URLs, and data storage formats like XML and JSON.
>- **Disadvantages**: 
>    - Case-sensitive and includes characters that may not be URL-safe without encoding.
>    - Slightly more complex encoding and decoding process¹².
>
>Summary
>- **Base16**: Simple and easy to read, but less space-efficient.
>- **Base32**: More space-efficient than Base16, case-insensitive, but less efficient than Base64.
>- **Base64**: Most space-efficient, widely used, but case-sensitive and includes non-URL-safe characters.
>
>Each encoding scheme has its own use cases and trade-offs, so the choice depends on the specific requirements of your application.
>
>If you have any specific scenarios or further questions, feel free to ask!
>
>¹: [Base64 vs. Base32 Comparison](1)
>²: [RFC 4648](2)
>³: [Base 32 and Base 64 Encoding](3)
>
>Source: Conversation with Copilot, 2024. 8. 5.
>(1) RFC 4648: The Base16, Base32, and Base64 Data Encodings. https://www.rfc-editor.org/rfc/rfc4648.
>(2) Base64 vs. Base32 Comparison - B64Encode. https://b64encode.com/blog/base64-vs-base32-comparison/.
>(3) Base 32 and Base 64 Encoding - DZone. https://dzone.com/articles/base-32-and-base-64-encoding.

### Binary literals
- Prior to C++14, there is no support for binary literals. However, hexadecimal literals provide us with a useful workaround:

```C++
#include <iostream>

int main()
{
    int bin{};    // assume 16-bit ints
    bin = 0x0001; // assign binary 0000 0000 0000 0001 to the variable
    bin = 0x0002; // assign binary 0000 0000 0000 0010 to the variable
    bin = 0x0004; // assign binary 0000 0000 0000 0100 to the variable
    bin = 0x0008; // assign binary 0000 0000 0000 1000 to the variable
    bin = 0x0010; // assign binary 0000 0000 0001 0000 to the variable
    bin = 0x0020; // assign binary 0000 0000 0010 0000 to the variable
    bin = 0x0040; // assign binary 0000 0000 0100 0000 to the variable
    bin = 0x0080; // assign binary 0000 0000 1000 0000 to the variable
    bin = 0x00FF; // assign binary 0000 0000 1111 1111 to the variable
    bin = 0x00B3; // assign binary 0000 0000 1011 0011 to the variable
    bin = 0xF770; // assign binary 1111 0111 0111 0000 to the variable

    return 0;
}
```

- In C++14 onward, we can use binary literals by using the `0b` prefix:

```C++
#include <iostream>

int main()
{
    int bin{};        // assume 16-bit ints
    bin = 0b1;        // assign binary 0000 0000 0000 0001 to the variable
    bin = 0b11;       // assign binary 0000 0000 0000 0011 to the variable
    bin = 0b1010;     // assign binary 0000 0000 0000 1010 to the variable
    bin = 0b11110000; // assign binary 0000 0000 1111 0000 to the variable

    return 0;
}
```

### Digit separators
- Because long literals can be hard to read, C++14 adds the ability to use a single quotation mark (apostrophe) `'` as a digit separator.
	- e.g. `1'000'000'000`
- Note that comma `,` is not used as a digit separator. This is due to the fact that it may cause confusion, as Europeans use period `.` to indicate digit separator and comma `,` for decimal point. Basically, it is a localization issue.
- The digit separator is purely visual and do not impact the literal value in any way.
	- Though it can visually represent thousands, it does not necessary change the value to thousands.
- Note that the digit separator can NOT be used before the first digit.

### Outputting values in base-8/16/32
- I/O manipulators such as `std::dec`, `std::oct`, and `std::hex` can be used to output decimal, octal, and hexadecimal values respectively.
- For example,

code
```C++
#include <iostream>

int main()
{
    int x { 12 };
    std::cout << x << '\n'; // decimal (by default)
    std::cout << std::hex << x << '\n'; // hexadecimal
    std::cout << x << '\n'; // now hexadecimal
    std::cout << std::oct << x << '\n'; // octal
    std::cout << std::dec << x << '\n'; // return to decimal
    std::cout << x << '\n'; // decimal

    return 0;
}
```

result
```console
12
c
c
14
12
12
```

- Note that once the I/O manipulator is applied, it remains set for future output until it is changed again.
- Printing binary numbers is a bit more complicated, and so it will be covered later.

## Constant expressions and compile-time optimization

### The as-if rule
- In C++, compilers are given a lot of leeway to optimize programs. The **as-if rule** says that the compiler can modify a program however it likes in order to produce more optimized code, so long as those modifications do not affect a program's observable behavior.
- Exactly how a compiler optimizes a given program is up to the compiler itself. However, there are things we can do to help the compiler optimize better.

### Compile-time evaluation of expressions
- Consider the following program:

```C++
#include <iostream>

int main()
{
	int x { 3 + 4 };
	std::cout << x << '\n';

	return 0;
}
```

- The output is straightforward, as it prints `7` every time the program runs.
- If this program was run without optimization, the compiler would generate an executable that calculates the result of `3 + 4` at runtime. If the program were executed a million times, `3 + 4` calculation would occur a million times - considering that the result of the calculation is `7` and it never changes, it is wasteful to do all that calculation over and over again when the value `7` could just be written in place.
	- A situation such as this is considered an **optimization opportunity**.
- Modern C++ compilers are able to evaluate some expressions at compile-time. When this occurs, the compiler can replace the expression with the result of the expression.
	- A simple arithmetic expression with known values (e.g. `3+4`) can be replaced with its result at compile-time.
	- **Compile-time evaluation of expressions** is considered an optimization.

### Constant expressions
- One kind of expression that can always be evaluated at compile time (and does not change during runtime) is called a **constant expression**.
	- e.g. `5`, `1.2 + 3.4`, `const int x = 5;`, `const int y = x + 3;`
	- Opposite of constant expression is runtime expression.
- A **compile-time constant** is a constant whose value must be known at compile time. This includes:
	- Literals
	- Constexpr variables (more on this later)
	- Const integral variables with a constant expression initializer (e.g. `const int x = 5;`)
	- Non-type template parameters (more on this later)
	- Enumerators (more on this later)
- Const variables that are not compile-time constants are sometimes called **runtime constants**.
	- Runtime constants cannot be used in a constant expression.
	- e.g. `int x = 5;`, `const int y = x;` (`x` is not a constant variable)
- Note that `<<` operator does NOT support compile-time evaluation, because output can't be done at compile-time.

### Usefulness of constant expressions
- Constant expressions are useful for (at least) three reasons:
	- Constant expressions are most likely to be optimized.
	- Both the type and the value is known at compile-time, which means any errors associated with constant expressions can be caught at compile-time. This makes it comparably easier to test and safer than catching errors during runtime.
	- Constant expressions are useful for keeping things memory safe by setting certain values to a fixed amount (that cannot be changed).

### Partial optimization of constant subexpressions
- When a part of a runtime expression consists of a constant subexpression, that constant subexpression can be optimized.
	- e.g. `std::cout << 3 + 4;` is a runtime expression, but `3 + 4` is a constant subexpression. `3 + 4` can be optimized by replacing it with `7`.

### Optimization of non-constant expressions
- Compilers are capable of optimizing non-constant expressions in certain cases.
- When a variable is initialized and its value does not change throughout the whole program, the compiler may choose to replace the variable with its value wherever the variable is called. Furthermore, the variable may be removed (**optimized out/away**).
- For example,

Before optimization
```C++
#include <iostream>

int main()
{
	int x { 7 };
	std::cout << x << '\n';

	return 0;
}
```

After optimization
```C++
#include <iostream>

int main()
{
	std::cout << 7 << '\n';

	return 0;
}
```

- This kind of optimization only happens if the compiler realizes that the value of a variable does not change. Whether the compiler realizes this comes down to how complex the program is, and how sophisticated the compiler's optimization routines are.
- Note that it's worth considering changing the non-constant variable to a constant variable if its value does not change. Then it's guaranteed that the compiler will optimize the code accordingly.

### Optimization can make programs harder to debug
- When the compiler optimizes a program, variables/expressions/statements/function calls may be rearranged/altered/replaced with a value/removed. Such changes can make it hard to debug a program effectively.
- There are times when optimization itself can cause a bug; like when a variable/expression is replaced with a wrong value.
- To help minimize such issues with debugging, debug builds will typically turn down (or off) optimizations, so that the compiled code will closely match the source code.

## Constexpr variables
### Problem with const
- When using `const`, integral variables may end up as either a compile-time const or a runtime const, depending on whether the initializer is a constant expression or not.
	- In some cases, this can make it hard to tell whether the `const` variable is actually a compile-time constant or not.
- The use of `const` to create a compile-time constant variables does not extend to non-integral variables.

### The constexpr keyword
- `constexpr` keyword (shorthand for constant expression) can be used instead of `const` to make sure the variable is declared as a compile-time constant variable; as such, a `constexpr` variable is always a compile-time constant.
	- As a result, a `constexpr` variable must be initialized with a constant expression, otherwise a compilation error will result.
- For example,

```C++
#include <iostream>

int five()
{
    return 5;
}

int main()
{
    constexpr double gravity { 9.8 }; // ok: 9.8 is a constant expression
    constexpr int sum { 4 + 5 };      // ok: 4 + 5 is a constant expression
    constexpr int something { sum };  // ok: sum is a constant expression

    std::cout << "Enter your age: ";
    int age{};
    std::cin >> age;

    constexpr int myAge { age };      // compile error: age is not a constant expression
    constexpr int f { five() };       // compile error: return value of five() is not a constant expression

    return 0;
}
```

- Additionally, `constexpr` works for both integral and non-integral types.

### Const vs. constexpr
- `const` means that the value of an object cannot be changed after initialization. The value of the initializer may be known at compile-time or runtime. The object can be evaluated at runtime.
- `constexpr` means that the object can be used in a constant expression. The value of the initializer must be known at compile-time. The object can be evaluated at runtime or compile-time.
- `constexpr` variables are implicitly `const`. However, it's not true for the other way around.
- Defining a variable as both `constexpr` and `const` is possible but it is redundant in most cases.

### Const and constexpr function parameters
- Normal function calls are evaluated at runtime, with the supplied arguments being used to initialize the function's parameters. Because the initialization of function parameters happens at runtime, this leads to two consequences:
	- `const` function parameters are treated as runtime constants (even when the supplied argument is a compile-time constant).
	- Function parameters cannot be declared as `constexpr`, since their initialization value isn't determined until runtime.
- C++ does support functions that can be evaluated at compile-time. This will be discussed in future lessons.

## The conditional operator
- The **conditional operator** `?:` (aka arithmetic if operator) is a ternary operator (takes 3 operands) that provides a shorthand method for doing a particular type of if-else statement.
- To recap, an if-else statement takes the following form:

```C++
if (condition)
	statement1;
else
	statement2;
```

- The `?:` operator takes the following form:

```C++
condition ? expression1 : expression2;
```

- If `condition` evaluates to `true`, then `expression1` is evaluated, else `epxression2`.
	- The `:` and `expression2` are not optional.
- Consider an if-else statement that looks like this:

```C++
if (x > y)
	greater = x;
else
	greater = y;
```

- Above if-else statement can be rewritten as:

```C++
greater = ((x > y) ? x : y);
```

- Using the conditional operator can help compact code without losing readability.

### The conditional operator as an expression
- The conditional operator and its operands are considered an expression, therefore it can be used in places where an expression is required.
- For example, the conditional operator can be used for initializing a variable:

```C++
#include <iostream>

int main()
{
    constexpr bool inBigClassroom { false };
    constexpr int classSize { inBigClassroom ? 30 : 20 };
    std::cout << "The class size is: " << classSize << '\n';

    return 0;
}
```

- There is no direct if-else replacement for the example above. Consider the following:

```C++
#include <iostream>

int main()
{
    constexpr bool inBigClassroom { false };

    if (inBigClassroom)
        constexpr int classSize { 30 };
    else
        constexpr int classSize { 20 };

    std::cout << "The class size is: " << classSize << '\n';

    return 0;
}
```

- The code above will not compile because `classSize` will only exist within the scope of the conditional statement, meaning that printing its value will result in undefined variable error.
	- Declaring `classSize` outside the if-else block will not work, as its intended purpose is to be a `constexpr` variable, which means it has to be initialized with a value at definition.
- Like the example above, the conditional operator is useful for situations where if-else logic must be contained within the initializer.

>[!important] Parenthesizing the conditional operator
>Because operators have a certain order of priority and most operators are prioritized over the evaluation of the conditional operator, it's recommended to use parenthesis on the conditional operator (either the entire expression or the condition) to make it more readable and clear.
>
>Follow these two rules:
>- Parenthesize the entire conditional operator when used in a compound expression (an expression with other operators).
>- Parenthesize the condition if it contains any operators (other than the function call operator).

>[!warning] Operant types must match (or be convertible)
>When using a conditional operator, the type of the second and third operand must match, otherwise one of the operands will be converted to match the other. Such conversions may yield undefined behaviors.
>
>In general, it's okay to mix operands with fundamental types. But it's best to avoid mixing signed and unsigned values.
>- Mixing `int` and `float` is okay, as `int` operand will be converted to `float`.
>- Consider `(true ? -1 : 2u)`, where `-1` is converted to `unsigned int` to match the type of the other; which causes the overflow wrap-around to occur.
>
> A compile error will result if the types are not convertible. For example, mixing `int` and C-style string (e.g. `"Hello World!"`) will result in compile error.
> 
> If either operand is not a fundamental type, it's generally best to explicitly convert one or both operands to a matching type.

- It's best to avoid using conditional operator in complicated expressions, as they tend to be error prone and hard to read.

## Inline functions and variables
### Function overhead
- Writing functions provides many potential benefits, as code in a function:
	- Easy to read and understand in the context of the overall program.
	- Easy to use, as you can call the function without understanding how it is implemented.
	- Easy to update, as the function can be updated in one place
	- Easy to reuse, as functions are naturally modular
- One downside of using a function is that every time a function is called, there is a certain amount of performance **overhead** (extra work that must happen to facilitate a function) that occurs:
	- When a function is called, the CPU must store the address of the current instruction it is executing, so it knows where to return to later.
	- The function parameters must be instantiated and then initialized.
	- When the function ends, the program has to jump back to the location of the function call, and then the return value ahs to be copied so it can be output.
- For functions that are large and/or perform complex tasks, the overhead of the function call is typically insignificant compared to the amount of time the function takes to run.
	- However, for small functions, the overhead costs can be larger than the time needed to actually execute the function's code. In cases where a small function is called often, using a function can result in a significant performance penalty over writing the same code in-place.

### Inline expansion
- The compiler has a trick that it can use to avoid function overhead; **inline expansion** is a process where a function call is replaced by the code from the called function's definition.
- For example,

Before inline expansion
```C++
#include <iostream>

int min(int x, int y)
{
    return (x < y) ? x : y;
}

int main()
{
    std::cout << min(5, 6) << '\n';
    std::cout << min(3, 2) << '\n';
    return 0;
}
```

After
```C++
#include <iostream>

int main()
{
    std::cout << ((5 < 6) ? 5 : 6) << '\n';
    std::cout << ((3 < 2) ? 3 : 2) << '\n';
    return 0;
}
```

- Beyond removing the cost of function call (overhead), inline expansion can also allow the compiler to optimize the resulting code more efficiently.
	- If a function becomes a constant expression due to inline expansion, the compiler could further optimize the code by optimizing out the constant expression with a value.
- Inline expansion has its own potential cost - if the body of the function being expanded takes more instructions than the function call being replaced, then each inline expansion will cause the executable to grow larger. Larger executables tend to be slower (due to not fitting as well in memory caches).
- The decision about whether a function would benefit from being made inline is not straightforward. Inline expansion is best suited to simple, short functions (no more than a few statements), especially cases where a single function call can be executed more than once (e.g. function calls inside a loop).

### Historical use of inline keyword
- Historically, compilers either didn't have the capability to determine whether inline expansion would be beneficial or were not very good at it. For this reason, C++ provided the keyword `inline`, which was originally intended to be used as a hint to the compiler that a function would (probably) benefit from being expanded inline.
- A function that is declared using the `inline` keyword is called an **inline function**.
- An example of inline function:

```C++
#include <iostream>

inline int min(int x, int y)
{
    return (x < y) ? x : y;
}

int main()
{
    std::cout << min(5, 6) << '\n';
    std::cout << min(3, 2) << '\n';
    return 0;
}
```

>[!warning] The `inline` keyword is no longer used in modern C++ for inline expansion.
>The `inline` keyword is no longer used in modern C++ because of a few reasons:
>- Using `inline` to request inline expansion is a form of premature optimization, and misuse could actually harm performance.
>- The `inline` keyword is just a hint. The compiler is completely free to ignore it.
>- The `inline` keyword is defined at the wrong level of granularity; `inline` keyword is used on a function definition, but inline expansion is actually determined per function call.

### Modern use of inline keyword
- In modern C++, the term `inline` has evolved to mean "multiple definitions are allowed". Thus, an **inline function** is one that is allowed to be defined in multiple translation units (without violating the ODR).
- Inline functions have two primary requirements:
	- The compiler needs to be able to see the *full definition* of an inline function in each translation unit where the function is used (a forward declaration will not suffice on its own). The definition can occur after the point of use if a forward declaration is also provided. Only one such definition can occur per translation unit, otherwise a compilation error will occur.
	- Every definition for an inline function must be *identical*, otherwise undefined behavior will result.
- For example,

main.cpp
```C++
#include <iostream>

double circumference(double radius); // forward declaration

inline double pi() { return 3.14159; }

int main()
{
    std::cout << pi() << '\n';
    std::cout << circumference(2.0) << '\n';

    return 0;
}
```

math.cpp
```C++
inline double pi() { return 3.14159; }

double circumference(double radius)
{
    return 2.0 * pi() * radius;
}
```

- Inline functions are typically defined in header files, where they can be `#included` into the top of any code file that needs to see the full definition of the identifier. This ensures that all inline definitions for an identifier are identical.
- For example,

pi.h
```C++
#ifndef PI_H
#define PI_H

inline double pi() { return 3.14159; }

#endif
```

main.cpp
```C++
#include "pi.h" // will include a copy of pi() here
#include <iostream>

double circumference(double radius); // forward declaration

int main()
{
    std::cout << pi() << '\n';
    std::cout << circumference(2.0) << '\n';

    return 0;
}
```

math.cpp
```C++
#include "pi.h" // will include a copy of pi() here

double circumference(double radius)
{
    return 2.0 * pi() * radius;
}
```

- Inline functions (defined in header files) are particularly useful for header-only libraries, which are one or more header files that implement some capability (no .cpp files are included).
	- Header-only libraries are popular because there are no source files that need to be added to a project to use them (and be linked). You simply `#include` the header-only library and then can use it.

>[!important]
>There are a couple reasons why not all functions are inline and defined in a header file:
>- It can increase the compile time. When a function in a code file changes, only that code file needs to be recompiled. When an inline function in a header file changes, every code file that includes that header (either directly or via another header) needs to be recompiled. On large projects, this can have a drastic impact.
>- It can lead to more naming collisions since you'll end up with more code in a single code file.

### Inline variables (C++17)
- C++17 introduces **inline variables**, which are variables that are allowed to be defined in multiple files.
	- Inline variables work similarly to inline functions, and have the same requirements.
- Common use for inline variables will be covered later as it will relate to the topic of sharing global constants across multiple files.

## Constexpr and consteval functions
- One challenge with constant expressions is that function call to a normal function are not allowed in constant expressions. This means we cannot use such function calls anywhere a constant expression is required.
- For example:

```C++
#include <iostream>

double calcCircumference(double radius)
{
    constexpr double pi { 3.14159265359 };
    return 2.0 * pi * radius;
}

int main()
{
    constexpr double circumference { calcCircumference(3.0) };

    std::cout << "Our circle has circumference " << circumference << "\n";

    return 0;
}
```

- The code above will result in a compile error, because `circumference` requires that its initializer is a constant expression, and the call `calcCircumference()` isn't a constant expression.

### Constexpr functions
- A **constexpr function** is a function that is allowed to be called in a constant expression.
	- To make a function a constexpr function, simply place the `constexpr` keyword in front of the function's return type.
- For example,

```C++
#include <iostream>

constexpr double calcCircumference(double radius)
{
    constexpr double pi { 3.14159265359 };
    return 2.0 * pi * radius;
}

int main()
{
    constexpr double circumference { calcCircumference(3.0) };

    std::cout << "Our circle has circumference " << circumference << "\n";

    return 0;
}
```

- If a required constant expression contains a constexpr function call, that constexpr function call must evaluate at compile-time.
	- In the example above, `calcCircumference()` is evaluated at compile-time; the return value of the function call is calculated at compile-time, and then the function call is replaced with the return value (e.g. `constexpr double circumference { 18.8496 };`)
- To evaluate at compile-time, two other things must also be true:
	- The arguments to the constexpr function call must be known at compile time
	- All statements and expressions within the constexpr function must be evaluatable at compile-time.

>[!important]
>Constexpr functions can also be evaluated at runtime, in which case they will return a non-constexpr result.
>
>One of the cases where a constexpr function is evaluated at runtime is when the arguments to the call are not constant expressions.
>
>Another case is when the constexpr function call is part of a non-required constant expression.

>[!warning]
>The parameters of a constexpr function are not implicitly constexpr, nor may they be declared as `constexpr`.
>
>If a constexpr function is given constexpr arguments, then the function will be evaluated at compile-time. However, if a constexpr function is given arguments that are not constexpr, then the function will be evaluated at runtime.

### Constexpr functions are implicitly inline
- When a constexpr function is evaluated at compile-time, the compiler must be able to see the full definition of the constexpr function prior to such function calls.
	- A forward declaration will not suffice in this case, even if the actual function definition appears later in the same compilation unit.
- A constexpr function called in multiple files needs to have its definition included into each translation unit.
	- This would normally be a violation of the ODR, but constexpr functions are implicitly inline (which makes them exempt).
- Because constexpr functions are implicitly inline, they are often defined in header files, so they can be `#included` into any .cpp file that requires the full definition.

### Consteval (C++20)
- C++20 introduces the keyword `consteval`, which is used to indicate that a function MUST evaluate at compile-time, otherwise a compile error will result.
	- Such functions are called **immediate functions**.
- For example,

```C++
#include <iostream>

consteval int greater(int x, int y) // function is now consteval
{
    return (x > y ? x : y);
}

int main()
{
	// ok: will evaluate at compile-time
    constexpr int g { greater(5, 6) };
    std::cout << g << '\n';

	// ok: will evaluate at compile-time
    std::cout << greater(5, 6) << " is greater!\n";

    int x{ 5 }; // not constexpr
    // error: consteval functions must evaluate at compile-time
    std::cout << greater(x, 6) << " is greater!\n";

    return 0;
}
```

- Note that the parameters of a consteval function are not constexpr.
	- Even though consteval functions can only be evaluated at compile-time (meaning they can only accept constexpr arguments), this decision was made for the sake of consistency.

### Using consteval to make constexpr execute at compile-time (C++20)
- The downside of consteval functions is that such functions can't evaluate at runtime, making them less flexible than constexpr functions (which can do either).
	- The downside of constexpr function is that it does not guarantee evaluation at compile-time.
- One way to get around the issue(s) mentioned above, is to use constexpr function with a consteval function as a helper function.
- For example,

```C++
#include <iostream>

consteval auto compileTimeEval(auto value)
{
    return value;
}

constexpr int greater(int x, int y)
{
    return (x > y ? x : y);
}

int main()
{
	// may or may not execute at compile-time
    std::cout << greater(5, 6) << '\n';
    // will execute at compile-time
    std::cout << compileTimeEval(greater(5, 6)) << '\n';

    int x { 5 };
    // we can still call the constexpr version at runtime if we wish
    std::cout << greater(x, 6) << '\n';

    return 0;
}
```

- This workaround works because consteval functions require constant expressions arguments. Therefore, if the return value of a constexpr function is used as an argument to a consteval function, the constexpr function must be evaluated at compile-time.
- Note that while it may seem like inefficient to set up a consteval function that simply returns a value that it's given, it doesn't matter because the entire call to the consteval function willy simply be replaced with the calculated return value.
- `auto` return type allows a function to work with any type of value. This will be covered more later on.

### Constexpr/consteval functions can use non-const local variables
- Within a constexpr or consteval function, local variables that are non-constexpr can be used.
	- Non-constexpr, meaning that the values of these local variables can be changed.
	- However, initializing the variables with a return value of a non-constexpr function may make the constexpr function to be evaluated at runtime; compile error in consteval function case.
- For example,

```C++
#include <iostream>

consteval int doSomething(int x, int y) // function is consteval
{
    x = x + 2;       // we can modify the value of non-const function parameters

    int z { x + y }; // we can instantiate non-const local variables
    if (x > y)
        z = z - 1;   // and then modify their values

    return z;
}

int main()
{
    constexpr int g { doSomething(5, 6) };
    std::cout << g << '\n';

    return 0;
}
```

### Function parameters and local variables as arguments
- Function parameters and local variables inside a constexpr/consteval function can be used as arguments for another constexpr/consteval function inside that function.
	- Both of these functions will be evaluated at compile-time.
	- Note that a constexpr/consteval function can call another constexpr/consteval function.
- For example,

```C++
#include <iostream>

constexpr int goo(int c)
{
    return c;
}

constexpr int foo(int b)
{
    return goo(b);
}

int main()
{
    std::cout << foo(5);

    return 0;
}
```

### A constexpr function can call a non-constexpr function
- A constexpr function can call a non-constexpr function, but only when the constexpr function is being evaluated in a non-constant context.
- Calling a non-constexpr function is allowed so that a constexpr function can do something like this:

```C++
#include <type_traits> // for std::is_constant_evaluated

constexpr int someFunction()
{
    if (std::is_constant_evaluated()) // if evaluating in constant context
        return someConstexprFcn();
    else
        return someNonConstexprFcn();
}
```

- Though it's allowed, it's best to avoid calling non-constexpr functions from within a constexpr function if possible.
- Like the example above, if a constexpr function requires different behavior for constant and non-constant contexts, conditionalize the behavior with `if (std::is_constant_evaluated())` (in C++20) or `if consteval` (C++23 onward).

>[!warning] Always test your constexpr functions in a constant context.

### Why not constexpr every function?
- There are a few things to consider before making a function `constexpr`:
	- Not all functions can be evaluated as part of a constant expression.
	- `constexpr` function is used in contexts that require constant expressions. Make sure that the constexpr function is absolutely necessary, as removing the `constexpr` later will break the code.
	- `constexpr` function is harder to debug due to optimization & can't be inspected at runtime.

>[!important]
>Though one should be careful not to make every functions unnecessarily `constexpr`, it's still a good idea to make a function `constexpr` if that function can be evaluated as part of a constant expression.

## Intro to string types
- C-style string literals (as covered previously on [[#Literals]]) refers to a text in between double quotation marks with a hidden null terminator.
- While C-style string literals are fine to use, C-style string variables are best avoided in modern C++ because they behave oddly, are hard to work with, and are dangerous.
- C++ has introduced two additional string types into the language that are much easier and safer to work with; `std::string` and `std::string_view` (C++17).
	- These are not fundamental types.

### Intro to std::string
- The easiest way to work with strings and string objects in C++ is via the `std::string` type, which lives in the `<string>` header.
- For example,

```C++
#include <string>

int main()
{
	std::string name = "Alex";
	name = "John";

	return 0;
}
```

- `std::string` objects can be printed to console by using `std::cout`.
	- e.g. `std::cout << name;`
	- Empty strings will print nothing.
- `std::string` uses **dynamic memory allocation**, meaning that it's able to allocate different amount of memory depending on the length of the string being stored.
	- In other words, `std::string` is able to store strings of different lengths.
	- Although dynamic memory allocation makes `std::string` so flexible compared to `char`, it is also comparatively slow.

### String input with std::cin
- One of the things that you need to watch out for when using `std::string` with `std::cin` and `>>` operator, is that `>>` operator only returns characters up to the first whitespace it encounters.
- For example,

```C++
#include <iostream>
#include <string>

int main()
{
    std::cout << "Enter your full name: ";
    std::string name{};
    std::cin >> name;

    std::cout << "Enter your favorite color: ";
    std::string color{};
    std::cin >> color;

    std::cout << "Your name is " << name << " and your favorite color is " << color << '\n';

    return 0;
}
```

- In the example above, if `John Doe` is entered when asked for the full name, `"John"` gets assigned to `name` and `"Doe"` gets left inside the `std::cin` buffer. When asked for the favorite color, `std::cin` will skip waiting for user input and `"Doe"` gets assigned to `color`.
	- In the end, the last sentence that gets printed out is `"Your name is John and your favorite color is Doe"`.

### String input with std::getline()
- To read a full line of input into a string, `std::getline()` is used instead.
- `std::getline()` requires two arguments:
	- Input stream (e.g. `std::cin`)
	- String variable (e.g. `std::string text`)
- An example:

```C++
#include <iostream>
#include <string>

int main()
{
	std::cout << "Enter your full name: ";
	std::string name;
	std::getline(std::cin, name);
	std::cout << "Hello, " << name << "!";

	return 0;
}
```

```console
Enter your full name: John Doe
Hello, John Doe!
```

- It's good practice to use `std::cin >> std::ws` as the first argument to `std::getline()` because the input manipulator `std::ws` makes it so that `std::cin` ignores any leading whitespace before extraction.
	- Usually this won't be a problem if only `std::getline()` is being used, but there's a possibility that a whitespace is sitting in the input buffer if `std::cin >>` was used.
- For example:

```C++
#include <iostream>
#include <string>

int main()
{
    std::cout << "Pick 1 or 2: ";
    int choice{};
    std::cin >> choice;

    std::cout << "Now enter your name: ";
    std::string name{};
    std::getline(std::cin, name); // note: no std::ws here

    std::cout << "Hello, " << name << ", you picked " << choice << '\n';

    return 0;
}
```

```console
Pick 1 or 2: 2
Now enter your name: Hello, , you picked 2
```

- In the example above, `2\n` was entered; `2` was assigned to `choice` and `\n` remained inside `sdt::cin`. When asked for `name`, `std::getline()` skipped waiting for user input as it ended up extracting `\n` and assigning it to `name`.
	- This problem is easily fixed by `std::getline(std::cin >> std::ws, name);`

### The length of a std::string variable
- `std::string` includes a member function `.length()` that returns the object's current length.
	- More about member function later.
	- It's written as `std::string::length()` in documentation.
- For example,

```C++
std::string name = "name";
std::cout << name.length(); // prints 4
```

- Although `std::string` is required to be null-terminated (as of C++11), the returned length of a `std::string` does not include the implicit null-terminator character.
- Note that `std::string::length()` returns an unsigned integral value (most likely of type `size_t`).
	- Use `static_cast<int>(var)` if assigning the value to `int` variable
- (C++20) `std::ssize()` function can also be used to get the length of a `std::string` as a large signed integral type (usually `std::ptrdiff_t`).

### Initializing a std::string is expensive
- Whenever a `std::string` variable is initialized, a copy of the string (used to initialize) is made.
	- Making copies of strings is expensive, so care should be taken to minimize the number of copies made.

>[!warning] Do not pass `std::string` by value, as it makes an expensive copy.

>[!warning] Do not return `std::string` by value, as it makes an expensive copy.

- Passing and returning `std::string` properly will be discussed later on, when discussing `std::string_view` and pass/return-by-reference.

### std::string literals (C++14)
- Double-quoted string literals (e.g. "Hello World!") are C-style strings by default (and thus, have a strange type).
	- Assigning a double-quoted string literal to a `std::string` type variable incurs an implicit conversion.
- String literals with type `std::string` is a double-quote string literal with `s` suffix.
	- For example, `std::string name = "John Doe"s;`
- In order to use the `s` suffix (easy access, so to say), `using namespace std::string_literals;` must be stated.
	- Another way is `using namespace std::literals;` but this also imports all of the standard library literals into the scope (which won't likely be used).
	- `using` directives will be covered later. Just know that it allows for a namespace to be opened to the global scope, allowing its types, functions, and all other stuff to be used easily (without stating the namespace over and over).

>[!important]
>Another way to assign string literals to `std::string` types is using the `std::string` constructor with a `const char*` argument. For example,
>```C++
>std::string name = std::string("John Doe");
>```
>This way avoids implicit conversion, and just as efficient as using the `std::string` literal (the `s` suffix).

- Note that it's not super important to use `std::string` literals to initialize a `std::string` variable, as it is fine to do with C-style string literal.
	- However, there are some advantages that will be discussed later.

### Constexpr strings (Don't)
- If you try to define a `constexpr std::string`, your compiler will probably generate an error.
	- This happens because it isn't supported at all in C++17 or earlier, and only works in very limited cases in C++20/23.

## Intro to std::string_view (C++17)
### What is std::string_view
- Using `std::string` can be expensive because it makes copies of its initializer.
	- For example, in a statement such as `std::string name = "John Doe";`, the C-style string literal `"John Doe"` is copied into memory.
	- Unlike fundamental types, initializing and copying a `std::string` is slow.
- The expensive copy happens again when a `std::string` object is passed to a function as an argument, because the parameter (which is `std::string`) is initialized (which means another copy).
- To address the issue with `std::string` being expensive to initialize/copy, `std::string_view` (which lives in the `<string_view>` header) was introduced.
- `std::string_view` provides read-only access to an existing string (a C-style string, a `std::string`, or another) without making a copy.
	- **Read-only** means that the value can be accessed and viewed but cannot be modified. Another word for it is **immutable**.
- What makes `std::string_view` so much lighter than `std::string` is the fact that it does not own the string data. It merely provides a lightweight view into an existing string, and it does not manage memory (no allocation/deallocation).
- `std::string_view` is flexible in a way that it can be initialized from nearly anything; a C-style string, a `std::string`, or another `std::string_view`.
- For example,

```C++
#include <iostream>
#include <string>
#include <string_view>

int main()
{
    std::string_view s1 { "Hello, world!" }; // initialize with C-style string literal
    std::cout << s1 << '\n';

    std::string s{ "Hello, world!" };
    std::string_view s2 { s };  // initialize with std::string
    std::cout << s2 << '\n';

    std::string_view s3 { s2 }; // initialize with std::string_view
    std::cout << s3 << '\n';

    return 0;
}
```

- `std::string_view` can be initialized from any kind of string because it merely creates a view into the memory occupied by the content.
	- It extends to function parameters.

>[!warning] Problem with non-ownership
>When a `std::string_view` is initialized with a variable, it creates a view into the memory occupied by that variable. If the variable is changed or removed, the `std::string_view` can become invalid or point to unintended data - which is referred to as **dangling view**.
>
>To avoid such issues, ensure that the lifetime of the original variable exceeds the lifetime of the `std::string_view`. Alternatively, just use different string type.

### std::string_view to std::string
- It is possible to use `std::string_view` as an initializer for a `std::string`, but there are some caveats:
	- The compiler won't allow implicit conversion, so explicitly casting it (e.g. `static_cast<std::string>(stringViewVar);`) is necessary.

### std::string_view assignments
- Assigning a new string to a `std::string_view` simply changes the view to the new string.
	- It does not modify the prior string in any way.
- For example,

```C++
std::string str = "Alex";
std::string_view name = str;
std::cout << name << std::endl; // prints Alex

name = "John";
std::cout << name << std::endl; // prints John
std::cout << str << std::endl; // prints Alex
```

- <mark class="hltr-red">Warning</mark> : When `std::string_view` is initialized with a `std::string` variable, the size of the `std::string_view` is fixed to the length of the string. While this is no problem when a new string is assigned to `std::string_view` because it takes the length of the new string, it does become a problem when the value of the initializer changes.
- For example:

```C++
#include <iostream>
#include <string>
#include <string_view>


int main()
{
	std::string str = "John";
	std::string_view sv = str;

	std::cout << sv << std::endl;

	str = "Hello World!";
	std::cout << sv << std::endl;

	sv = "Jane Doe";
	std::cout << sv << std::endl;

    return 0;
}
```

```console
John
Hell
Jane Doe
```

- In the above example, when `sv` was assigned to `str` with `"John"` as its value, the length was set to `4`. So when the value of `str` changed to `"Hello World!"`, the changed length is not reflected on `sv` and so printing `sv` results with `"Hell"`.
	- As shown, re-assigning `sv` with a new value fixes it with a new length.

### Literals for std::string_view
- Similar to how literals for `std::string` work, simply add `sv` suffix to the double-quoted string literals to make `std::string_view` literals.
	- `sv` suffix lives in `std::string_view_literals` namespace.
- For example,

```C++
#include <iostream>
#include <string>      // for std::string
#include <string_view> // for std::string_view

int main()
{
    using namespace std::string_literals;      // access the s suffix
    using namespace std::string_view_literals; // access the sv suffix

    std::cout << "foo\n";   // no suffix is a C-style string literal
    std::cout << "goo\n"s;  // s suffix is a std::string literal
    std::cout << "moo\n"sv; // sv suffix is a std::string_view literal

    return 0;
}
```

- It's totally fine to initialize `std::string_view` with any other string types though.

### constexpr std::string_view
- Unlike `std::string`, `std::string_view` has full support for `constexpr`:

```C++
#include <iostream>
#include <string_view>

int main()
{
    constexpr std::string_view s{ "Hello, world!" };
    std::cout << s << '\n';

    return 0;
}
```

- Note that `s` will be replaced with `"Hello, world!"` at compile-time.
- In the case when a variable only needs to be printed out once, it's best to use something that is immutable (cannot be changed later), read-only, and null-terminated - which is to say, a **string symbolic constant**.
	- `constexpr std::string_view` makes for the preferred choice when string symbolic constants are needed.

### Improper use of std::string_view
- There are a few cases where using `std::string_view` improperly leads to unintended/undefined behaviors.

#### Case 1: initializer in nested block
- Consider the code below:

```C++
#include <iostream>
#include <string>
#include <string_view>

int main()
{
    std::string_view sv{};

    {
        std::string s{ "Hello, world!" };
        sv = s;
    }

    std::cout << sv << '\n';

    return 0;
}
```

- The code above results in an undefined behavior because the `std::string_view` is initialized with a variable `s` that gets destroyed outside the nested block. The `std::string_view` has become a dangling view.

#### Case 2: return value as initializer
- Consider the code below:

```C++
#include <iostream>
#include <string>
#include <string_view>

std::string getName()
{
    std::string s { "Alex" };
    return s;
}

int main()
{
  std::string_view name { getName() };
  std::cout << name << '\n';

  return 0;
}
```

- The code above results in an undefined behavior because the `std::string_view` is initialized with a return value of a function, which gets destroyed at the end of the function call.

#### Case 3: std::string literal as initializer
- Consider the code below:

```C++
#include <iostream>
#include <string>
#include <string_view>

int main()
{
    using namespace std::string_literals;
    std::string_view name { "Alex"s };
    std::cout << name << '\n';

    return 0;
}
```

- The code above results in an undefined behavior because the `std::string_view` is initialized with a `std::string` literal, which is a temporary object.
	- This is actually similar to Case 2, when you consider that the `std::string` literal is the same as using `std::string("C-style string")`. In the end, a temporary object is created inside a function, which is then returned - only to be destroyed after the function call.

#### Case 4: initializer is modified
- Consider the code below:

```C++
#include <iostream>
#include <string>
#include <string_view>

int main()
{
    std::string s { "Hello, world!" };
    std::string_view sv { s };

    s = "Hello, universe!";
    std::cout << sv << '\n';

    return 0;
}
```

- The code above results in an undefined behavior because the value that the `std::string_view` was viewing has been modified.
	- A `std::string_view` that is viewing a value that is modified is said to be **invalidated**.
	- Reminder that the length of the `std::string_view` is fixed at the point of initialization.

>[!important]
>It's possible to revalidate an invalid `std::string_view` by re-assigning it with a valid string.


#### Best Practices
- Do not initialize a `std::string_view` with a `std::string` literal.
	- It's okay to use a C-style string literal or a `std::string_view` literal.
- Make sure that the initializer outlives the `std::string_view` object.
	- Do not use temporary object as an initializer.
- Make sure that the initializer does not become modified.

### View modifications
- `std::string_view` provides member functions that can modify the view.
- `.remove_prefix()` removes characters from the left side of the view.
- `.remove_suffix()` removes characters from the right side of the view.
- For example,

```C++
#include <iostream>
#include <string_view>

int main()
{
	std::string_view str{ "Peach" };
	std::cout << str << '\n';

	// Remove 1 character from the left side of the view
	str.remove_prefix(1);
	std::cout << str << '\n';

	// Remove 2 characters from the right side of the view
	str.remove_suffix(2);
	std::cout << str << '\n';

	str = "Peach"; // reset the view
	std::cout << str << '\n';

	return 0;
}
```

```console
Peach
each
ea
Peach
```

- When the view is modified and only a part of the string is shown, that part of the string is called the **substring**.
	- A substring is a contiguous sequence of characters within an existing string.

### std::string_view may not be null-terminated
- If a `std::string_view` is viewing a whole string (which includes a null-termination), then it is viewing a null-terminated string (and treated as such). But if it is viewing a substring that does not include a null-termination, then it is not null-terminated.
- In most cases, using a `std::string_view` that is not null-terminated is fine. However, it's best not to write any code that assumes a `std::string_view` is null-terminated.

## Operator precedence and associativity
### Evaluation of compound expressions
- In order to evaluate an expression, the compiler must do two things:
	- At compile time, the compiler must parse the expression and determine how operands are grouped with operators. This is done via the precedence and associativity rules (discussed soon).
	- At compile time or runtime, the operands are evaluated and operations executed to produce a result.

### Operator precedence
- To assist with parsing a compound expression, all operators are assigned a level of **precedence**. Operators with a higher precedence level are grouped with operands first.
- Operator precedence mostly follows the arithmetic precedence. As such, multiplication/division has a higher precedence level than addition/subtraction.
- Detailed list of operators and their precedence levels soon to follow in a table.

### Operator associativity
- If two operators with the same precedence level are adjacent to each other in an expression, the operator's **associativity** tells the compiler whether to evaluate the operators from left to right or from right to left.
	- Subtraction has precedence level 6, and the operators in precedence level 6 have an associativity of left-to-right.
- Take `7 - 4 - 1` for example. If this is evaluated as `(7 - 4) - 1`, then this evaluates to `2`. If this is evaluated as `7 - (4 - 1)`, then this evaluates to `4`. Because we are dealing with subtractions, the order is left-to-right, so the compound expression is evaluated as `(7 - 4) - 1`, which results to `2`.
- Detailed list of operators and their associativity soon to follow in a table.

### Table of operator precedence and associativity
![[cpp_Table_of_Precedence_and_Associativity]]

>[!important] Use parentheses whenever possible.
>Use parentheses to make it clear how a non-trivial compound expression should evaluate, even if they are technically unnecessary. There are so many operators and precedence levels that it's hard to remember them all, and it's a hassle to look through the table every time. Using parentheses makes it clear and avoids the hassle.

### Order of Evaluation
(note) the explanation for "evaluation" seems a little weird on the website. The contents of this specific section takes information from other sources, such as *cppreference.com* (and Copilot).

- In the context of the C++ standard, **evaluation** refers to the process of computing the value of an expression and any associated side effects. There are two main aspects of evaluation:
	- **Value Computation** : this involves calculating the value that an expression returns. For example, in the expression `a + b`, the value computation would involve adding the values of `a` and `b`.
	- **Side Effects** : these are additional actions that occur during the evaluation of an expression, such as modifying a variable, writing to a file, or calling a function. For example, in the expression `a = b + c`, the side effect is the assignment of the result of `b + c` to `a`.
- The order of evaluation is unspecified, meaning the compiler has the freedom to evaluate parts of an expression in any order, unless explicitly defined by the standard.
	- The precedence and association rules to determine the order in which value computations occur, but it does not determine the order in which the operands or subexpressions are evaluated.
- Consider the following expression : `a * b + c * d`
	- By following the precedence and associativity rules, the expression is grouped as `(a * b) + (c * d)`. This expression will always compute the value `14`.
	- The compiler is free to evaluate operands `a`, `b`, `c`, or `d` in any order.
	- The compiler is free to evaluate subexpressions `a * b` or `c * d` in any order.
- For most expressions, the order of evaluation does not matter. However, there are some rare cases when it does. For example,

```C++
#include <iostream>

int getValue()
{
    std::cout << "Enter an integer: ";

    int x{};
    std::cin >> x;
    return x;
}

void printCalculation(int x, int y, int z)
{
    std::cout << x + (y * z);
}

int main()
{
    printCalculation(getValue(), getValue(), getValue());

    return 0;
}
```

- When the code above is executed, the program will ask for user input 3 times. The order of the input may not correspond to left-to-right order of the arguments (x, y, z). In fact, the order in which the arguments are handled is up to the compiler.
	- The Clang compiler evaluates arguments in left-to-right order.
	- The GCC compiler evaluates arguments in right-to-left order.

## Arithmetic operators
### Unary arithmetic operators
- Unary operator means that the operator takes one operand (on the right).
- There are two unary arithmetic operators, plus `+` and minus `-`.
- The unary minus operator returns the negation of the operand.
	- Basically, it multiplies the operand by `-1`.
- The unary plus operator just returns the value of the operand. It's just there for symmetry, and so it's useless.

>[!warning]
>Do not confuse the unary minus operator with the binary subtraction operator, which uses the same symbol. Operators in `-5` and `2 - 5` are totally different.

### Binary arithmetic operators
- Binary operators are operators that takes two operands (left and right).
- There are 5 binary arithmetic operators:
	- Addition `+`
	- Subtraction `-`
	- Multiplication `*`
	- Division `/`
	- Remainder `%`

### Divisions : integer and floating point
- The division operator behaves in two different ways depending on the types of the operands.
- Floating point division occurs when if either (or both) of the operands are floating point values.
	- The division returns a floating point value, and the fraction is kept.
- Integer division occurs when both of the operands are integers.
	- The division drops any fractions and returns an integer value.
- In case there are two integers and floating point division is required, the simplest way to solve this problem is to convert one of the operands to a floating point number by using `static_cast<type>(var)`.

### Zero division
- Division by `0` results in undefined behavior. It can crash the program. On some architectures, it may produce `NaN` or `Inf`.
- Best thing to do, is not to do it. Prevent the user from doing it.

### Arithmetic assignment operators
- Arithmetic assignment operators are assignment operators that are mixed with a binary arithmetic operator. There are 6 to account for:
	- Assignment `=` : assigns the right operand to the left operand
	- Addition assignment `+=` : adds the right operand to the left operand, and then assigns the result to the left operand.
	- Subtraction assignment `-=`
	- Multiplication assignment `*=`
	- Division assignment `/=`
	- Remainder assignment `%=`

## Remainder and exponentiation
### Modulo
- The concept of modulo is used both in mathematics and programming, but there are some differences in how it is applied and interpreted.
- Modulo in mathematics
	- Definition: the modulo operation finds the remainder when one integer is divided by another. It is often denoted as $a \mod n$, where $a$ is the dividend and $n$ is the divisor.
	- Positive Remainder: the result is typically the smallest non-negative integer that represents the remainder.
	- Examples: $5 \mod 3 = 2$, $-5 \mod 3 = 1$, $-7 \mod 5 = 3$, $7 \mod -5 = -3$
- Modulo in C/C++
	- Definition: the modulo operation is a binary arithmetic operation which is represented by the `%` operator, where the left operand is the dividend and the right operand is the divisor.
	- Implementation: the remainder always has the same sign as the dividend.
	- Examples: `5 % 3 == 2`, `-5 % 3 == -2`, `-7 % 5 = -2`, `7 % -5 = 2`
- (Note) mathematics modulo is defined in such a way that $a = bq + r$ where $a$ is the dividend, $b$ is the divisor, $q$ the quotient, and $r$ the remainder.
	- The quotient (the result of the regular division) seems to use floor function, where the number is rounded to the nearest integer in the negative direction.
	- For example, in $7 \mod -5$, the quotient is $-1.4$ which is then rounded to $-2$; therefore the equation becomes $7 = 10 + r$, and $r = -3$.
- (Note) C/C++ modulo feels more intuitive, where $|bq| \leq |a|$ is always true. The focus seems to be on the remainder, which is why the learncpp website emphasizes that the `%` operator be referred to as the remainder operator.

### The remainder operator
- The remainder operator (aka modulo/modulus operator) `%` is an operator that returns the remainder after doing an integer division.
	- For example, the remainder for integer division `7 / 4` is `3`. Therefore, `7 % 4 = 3`.
- The remainder operator is most useful for testing whether a number is evenly divisible by another number (meaning that after division, there is no remainder).
	- For example, `x % 2` helps check whether an integer `x` is an even or an odd number.

>[!important]
>Prefer to compare the result of the remainder operator against `0` if possible.
>
>Think of a function `bool isOdd(int x)` where its purpose is to return `true` if the `x` is an odd number. The conditional logic could be that "if x % 2 equals 1, then return true". However, this will fail when the `x` value is a negative integer (e.g. `-5`) because the remainder will be `-1` and it does not equal to `1`. In this case, it's better to check if the remainder does not equal to `0`.

### Exponent operator
- In mathematics, the exponent is commonly denoted as `^`. However, in C++, that symbol is used as Bitwise XOR operator (which will be covered later). In fact, C++ does not have an exponent operator.
- To do exponents in C++, use the `std::pow()` function from the `<cmath>` header.
	- e.g. 3 to the 4th power = `double x = std::pow(3.0, 4.0);`
- Note that the return type of `std::pow()` is double; due to the rounding errors in floating point numbers, the result may not be precise.
- Note that the standard library does not include an exponent function for integral type. It may be due to possible overflow.

## Increment/decrement operators, and side effects
### Incrementing/decrementing variables
- Incrementing means adding `1` to the current value. Conversely, decrementing means subtracting the value by `1`. In code, incrementing is equivalent to `x = x + 1;`, and decrementing is `x = x - 1;`.
- Incrementing/decrementing is a common operation, so C++ provides operators `++` and `--` for increment and decrement, respectively.
- The operators `++`/`--` behaves differently depending on the placement next to the variable; if it is used as prefix (as in it comes before), the operation happens first and then the variable is returned. If it is used as postfix (as in it comes after), the variable is returned first and then the operation happens.
	- `++x` is pre-increment, where `x` is increased by `1` and then returned.
	- `--x` is pre-decrement
	- `x++` is post-increment, where `x` is returned first, and then `x` is increased by `1`.
	- `x--` is post-decrement
- Consider the following example:

```C++
#include <iostream>

int main()
{
    int x { 5 };
    int y { ++x }; // x is incremented to 6, x is evaluated to the value 6, and 6 is assigned to y

    std::cout << x << ' ' << y << '\n';
    return 0;
}
```

```console
6 6
```

- In the above example, pre-increment operation took place; `x` was increased by `1`, and the new value was returned then assigned to `y`.
- Consider the following example:

```C++
#include <iostream>

int main()
{
    int x { 5 };
    int y { x++ }; // x is incremented to 6, copy of original x is evaluated to the value 5, and 5 is assigned to y

    std::cout << x << ' ' << y << '\n';
    return 0;
}
```

```console
6 5
```

- In the above example, post-increment operation took place; the value of `x` was first assigned to `y` and then `x` was increased by `1`.

### Side effects
- A function or expression is said to have a **side effect** if it has some observable effect beyond producing a return value.
- As previously mentioned before, evaluation consists of value computation and side effects.
- Side effects include range of things, such as changing the value of objects, doing input/output, updating a GUI, and etc.
- For example:

```C++
x = 5; // the assignment operator has side effect of changing value of x
++x; // operator++ has side effect of incrementing x
std::cout << x; // operator<< has side effect of modifying the state of the console
```

>[!warning]
>The [[#Order of Evaluation]] is up to the compiler to decide; a lot of times it is ambiguous, and it's best to be careful not to make any assumption about the order of evaluation (or code based on that assumption).
>
>For example, `add(x, ++x)` causes an undefined behavior because it's questionable whether the intention of the function call was to `x + (x+1)` or `(x+1) + (x+1)` - it all depends on the order the compiler evaluates in.
>
>Similarly, `x + ++x` causes an undefined behavior for the same reason.

>[!important]
>The C++ standard intentionally does not define the order of evaluation so that compilers can do whatever is most natural (and thus most performant) for a given architecture.

>[!important]
>The best way to avoid nearly all order of evaluation issues is by ensuring that any variable that has a side-effect applied is NOT used more than once in a given statement.
>
>For example, if `x++` is in a statement, it's probably best not to use `x` again within that statement.
>
>One exception is for simple assignment expressions, such as `x = x + y` (which is essentially `x += y`).

## The comma operator
- The comma operator `,` allows you to evaluate multiple expressions wherever a single expression is allowed.
	- The comma operator evaluates the left operand, then the right operand, and then returns the result of the right operand.
	- For example, `(++x, ++y)` evaluates `++x` first, then `++y`, and lastly returns `y`.
- The comma operator has the lowest precedence of all the operators, even lower than assignment.
	- Careful not to mistake `x = (a, b);` and `x = a, b` as the same thing.
- The comma operator is commonly used in *for loops*, which will be discussed later.

>[!warning] Avoid using the comma operator, except within *for loops*.

## Comma as a separator
- In C++, the comma symbol is often used as a separator - which does NOT invoke the comma operator.
- Separator comma is used to separate parameters in function definition.
	- e.g. `foo(int x, int y)`
- Separator comma is used to separate arguments in function call.
	- e.g. `foo(x, y)`
- Separator comma is used to separate multiple variables being declared/defined on the same line.
	- e.g. `int x, y, z;`

>[!warning] Avoid using separator commas for declaring multiple variables in one line.

## Relational operators and floating point comparisons
### Relational operators
- Relational operators are binary arithmetic operators that compares left and right operands. There are 6 relational operators:
	- Greater than `>`
	- Less than `<`
	- Greater than or equal to `>=`
	- Less than or equal to `<=`
	- Equality `==`
	- Inequality `!=`

### Floating point comparisons
- Due to the rounding errors, comparing floating point values is best to be avoided or be used with care.
- An example of comparing floating point values gone wrong:

```C++
#include <iostream>

int main()
{
    constexpr double d1{ 100.0 - 99.99 }; // should equal 0.01 mathematically
    constexpr double d2{ 10.0 - 9.99 }; // should equal 0.01 mathematically

    if (d1 == d2)
        std::cout << "d1 == d2" << '\n';
    else if (d1 > d2)
        std::cout << "d1 > d2" << '\n';
    else if (d1 < d2)
        std::cout << "d1 < d2" << '\n';

    return 0;
}
```

```console
d1 > d2
```

- In the example above, the debugger may show that the value of `d1` is `0.010000000000005116` and `d2` is `0.0099999999999997868`. They both are close to `0.01` but off by a little bit.
- Comparing the floating point values on whether they are equal `==` or unequal `!=` is DEFINITELY not reliable. However, greater than `>` or less than `<` (and its equal to variations) are somewhat reliable.
	- These operators are especially reliable when the operands are more likely to be different than identical, or when the small amount of error is permissible.

>[!important]
>It is safe to compare a floating point literal with a variable of the same type that has been initialized with a literal of the same type, so long as the number of significant digits in each literal does not exceed the minimum precision for that type.
>
>For example, `double gravity = 9.8; if (gravity == 9.8) //..` is perfectly fine to do.

>[!warning]
>It is generally not safe to compare floating point literals of different types. For example, `9.8f == 9.8` will return `false`.

### Close enough floating point values
- Although not perfect, there is some way to get around the rounding point error issue with comparing equality of two floating point values - that is, by using a margin of error.
- As long as two floating point values are close enough by an acceptable margin of error (which is called **epsilon**), these two values can be considered equal.
- There are two ways to implement epsilon: absolute epsilon and relative epsilon.
- Absolute epsilon is the easiest to implement in the sense that the function (e.g. `equalTo()`) takes the absolute value of the difference of the two given floating point values (e.g. `std::abs(a - b)`), and then checks whether the value is smaller than the given absolute epsilon (e.g. `absDiff <= absEpsilon`). An example code:

```C++
#include <cmath> // for std::abs()

bool equalTo(double a, double b, double absEpsilon)
{
    return std::abs(a - b) <= absEpsilon;
}
```

- While using absolute epsilon can work, it's not great. While an epsilon of `0.00001` is good for inputs around `1.0`, it is too big for inputs around `0.00000000001`, and too small for inputs like `10,000`.
	- Choosing an appropriate epsilon can be a headache because you should always be aware just how big the input values usually are.
- Relative epsilon is a method where it determines that the two floating point values are equal (close enough) if the distance of the two values are less than or equal to a small percentage of the higher value.
	- This method was suggested by Donald Knuth (a famous computer scientist) in his book "The Art of Computer Programming, Volume II".
- The implementation of the relative epsilon method looks like this:

```C++
#include <algorithm> // for std::max
#include <cmath>     // for std::abs

bool approximatelyEqualRel(double a, double b, double relEpsilon)
{
	return (std::abs(a - b) <= (std::max(std::abs(a), std::abs(b)) * relEpsilon));
}
```

- In the code above, if `relEpsilon` is set to `0.01`, it means that the function determines that the two values are equal if the distance between them are within 1% of the higher value.
- While Donald's method works great in most cases, it is not perfect - especially so as the numbers approach zero.
	- Donald's method can be improved by implementing absolute epsilon method when the numbers are very small; the absolute epsilon should be set to something very small (e.g. `1e-12`).
- Implementation of absolute epsilon & relative epsilon:

```C++
bool approximatelyEqualAbsRel(double a, double b, double absEpsilon, double relEpsilon)
{
    if (std::abs(a - b) <= absEpsilon)
        return true;

    return approximatelyEqualRel(a, b, relEpsilon);
}
```

## Logical operators
- While relational operators can be used to test whether a particular condition is true or false, they can only test one condition at a time.
- Logical operators provides the capability to test multiple conditions.
- C+ has 3 logical operators:
	- Logical NOT `!`
	- Logical AND `&&`
	- Logical OR `||`
- `!` operator is useful for negating `bool` values. If `x` is `true`, then `!x` is `false`.
- `&&` operator returns `true` only if both operands are `true`.
- `||` operator returns `true` if one or both of the operands are `true`.
- Both `&&` operator and `||` operator can be chained together with many of its kind.
	- e.g. `x && y && z`, `x || y || z`

>[!important] Alternative operator representations
>Logical AND operator can be represented with `and`.
>Logical OR operator can be represented with `or`.
>Logical NOT operator can be represented with `not`.
>Putting all together, `!a && (b || c)`

### Related mathematics field
- [Propositional Calculus](https://en.wikipedia.org/wiki/Propositional_calculus)
- [Boolean Algebra](https://en.wikipedia.org/wiki/Boolean_algebra)

### Short circuit evaluation
- Short circuit evaluation refers to when logical operators immediately returns a result by evaluating just one operand instead of evaluating the whole expression.
- `&&` operator short circuits and returns `false` when the left operand is `false`.
- `||` operator short circuits and returns `true` when the left operand is `true`.
- Note that when the short circuit happens, the right operand does not get evaluated.
	- For example, if `x && ++y` and `x == false`, then `++y` never executes.

>[!important]
>The `&&` operator and `||` operator are an exception to the rule that the operands may evaluate in any order, as the standard explicitly states that the left operand must evaluate first.

>[!important]
>When mixing `&&` operator and `||` operator in a single expression, explicitly parenthesize each operation to ensure they evaluate in the order that is intended.

### De Morgan's laws
- [De Morgan's laws](https://en.wikipedia.org/wiki/De_Morgan%27s_laws) are a pair of rules that describe how negation is distributed:
	- `!(x && y)` is equivalent to `!x || !y`
	- `!(x || y)` is equivalent to `!x && !y`
- These laws are better understood with Venn diagrams:
	- ![[Demorganlaws.svg|300]]
	- Note that the the resultant set is the set of all points in any shade of blue.

### Logical XOR
- Logical Exclusive OR (XOR in short) is a logical operator which returns true if and only if the inputs differ (one of them is true while the other is false).
- C++ does not provide logical XOR operator.
	- In mathematics, it's possible to implement (find equivalence) logical XOR by combining logical AND, logical OR, and logical NOT. However, it's not possible in C++ because of short-circuit.
- `!=` operator produces the same result as a logical XOR when given `bool` operands.
	- For example, `a != b` returns `true` only if the two values differ.

## Bitwise operations
Skipping this whole [optional chapter on bitwise operations](https://www.learncpp.com/cpp-tutorial/bit-flags-and-bit-manipulation-via-stdbitset/).

## Compound statements (blocks)
- A compound statement (aka block) is a group of zero or more statements that is treated by the compiler as if it were a single statement.
- Blocks begin and end with curly brackets, `{` and `}`. In between the curly brackets, statements to be executed are placed. Semicolon is not needed.
- Common usages of the block includes:
	- the function body (e.g. `int add(int x, int y) { return x + y; }`).
	- conditional statements (e.g. `if (condition) { execute }`)
	- 
- Initialization is NOT a block (e.g. `int x{};`).
- Blocks can be nested, as in blocks inside other blocks:

```C++
int add(int x, int y)
{ // block
    return x + y;
} // end block

int main()
{ // outer block

    // multiple statements
    int value {};

    { // inner/nested block
        add(3, 4);
    } // end inner/nested block

    return 0;

} // end outer blocks
```

- When blocks are nested, the enclosing block is typically called the **outer block**, and the enclosed block is called the **inner block** or **nested block**.
	- C++ standard says that C++ compilers should support 256 levels of nesting. However, not all do (nor should you).

### User-defined namespaces and the scope resolution operator
- The concept of namespace and scope was introduced in [[#Naming collisions and an introduction to namespaces]].
	- As a reminder, a naming collision occurs when two identical identifiers are introduced into the same scope (and the compiler can't disambiguate which one to use).
- C++ allows us to define our own namespaces via the `namespace` keyword. Namespaces that you create in your own programs are casually called **user-defined namespaces**.
- The syntax for a namespace is as follows:

```C++
namespace NamespaceIdentifier
{
	// content of namespace here
}
```

- Historically, namespace names have not bee capitalized, and many style guides still recommend this convention. However, there are some reasons to prefer namespace names with a capital letter:
	- The C++20 standards document uses this style.
	- The C++ Core guidelines document uses this style.

### Scope resolution operator
- The best way to tell the compiler to look in a particular namespace for an identifier is to use the **scope resolution operator** `::`. The scope resolution operator tells the compiler that the identifier specified by the right-hand operand should be looked for in the scope of the left-hand operand.
- For example,

```C++
#include <iostream>

namespace Foo
{
    int doSomething(int x, int y)
    {
        return x + y;
    }
}

namespace Goo
{
    int doSomething(int x, int y)
    {
        return x - y;
    }
}

int main()
{
    std::cout << Foo::doSomething(4, 3) << '\n';
    std::cout << Goo::doSomething(7, 4) << '\n';

    return 0;
}
```

```console
7
3
```

- If `::` operator is used without a left operand, then the right operand (the identifier) is looked for in the global namespace.
- If scope resolution operand is not provided, then the identifier is assumed to be in the most immediate namespace. For example,

```C++
#include <iostream>

void print() // this print() lives in the global namespace
{
	std::cout << " there\n";
}

namespace Foo
{
	void print() // this print() lives in the Foo namespace
	{
		std::cout << "Hello";
	}

	void printHelloThere()
	{
		print();   // calls print() in Foo namespace
		::print(); // calls print() in global namespace
	}
}

int main()
{
	Foo::printHelloThere();

	return 0;
}
```

```console
Hello there
```

### Forward declaration inside namespaces
- As mentioned before, it's recommended to propagate forward declarations by using [[#Header files]]. For identifiers inside a namespace, those forward declarations also need to be inside the same namespace. For example:

add.h
```C++
#ifndef ADD_H
#define ADD_H

namespace BasicMath
{
    // function add() is part of namespace BasicMath
    int add(int x, int y);
}

#endif
```

add.cpp
```C++
#include "add.h"

namespace BasicMath
{
    // define the function add() inside namespace BasicMath
    int add(int x, int y)
    {
        return x + y;
    }
}
```

main.cpp
```C++
#include "add.h" // for BasicMath::add()

#include <iostream>

int main()
{
    std::cout << BasicMath::add(4, 3) << '\n';

    return 0;
}
```

>[!important]
>It's legal to declare namespace blocks in multiple locations (either across multiple files, or multiple places within the same file). All declarations within the namespace are considered part of the namespace.

>[!warning] Do not add custom functionality to the `std` namespace

### Nested namespaces
- Namespaces can be nested inside other namespaces. For example:

```C++
#include <iostream>

namespace Foo
{
    namespace Goo // Goo is a namespace inside the Foo namespace
    {
        int add(int x, int y)
        {
            return x + y;
        }
    }
}

int main()
{
    std::cout << Foo::Goo::add(1, 2) << '\n';
    return 0;
}
```

- Note that because namespace `Goo` is inside of namespace `Foo`, we access `add` as `Foo::Goo::add()`.
- Since C++17, nested namespaces can also be declared like `namespace Foo::Goo {}`.
- Whether you keep the separate `Foo::Goo` definition or nest `Goo` inside `Foo` is a stylistic choice.

### Namespace aliases
- Namespace aliases allows us to temporarily shorten a long sequence of namespaces, like so:
	- `namespace Active = Foo::Goo;`
- Not only is this convenient because the namespace is shortened, it's also useful to move the functionality from a namespace to another (and just update the alias to reflect the new destination).

### How to use namespaces
- It's worth noting that namespaces were NOT originally designed as a way to implement an information hierarchy. Rather, they were designed primarily as a mechanism for preventing naming collisions.
	- As evidence of this, note that the entirety of the standard library lives under the single top-level namespace `std`.
- Namespaces now serve multiple purposes:
	- Prevent naming collisions for larger projects that include multiple third party libraries.
	- Prevent naming collisions when distributing codes, and provide support for auto-complete and suggestion feature.
	- Prevent naming collisions between projects/libraries, teams, and companies (e.g. `Company::Team::Project).
- All in all, namespaces help make code reusable.

>[!important] In general, avoid nested namespaces that are more than 3 levels.

## Local variables
Skipped. Refer to https://www.learncpp.com/cpp-tutorial/local-variables/

## Intro to global variables
- Variables declared in the global namespace outside any function are called **global variables**.
- By convention, global variables are declared at the top of a file, below the includes, in the global namespace.
- Identifiers declared in the global namespace have **global namespace scope** (aka file scope), which means they are visible from the point of declaration until the end of the file in which they are declared.
- By extension, variables declared inside a namespace that is defined in a global scope are global variables.
	- e.g. `Foo::x` is a global variable if namespace `Foo` was defined in the global scope.
	- Basically, any variable that can be accessed anywhere (as long as namespace is stated) is a global variable.

>[!important]
>Best practice is to define global variables inside a namespace rather than in the global namespace.

- Global variables are created when the program starts (before `main()` begins execution) and destroyed when it ends - the duration in between is called **static duration**.
	- Variables with static duration are sometimes called **static variables**.
- By convention, `g` or `g_` prefix is used for global variable identifiers.
	- This prefix is omitted for global variables defined inside a user-defined namespace.

>[!note] Hungarian notation
>Hungarian notation refers to use of prefix in identifiers to indicate type. For example, `nAge` would indicate `int` type.
>
>Hungarian notation has largely fallen out of favor in modern C++ programming because it is redundant; C++ is strongly-typed language, and the type information is provided by the compiler. There's really no confusion as to what type is being used.
>
>The C++ Core Guidelines strongly discourage the use of Hungarian notation. Instead, they advocate for using clear and descriptive names that reflect the purpose of variables/functions without relying on prefixes.
>
>Note that not all prefixes are "bad", per se. Using prefixes to represent the scope or duration (e.g. `g`, `s`, `m`) of a variable is useful.

>[!warning]
>It's best to avoid using non-constant global variables. If global access to a variable is required, then consider using a Singleton Pattern, namespace, dependency injection, or thread-local storage.
>- Singleton Pattern : ensures a single instance of a class with global access.
>- Namespace : encapsulates the variable within a namespace.
>- Dependency Injection : passes the variable as a parameter to functions or classes.
>- Threat-local storage : provides each thread with its own instance of the variable.
>
>Refer to [[cpp_global_state_context_objects]]

## Variable shadowing (name hiding)
- When a variable is declared in a block and another variable with the same identifier is declared inside a nested block, the nested variable "hides" the outer variable in areas where they are both in scope.
	- In other words, when an identifier is evaluated, the most immediate variable declared in or outside that scope takes precedence over the variables that are in outer scope.
	- This sort of behavior is called **variable shadowing** or name hiding.
- For example,

```C++
#include <iostream>

int main()
{ // outer block
    int apples { 5 }; // here's the outer block apples

    { // nested block
        // apples refers to outer block apples here
        std::cout << apples << '\n'; // print value of outer block apples

        int apples{ 0 }; // define apples in the scope of the nested block

        // apples now refers to the nested block apples
        // the outer block apples is temporarily hidden

        apples = 10; // this assigns value 10 to nested block apples, not outer block apples

        std::cout << apples << '\n'; // print value of nested block apples
    } // nested block apples destroyed


    std::cout << apples << '\n'; // prints value of outer block apples

    return 0;
} // outer block apples destroyed
```

```console
5
10
5
```

- In the above code, identifier `apples` is used for declaring a variable inside a nested block and a variable in the outer block. When `apples` is called inside a nested block, the nested `apples` is called. When `apples` is called in the outer block, the outer `apples` is called.

>[!important]
>Variable shadowing applies to global variables. Local variables take precedence over global variables.

>[!warning]
>Variable shadowing should generally be avoided.

## Linkage
- The concept of **linkage** determines the visibility and accessibility of names (such as variables, functions, and objects) across different translation units (source files). Linkage specifies whether a name can be referred to from other translation units or only within the same translation unit.
- There are three main types of linkage: internal linkage, external linkage, and no linkage.

### No linkage
- Names with **no linkage** are local to a block or function and cannot be accessed outside of that scope.
	- Local variables have no linkage.

### Internal linkage
- Names with **internal linkage** are visible only within the same translation unit. They cannot be accessed from other translation units.
- Global variables/functions with a `static` keyword has internal linkage.
	- `static` keyword is a storage class specifier, which sets both the name's linkage and its storage duration.
- Constant global variables have internal linkage by default.
	- e.g. `const`, `constexpr`, `consteval`
- Global variables with internal linkage are sometimes called **internal variables**.

>[!important]
>Internal objects/functions that are defined in different files are considered to be independent entities (even if their names and types are identical), so there is no violation of the One-Definition Rule.

#### (note) Usefulness of internal linkage
Internal linkage is useful in several real-life scenarios where you want to limit the visibility of variables or functions to a single translation unit (source file). Here are some examples:

**File-Scope Constants**
When you have constants that are only relevant within a single source file, you can use internal linkage to prevent them from being accessed or modified from other files.

```cpp
static const int MAX_BUFFER_SIZE = 1024; // Internal linkage
```

**Helper Functions**
Helper functions that are only used within a single source file can be given internal linkage to avoid name clashes and to keep the global namespace clean.

```cpp
static void helperFunction() {
    // Implementation
}
```

**File-Scope Variables**
Variables that are only needed within a single source file can be given internal linkage to prevent unintended access or modification from other files.

```cpp
static int counter = 0; // Internal linkage

void incrementCounter() {
    ++counter;
}
```

**Encapsulation**
When implementing a module or library, you might have internal functions or variables that should not be exposed to the users of the module. Using internal linkage helps encapsulate these details.

```cpp
// In a source file of a library
static void internalFunction() {
    // Implementation
}

void publicFunction() {
    internalFunction();
}
```

**Avoiding Name Clashes**
In large projects with many source files, using internal linkage for file-specific variables and functions helps avoid name clashes and reduces the risk of linking errors.

```cpp
// In file1.cpp
static int uniqueID = 1; // Internal linkage

// In file2.cpp
static int uniqueID = 2; // Internal linkage
```

Summary
- **File-Scope Constants**: Constants relevant only within a single source file.
- **Helper Functions**: Functions used only within a single source file.
- **File-Scope Variables**: Variables needed only within a single source file.
- **Encapsulation**: Internal functions or variables in a module or library.
- **Avoiding Name Clashes**: Preventing name clashes in large projects.

Using internal linkage helps maintain encapsulation, reduce the risk of name clashes, and keep the global namespace clean.

#### (note) Static duration
In C++, **static duration** refers to the lifetime of variables that are allocated when the program begins and deallocated when the program ends. These variables are initialized only once, prior to program startup, and retain their values throughout the entire execution of the program.

Key Points about Static Duration:
1. **Lifetime**: The variable exists for the entire duration of the program.
2. **Initialization**: The variable is initialized only once, before the program starts.
3. **Scope**: The scope of the variable can be local (within a function), class-level (static member variables), or global (file scope).

Examples:
- **Static Local Variables**:
```cpp
void exampleFunction() {
    static int count = 0; // Static duration, initialized once
    count++;
    std::cout << count << std::endl;
}
```
Here, `count` retains its value between function calls.

- **Static Member Variables**:
```cpp
class Example {
public:
    static int value;
};

int Example::value = 10; // Static duration, shared among all instances
```
`value` is shared among all instances of the `Example` class.

- **Static Global Variables**:
```cpp
static int globalValue = 5; // Static duration, file scope
```
`globalValue` is accessible only within the file it is declared in.

Static duration is useful for maintaining state information across function calls, sharing data among class instances, and limiting the scope of global variables.

>[!warning]
>Static variables refers to variables with static duration. They do NOT imply that they are internally linked; do not mistake them with `static` variables.

### External linkage
- Names with **external linkage** are visible across multiple translation units. They can be accessed from other source files.
- Non-constant global variables (without `static` keyword) have external linkage.
- Global variables with external linkage are sometimes called **external variables**.
- `extern` keyword can be used to make a global variable external.
	- Naturally, it'll only be useful for constant global variables (e.g. `extern const int x`).
- Forward declaration is necessary in order to access external variables that were defined in another file.
- For a global variable with default external linkage, `extern` keyword is necessary for forward declaration (e.g. `int x` --> `extern int x`).
	- Do not use `extern` keyword for an uninitialized non-constant global variable - not only is it redundant, it's also mistaken as a forward declaration for an external variable.

>[!warning]
>Do not use `extern` keyword for `constexpr`/`consteval` variables. They are meant to be evaluated at compile-time, and so linkage (which happens after compilation is done) is useless.

>[!important]
>Functions are external by default. `extern` keyword is not necessary for forward declaration.

## Avoid non-const global variables
- Although non-const global variables seem useful at first, it's best to avoid it as it becomes a huge problem later on.

### Everything everywhere all at once
- The problem with non-const global variables is that they can be accessed by everything, everywhere, and all at once; which makes the program's state unpredictable.
- Everything : when any function can access a non-const global variable, it becomes difficult to pin down for what reasons the variable has been used for; the purpose of the variable becomes unpredictable, not to mention the current value of the variable.
- Everywhere : in larger projects with many source files, libraries, and people working together, it'd be difficult to know that there is a non-const global variable hidden somewhere; re-definition could occur, value of the variable could be changed, and many things could happen intentionally or unintentionally.
- All at once : in multi-threading/processing program, a non-const global variable that does not have any safeguard against race condition and locks can crash the program.

### Initialization order problem
- Local variables with `static` keyword and global variables have **static duration**, which means that their lifetime begins when program begins and ends when program ends.
	- Note that they are both referred to as **static variable**.
- Static variables are generally initialized in order of definition (there are a few exceptions to this rule), and so it is crucial not to have variables dependent on the initialization value of other variables that won't be initialized until later.
- Consider the following example:

```C++
#include <iostream>

int initX();  // forward declaration
int initY();  // forward declaration

int g_x{ initX() }; // g_x is initialized first
int g_y{ initY() };

int initX()
{
    return g_y; // g_y isn't initialized when this is called
}

int initY()
{
    return 5;
}

int main()
{
    std::cout << g_x << ' ' << g_y << '\n';
}
```

```console
0 5
```

- In the example above, even though at first it looks like `g_x` and `g_y` should have equal value of `5`, `g_x` is given a value `0` because by the time when `initX()` is called, `g_y` is not yet initialized.
- The ambiguity in the order of variable initialization across a single translation unit is bad enough, it gets even worse across multiple translation units.
	- Note that non-const global variables are accessible across all translation units.
	- The ambiguity in the order that objects with static storage duration in different translation units are initialized is often called the **static initialization order fiasco**.

### When to use non-const global variables
- There are very few cases where non-const global variables are useful and should be used:
	- Logging
	- Utility (e.g. random number generator)
	- Global state
- As a rule of thumb, any use of a global variable should meet at least the following two criteria:
	- There should only ever be one of the thing the variable represents in the program
	- Its use should be ubiquitous throughout the program

### How to use non-const global variables
- If there is a good reason to use non-const global variables, then there are a few suggestions to follow:
	- Prefix all non-namespaced global variables with `g` or `g_`.
	- Place global variables in namespace.
	- Encapsulate global variables with a function or a class.
	- Pass global variables as arguments (instead of direct access to one)

#### (Note) Encapsulation
**Encapsulation** is a fundamental concept in object-oriented programming (OOP) which involves bundling data (variables) and methods (functions) that operate on that data into a single unit, typically a class. Encapsulation helps to hide the internal state of an object and restricts direct access to some of its components, which is also known as information hiding.

Key Benefits of Encapsulation:
- **Data Protection**: Encapsulation protects the internal state of an object by keeping its data members private. Access to and modification of these data members is restricted to the class’s public methods, ensuring controlled and secure data manipulation.
- **Information Hiding**: Encapsulation hides the internal implementation details of a class from external code. Only the public interface of the class is accessible, providing abstraction and simplifying the usage of the class while allowing the internal implementation to be modified without impacting external code.
- **Modularity**: Helps in organizing code into logical units, making it easier to manage and understand.
- **Maintainability**: Changes to the internal implementation of a class do not affect external code that uses the class.
- **Control**: Provides control over how data is accessed and modified through methods.

---

Encapsulation is usually done with class (which haven't been covered yet). The main components of encapsulation (and the simplest) are **getter and setter**.

Example:
```C++
class Example {
private:
    int value; // Private variable, not accessible outside the class

public:
    void setValue(int v) {
        value = v; // Public method to set the value
    }

    int getValue() {
        return value; // Public method to get the value
    }
};

```

In the example above, note that `value` is not directly accessible from outside the class. However, indirect access to `value` is given by `setValue()` and `getValue()`. The major advantage from this simple set up is that `setValue()` guarantees type safety (won't accept any value other than `int`).

---

There is a way to use encapsulation with a function (although I'm not sure it counts). A constant global variable with a namespace can be defined in a translation unit, along with a function that simply returns it. Then, in another translation unit, the value of that variable can be accessed via the forward declared function. For example,

constants.cpp
```C++
namespace constants
{
    constexpr double gravity { 9.8 }; // has internal linkage, is accessible only within this file
}

double getGravity() // has external linkage, can be accessed by other files
{
    // We could add logic here if needed later
    // or change the implementation transparently to the callers
    return constants::gravity;
}
```

main.cpp
```C++
#include <iostream>

double getGravity(); // forward declaration

int main()
{
    std::cout << getGravity() << '\n';

    return 0;
}
```

This is a very simple way to implement encapsulation with a function, and so it should only be used in a simple program. Using class is the recommended way.

## Sharing global constants across multiple files
- In some applications, certain symbolic constants may need to be used throughout the code. These can include physics or mathematical constants that doesn't change (e.g. pi, speed of light, etc), or application-specific values (e.g. friction or gravity coefficients).
	- Instead of redefining these constants in every file that needs them, it's better to declare them once in a central location and use them wherever needed. That way, any changes to them will propagated out easily.
- This lesson discusses the most common ways to do this.

### Global constants as internal variables
- Prior to C++17, easiest way to share global constants is:
	1. Create a header file to hold the constants
	2. Inside the header file, define a namespace
	3. Add all constants inside the namespace (make sure they're `constexpr`)
	4. `#include` the header file wherever needed
- For example:

constants.h
```C++
#ifndef CONSTANTS_H
#define CONSTANTS_H

// define your own namespace to hold constants
namespace constants
{
    // constants have internal linkage by default
    constexpr double pi { 3.14159 };
    constexpr double avogadro { 6.0221413e23 };
    constexpr double myGravity { 9.2 }; // m/s^2 -- gravity is light on this planet
    // ... other related constants
}
#endif
```

main.cpp
```C++
#include "constants.h" // include a copy of each constant in this file

#include <iostream>

int main()
{
    std::cout << "Enter a radius: ";
    double radius{};
    std::cin >> radius;

    std::cout << "The circumference is: " << 2 * radius * constants::pi << '\n';

    return 0;
}
```

- Because theses constants are `constexpr`, they will have internal linkage. Also, in most cases, they will be optimized away.
- The downside to this "global constants as internal variables" approach is that every time `constants.h` header file gets include into a different code file, each of these constants is copied into the including code file. This issue further leads to two challenges:
	- Changing a single constant value would require recompilation of every code file that includes the constants header.
	- If the constants are large in size and can't be optimized away, this can use a lot of memory.

>[!important]
>`constexpr` variables are implicitly internal. When these constants are defined in a header file and then distributed in multiple source files, these constants are being defined in each translation unit; thus, it does not trigger redefinition error. However, this means "global constants as internal variables" does suffer from duplications.

### Global constants as external variables
- A way to circumvent the problems that "global constants as internal variables" have is to have global constants as external variables instead, so that there will be only one initialization of the constants and they can be shared with multiple files.

>[!warning]
>Just because one method has a way to fix a problem that another method has, doesn't mean it's better. Each method has their own advantages and disadvantages.

>[!warning] Possible errors in this section of the lesson
>Maybe I'm just not understanding things correctly, but it seems like this section of the lesson has either a wrong information or skipped over a critical information. For example, (1) even though in previous lessons it is mentioned that `constexpr` variables can NOT be forward declared, it does so anyway in this section. (2) the `constexpr` variables are forward declared as `const` variables - without any explanation on how that works.
>
>Due to the reasons above, I've made slight modification to this section; with different codes and different explanations.

- Without getting too much into details, the gist here is that global constants are defined in a source file, which is then forward declared in a header file; the header file is included wherever the constants are needed.
- For example:

constants.cpp
```C++
#include "constants.h"

namespace constants
{
    const double pi { 3.14159 };
    const double avogadro { 6.0221413e23 };
    const double myGravity { 9.2 };
}
```

constants.h
```C++
#ifndef CONSTANTS_H
#define CONSTANTS_H

namespace constants
{
    extern const double pi;
    extern const double avogadro;
    extern const double myGravity;
}

#endif
```

main.cpp
```C++
#include "constants.h" // include all the forward declarations

#include <iostream>

int main()
{
    std::cout << "Enter a radius: ";
    double radius{};
    std::cin >> radius;

    std::cout << "The circumference is: " << 2 * radius * constants::pi << '\n';

    return 0;
}
```

>[!reminder] `extern` keyword means "look elsewhere for definition".

- While this approach does solve the duplication problem that the "global constants as internal variables" approach has, its downside is that the constants are evaluated at runtime - meaning, optimization opportunities are limited.
	- Though, runtime constants do have the advantage that even if any of the constants change, recompilation is not necessary.

### Global constants as inline variables (C++17)

>[!reminder] Reminder from [[#Inline functions and variables]]
>`inline` keyword means "multiple definitions are allowed" - thus, an inline function is one that is allowed to be defined in multiple translation units.
>
>Inline functions have two primary requirements:
>- The compiler needs to be able to see the full definition of an inline function in each translation unit where the function is used; forward declaration alone does not suffice.
>- Every definition for an inline function must be identical, otherwise undefined behavior will result.
>
>(C++17) inline variables work similarly to inline functions, and have the same requirements.

>[!important]
>The evaluation of `inline` variables involves both the compiler and the linker, but their roles are distinct.
>
>The compiler processes the definition and usage of `inline` variables. When an `inline` variable is defined in a header file, the compiler ensures that the variable is available in all translation units that include the header.
>
>The linker handles the fact that `inline` variables can be defined in multiple translation units. It ensures that there is only one instance of the `inline` variables in the final executable, avoiding redefinition errors (also avoiding duplications).

>[!important]
>While `constexpr` functions are implicitly inline, `constexpr` variables are NOT implicitly inline. If an inline constexpr variable is needed, then `inline` keyword must be used.

>[!important]
>Non-inline constexpr variables have internal linkage. If included into multiple translation units, each translation unit will get its own copy of the variables; which is not an ODR violation because they are not exposed to the linker.

- A way to avoid the duplication problem while also ensuring the global constants are evaluated at compile time, is to define the global constants as inline variables. For example:

constants.h
```C++
#ifndef CONSTANTS_H
#define CONSTANTS_H

// define your own namespace to hold constants
namespace constants
{
    inline constexpr double pi { 3.14159 }; // note: now inline constexpr
    inline constexpr double avogadro { 6.0221413e23 };
    inline constexpr double myGravity { 9.2 }; // m/s^2 -- gravity is light on this planet
    // ... other related constants
}
#endif
```

main.cpp
```C++
#include "constants.h"

#include <iostream>

int main()
{
    std::cout << "Enter a radius: ";
    double radius{};
    std::cin >> radius;

    std::cout << "The circumference is: " << 2 * radius * constants::pi << '\n';

    return 0;
}
```

- Because the global constants are evaluated at compile-time, this method does have the downside that the source files that include the constants header has to be recompiled if any constant value is changed.

## Static local variables and its uses
### Static local variables
- As previously mentioned in [[#Internal linkage]], `static` keyword gives a global identifier an internal linkage. In this section, we'll learn what `static` keyword does to a local variable.
- Local variables have automatic duration by default, which means they are created at the point of definition, and destroyed when the block is exited.
- Using the `static` keyword on a local variable changes its duration from automatic duration to static duration, which means the variable is created at the start of the program, and destroyed at the end of the program.
- For example:

```C++
#include <iostream>

void incrementAndPrint()
{
    static int s_value{ 1 };
    ++s_value;
    std::cout << s_value << '\n';
}

int main()
{
    incrementAndPrint();
    incrementAndPrint();
    incrementAndPrint();

    return 0;
}
```

```console
2
3
4
```

- In the example above, `s_value` is initialized with `1` and then it gets incremented by `1` each time `incrementAndPrint()` is called.

>[!important]
>While static variables are not destroyed outside its block, it is also not accessible outside it.

- Static local variables that have a constexpr initializer can be initialized at program start.
- Static local variables that have non-constexpr initializer are zero-initialized at program start.
	- They are reinitialized the first time the variable definition is encountered.
	- The definition is skipped on subsequent calls, so no further reinitialization happens.
- Static local variables that have no initializer is zero-initialized at program start.

>[!important]
>A `constexpr` initializer is an initializer for a variable (or a function) that is evaluated at compile time; it involves not just a constant literals, but also more complex expressions and function calls that are evaluated at compile time.

>[!important]
>`static` keyword gives a variable **internal linkage** (one definition in a single translation unit) and **static duration** (creation at start of program, destruction at end of program).

### ID generation (or counter)
- One of the most common uses for static local variables is for unique ID generators.
- For example:

```C++
int generateID()
{
    static int s_itemID{ 0 };
    return s_itemID++;
}
```

- In the above example, `generateID()` will return `0` the first time it's called, and then each time it is called, it returns a number higher than the previous time it was called.
	- Because `s_itemID` is a local variable, it cannot be accessed directly; thus, it is safe its value and/or type being changed.
	- Because the returned value never repeats, it is unique - which makes it perfect for generating IDs.
	- The postfix `++` operator returns the value first and then increments the value.

>[!important]
>Static local variables can be used when a function needs a persistent object that is not directly accessible outside of the function.

### Scope, duration, and linkage summary
This chapter overall was rather complicated, with so many keywords and intertwining effects. Refer to the summary and the tables within in this [section](https://www.learncpp.com/cpp-tutorial/scope-duration-and-linkage-summary/).

## Using declarations and using directives

>[!warning] tldr; DO NOT USE `using` DECLARATIONS/DIRECTIVES!!

## Unnamed and inline namespaces (optional)
### Unnamed (anonymous) namespaces
- An unnamed namespace (aka anonymous namespace) is a namespace that is defined without a name.
- For example:

```C++
#include <iostream>

namespace // unnamed namespace
{
    void doSomething() // can only be accessed in this file
    {
        std::cout << "v1\n";
    }
}

int main()
{
    doSomething(); // we can call doSomething() without a namespace prefix

    return 0;
}
```

- All content declared in an unnamed namespace is treated as if it is part of the parent namespace.
- All identifiers inside an unnamed namespace are treated as if they have internal linkage.
	- This is effectively the same as defining a function as a static function.

>[!important]
>Unnamed namespaces are typically used when there are a lot of content that needs to stay local to a given translation unit, as it's easier than to mark all declarations as `static`.

>[!warning]
>Unnamed namespaces should generally not be used in header files, as every translation that includes that header will get its own copy of the namespaced content, leading to code bloat.

### Inline namespaces
- `inline` keyword can be used on a namespace as well, and the effect is that the namespace is considered a part of the parent namespace but without affecting its own linkage.
	- Normally a function or a variable inside a named namespace is called from its namespace (e.g. `foo::bar()`), but with the `inline` namespace, the function is called as if its part of the parent namespace (e.g. `bar()`).
- Inline namespaces are commonly used for managing different versions of a function. For example:

```C++
#include <iostream>

inline namespace V1 // declare an inline namespace named V1
{
    void doSomething()
    {
        std::cout << "V1\n";
    }
}

namespace V2 // declare a normal namespace named V2
{
    void doSomething()
    {
        std::cout << "V2\n";
    }
}

int main()
{
    V1::doSomething(); // calls the V1 version of doSomething()
    V2::doSomething(); // calls the V2 version of doSomething()

    doSomething(); // calls the inline version of doSomething() (which is V1)

    return 0;
}
```

```console
V1
V2
V1
```

- In the example above, `doSomething()` is in two different namespaces that represent its versions. By placing an `inline` keyword next to a namespace, it essentially achieves selecting a version of a function to use.

## Intro to control flow
- The specific sequence of statements that the CPU executes is called the program's **execution path**.
- When the statements are executed from top to bottom line by line, the execution path is said to be straight; thus, the program itself is referred to as **straight-line program**.
	- A straight-line program isn't something that is often desired; as most programs deal with different scenarios that handling it requires going back and forth to different parts of the program.
- **Control flow statements** are statements that allow the programmer to change the normal path of execution through the program.
	- When a control flow statement causes point of execution to change to a non-sequential statement, this is called **branching**.

### Categories of flow control statements
- There are 6 control flow statements:
	- Conditional statements
	- Jumps
	- Function calls
	- Loops
	- Halts
	- Exceptions
- Each of these control flow statements will be covered in future lessons.

## If statements and blocks
- One of the control flow statements is a conditional statement, which is a statement that specifies whether some associated statement(s) should be executed based on given conditions.
	- This was briefly covered back in [[#Intro to if statements]]
- Structure of conditional statement:

```C++
if (conditionA)
{
	// statement if conditionA is true
}
else if (conditionB)
{
	// statement if conditionB is true
}
else 
{
	// statemtnt if neither of the statements are true
}
```

### Constexpr if statements (C++17)
- C++17 introduces the **constexpr if statement**, which requires the conditional to be a constant expression.
	- The conditional will be evaluated at compile-time.
- If the constexpr conditional evaluates to `true`, the entire conditional statement block will be replaced by the true statement.
	- If `false`, then it'll be replaced with the false statement.
- For example:

```C++
#include <iostream>

int main()
{
	constexpr double gravity{ 9.8 };

	if constexpr (gravity == 9.8) // now using constexpr if
		std::cout << "Gravity is normal.\n";
	else
		std::cout << "We are not on Earth.\n";

	return 0;
}
```

- In the example above, the entire conditional statement is replaced with the true statement, `std::cout << "Gravity is normal.\n";`.

>[!important]
>Favor constexpr if statements over non-constexpr if statements when the conditional is a constant expression.
>
>Modern compilers will generally treat non-constexpr if statements that have constexpr conditional as if they were constexpr if statements. However, they are not required to do so.

## Intro to switch statement
### Switch statement
- The switch statement is a flow control statement that is used to execute the different blocks of statements based on the value of the given expression.
	- Many different cases can be set for different values of the switch expression.
	- The case value can only be of type `int` or `char`.
	- If a corresponding case for the value of the switch expression is not found, then the default statement is executed (if set).
	- Each case needs to include `break;` so that the switch statement can close once a case statement is executed.
- The structure of the switch statement goes something like this:

```C++
switch (x)
{
case 1:
	// case 1 statement executes if x == 1
	break;
case 2:
	// case 2 statement executes if x == 2
	break;
default:
	// default statement
	break;
}
```

- Note that the `case` keyword followed by a constant expression is referred to as the **case label**.
	- For `default`, it would be **default label**.
- Note that the indent levels of the labels are at the same level as the switch statement, and the case statements are indented by one level.
	- Labels do not define a nested level, and so it's not necessary to indent the case statements. However, that would look unreadable. So, the best compromise is to have the case statements indented by one level (as opposed to two).

>[!important]
>Switch statement is highly optimized in the sense that it can "jump" directly to the result, as opposed to doing a sequential comparisons like an if statement. That's why the switch only allows its conditional expression to be an integral type.
>
>Switch statement should be used over if statement whenever possible.

>[!important]
>If the switch statement is inside a function, `return` can be used instead of `break` (if no further execution is required).

### Fallthrough
- If `break` is not used in a switch case, the program will continue to execute the subsequent cases until it encounters a `break` or reaches the end of the switch statement - this behavior is known as **fallthrough**.
- Since fallthrough is rarely desired or intentional, many compilers (and code analysis tools) will flag fall-through as a warning.
- (C++17) in the rare case when fall-through is necessary, an attribute called `[[fallthrough]]` can be placed at the end of the case statement (that requires fallthrough).
	- Attributes are not statements, but they do modify null statements - meaning, `;` should follow where the attribute is placed.
- For example:

```C++
#include <iostream>

int main()
{
    switch (2)
    {
    case 1:
        std::cout << 1 << '\n';
        break;
    case 2:
        std::cout << 2 << '\n'; // Execution begins here
        [[fallthrough]];
    case 3:
        std::cout << 3 << '\n'; // This is also executed
        break;
    }

    return 0;
}
```

```console
2
3
```

- Once the fallthrough attribute is set in place, there shouldn't be any warnings about it.

### Sequential case labels
- Case labels can be stacked sequentially in order to implement logical OR for situations where a statement should be executed when any one of multiple cases (its values) match the switch value.
- For example:

```C++
bool isVowel(char c)
{
    switch (c)
    {
    case 'a': // if c is 'a'
    case 'e': // or if c is 'e'
    case 'i': // or if c is 'i'
    case 'o': // or if c is 'o'
    case 'u': // or if c is 'u'
    case 'A': // or if c is 'A'
    case 'E': // or if c is 'E'
    case 'I': // or if c is 'I'
    case 'O': // or if c is 'O'
    case 'U': // or if c is 'U'
        return true;
    default:
        return false;
    }
}
```

### Variable declarations and initializations inside switch/case statements
- Variable declarations/definitions (e.g. `int x;`) are allowed inside the switch statement, either before or after the case labels.
	- However, it is a bad practice to declare/define a variable after the case labels (inside the case statement). It'd be difficult to know if a variable is defined or not.
- Variable initialization (e.g. `int x = 4;`) is not allowed inside the switch statement.
- Variable assignment (e.g. `x = 4;`) is allowed inside the switch statement.
- Variable declaration/definition can be used inside the case statement only if the case statement is inside an explicit block. For example:

```C++
switch (1)
{
case 1:
{
    int x{ 4 };
    std::cout << x;
    break;
}

default:
    std::cout << "default case\n";
    break;
}
```

## Goto statements
- Goto statement is a control flow statement that causes the program to do an unconditional jump, where the execution jumps from the spot where `goto` is stated to the spot where a statement label is located, unconditionally.
	- Goto statement looks like this - `goto statementLabel;`, `statementLabel:`
	- Code that follows the statement label is NOT a nested block.
	- Though it is unconditional, it often accompanies an if-statement.
- For example:

```C++
#include <iostream>
#include <cmath> // for sqrt() function

int main()
{
    double x{};
tryAgain: // this is a statement label
    std::cout << "Enter a non-negative number: ";
    std::cin >> x;

    if (x < 0.0)
        goto tryAgain; // this is the goto statement

    std::cout << "The square root of " << x << " is " << std::sqrt(x) << '\n';
    return 0;
}
```

- In the example above, `goto tryAgain;` makes execution jump to where `tryAgain:` is located.

>[!warning] Avoid using goto statements
>The use of goto statement is shunned, for a good reason. The primary problem with goto is that it allows a programmer to jump around the code arbitrarily. This creates what is not-so-affectionately known as **spaghetti code**, which is to say a code is all tangled and twisted like a bowl of spaghetti.
>
>	"The quality of programmers is a decreasing function of the density of goto statements in the programs they produce." - Edsger W. Dijkstra
>A little joke from [xkcd](https://xkcd.com/292/):
>![[xkcd_goto.png]]

>[!important] .. unless the alternative is comparably worse
>One notable usage of goto statement is exiting a nested loop.

## Intro to loops and while statements
### While statements
- **Loops** are control flow constructs that allow a piece of code to execute repeatedly until some condition is met.
- The while statement (aka while loop) is an implementation of loop using keyword `while` followed by a conditional expression.
	- While statement will keep looping as long as the condition continues to evaluate to `true`. In another words, the while loop will end if condition returns `false`.
- The structure of a while loop looks like this:

```C++
while (condition)
{
	// statement goes here
}
```

- For example:

```C++
#include <iostream>

int main()
{
    int count{ 1 };
    while (count <= 10)
    {
        std::cout << count << ' ';
        ++count;
    }

    std::cout << "done!\n";

    return 0;
}
```

- The code above prints a number `1` through `10` using a while loop.
- Note that if the condition initially evaluates to `false`, then the associated statement (the code inside the while loop) will not execute at all.
- If while loop condition always evaluates to `true` (e.g. `true`), the while loop will execute infinitely - such loop is called an **infinite loop**.

>[!important]
>There are many use of infinite loops - such as game loop, render loop, window loop, and etc.

>[!warning]
>Make sure to implement an exit strategy when using an infinite loop - such as `return`, `break`, or `goto`.

>[!important] While loops can be nested, but it gets confusing real quick.

### Loop variables
- A **loop variable** is a variable that is used inside a conditional expression to control how many times a loop executes.
	- Loop variable is part of the loop logic that states "Run this loop until `x` reaches a set limit; increment/decrement `x`".
- For example, given `while (count <= 10)`, the loop variable is `count`. Once `count` goes above `10`, the while loop will stop.
- Loop variables are often given simple names - with `i`, `j`, and `k` being the most common.
	- It's better to use more intuitive variable names, such as `count` and `index`.
- The most common type of loop variable is called a **counter**, which is a loop variable that counts how many times a loop has executed.

>[!important] Loop variables should generally be a signed integral type.

### Iteration
- Each execution of a loop is referred to as an **iteration**.
- Using a counter as a loop variable is useful to implement "Do something at every Nth iteration" logic.
	- For example, `if (count % 10 == 0)` can be used to execute a code at every 10th iteration.

### Do while statements
- A **do while statement (do-while loop)** is a looping construct that works just like a while loop, except the statement is executed before the condition (meaning the statement always executes at least once).
- For example:

```C++
#include <iostream>

int main()
{
    int selection{};

    do
    {
        std::cout << "Please make a selection: \n";
        std::cout << "1) Addition\n";
        std::cout << "2) Subtraction\n";
        std::cout << "3) Multiplication\n";
        std::cout << "4) Division\n";
        std::cin >> selection;
    }
    while (selection < 1 || selection > 4);

    std::cout << "You selected option #" << selection << '\n';

    return 0;
}
```

- In the example above, the code following `do` will execute first and then the `while` condition is checked before going back to `do`.

>[!important]
>In practice, do-while loops aren't commonly used. Having the condition at the bottom of the loop obscures the loop condition, which can lead to errors. It's best to favor while loops over do-while loops when given an equal choice.

## For statements (classic)
- There are two kinds of for-statements. In this lesson, the classic for-statement is covered.
- The **for-statement (for-loop)** is an implementation of loop using keyword `for` followed by three statements (init-statement, condition, and end-expression) that govern the state of a loop variable which, in turn, governs the iterations of the loop.
- For-statement is evaluated in 3 parts:
	- **Init-statement** is a statement that is executed only once at the beginning of the loop. It is typically used to define and initialize a loop variable (e.g. `int x = 1;`).
	- **Condition** is a statement that is executed at the beginning of each iteration, typically used to check if the loop variable satisfies a certain condition (e.g. `x <= 10;`).
	- **End-expression** is a statement that is executed at the end of each iteration, typically used to increment or decrement the loop variable (e.g. `++x;`).
- The basics of the for-loop is that the loop will continue to iterate until a loop variable `x` reaches a certain value. It is useful for setting exactly how many times a loop will iterate.
- The loop variable is within the loop scope, where the variable exists from the point of definition through the end of the loop statement.
	- All variables declared or defined within the for-statement is within the loop scope.
- For example:

```C++
#include <iostream>

int main()
{
    for (int i{ 1 }; i <= 10; ++i)
        std::cout << i << ' ';

    std::cout << '\n';

    return 0;
}
```

```console
1 2 3 4 5 6 7 8 9 10
```

- The for-statement is a nice alternative to the while statement that uses a counter.

>[!warning] Avoid using `!=` operator for for-loop condition.

>[!warning]
>It is possible to omit init-statement, condition, and end-expression in the for-statement (e.g. `for (;;)`). It is recommended to avoid this form of the for-loop.

>[!important] Using multiple for-loop variables is possible and allowed..
>But really, is that necessary?

## Break, return, and continue
- The `break` statement can be used in any control flow statements (switch, while, do-while, and for) to stop the control flow statement to executing any further.
- `break` is a common way to get out of an intentional infinite loop.
- If a control flow statement is being used inside a function, `return` statement can be used to terminate the entire function, which in turn terminates the control flow statement early.
	- A return statement that is not the last statement in a function is called an **early return**.
- The `continue` statement provides a way to end the current iteration of a loop without terminating the entire loop. In other words, `contiue;` skips to the end of the current iteration.

>[!warning]
>If a loop variable (e.g. `counter`) is used to control the iterations, be careful not to skip over the code that increments/decrements the loop variable with a `continue` statement - doing so may cause the loop to become infinite.

## Halts (manually exiting the program early)
- Skipped because it never should be used.
- Refer to https://www.learncpp.com/cpp-tutorial/halts-exiting-your-program-early/

## Intro to random number generation
### Algorithms and state
- An **algorithm** is a finite sequence of instructions that can be followed to solve some problem or produce some useful result.
- An algorithm is considered to be **stateful** if it retains some information across calls. Conversely, a stateless **algorithm** does not store any information.
- An algorithm is considered **deterministic** if it will always produce the same output sequence for a given input.

### Pseudo-random number generators (PRNGs)
- A **pseudo-random number generator (PRNG)** is an algorithm that generates a sequence of numbers whose properties approximate a sequence of random numbers.
	- A "true" random is nearly impossible to generate with a software alone. It requires a hardware that can measure some physical phenomenon that is expected to be random.
	- PRNG is also known as **deterministic random bit generator (DRBG)**. It is deterministic in the sense that it requires a use of **random seed** (an initial value), and the sequence of the generated random numbers can be replicated using that seed.
- A short PRGN example that generates 100 16-bit pseudo-random numbers:

```C++
#include <iostream>

// For illustrative purposes only, don't use this
unsigned int LCG16() // our PRNG
{
    static unsigned int s_state{ 0 };

    s_state = 8253729 * s_state + 2396403;
    return s_state % 32768;
}

int main()
{
    // Print 100 random numbers
    for (int count{ 1 }; count <= 100; ++count)
    {
        std::cout << LCG16() << '\t';

        // If we've printed 10 numbers, start a new row
        if (count % 10 == 0)
            std::cout << '\n';
    }

    return 0;
}
```

- In the example above, each number generated is the result of some mathematical operation of its previous number.
	- The random number generated becomes the current state of the algorithm.
	- This particular algorithm has an issue where each result alternates between even and odd.
	- Most PRNGs work similarly to the code above, except they use more state variables and more complex mathematical operations.

### Characteristics of a good PRNG
- The quality of a random number generator depends highly on its capability to generate each number with approximately the same probability. In other words, random number generation with **distribution uniformity**.
	- If some numbers are generated more often than others, then the random number generator is said to be **biased**.
- The method by which the next number in the sequence is generated shouldn't be predictable.
	- Simply incrementing the state guarantees uniformity, but it is very much predictable.
	- More state variables and more complex mathematical operations help make PRNGs unpredictable.
- The PRNG should have a good dimensional distribution of numbers; meaning, it should make use of the entire range of possible results.
	- Entire range, meaning high numbers, middle numbers, low numbers, even numbers, and odd numbers.
- The PRNG should have a high period for all seeds.
	- All PRNGs are periodic, which means that at some point the sequence of numbers generated will begin to repeat itself (e.g. `1 2 3 1 2 3`).
- The PRNG should be efficient.
	- Though more states and more complex mathematical operations helps make PRNG unpredictable, it also makes it bigger and slower. So there's a fine line between too little and too much.

### Randomization from STD
- C++ provides randomization capabilities via the `<random>` header of the standard library.
- Within the library, there are 6 PRNG families available for use (as of C++20):
	- `minstd_rand` : Linear congruential generator
	- `mt19937` : Mersenne twister
	- `ranlux24` : Subtract and carry
	- `knuth_b` : Shuffled linear congruential generator
	- `default_random_engine` : Any of the above (implementation defined)
	- `rand()` : Linear congruential generator (Compatible with C)
- There is zero reason to use `knuth_b`, `default_random_engine`, and `rand()`.
- As of C++20. the Mersenne Twister algorithm is the only PRNG that has both decent performance and quality.

>[!important]
>A test called [PracRand](https://pracrand.sourceforge.net/) is often used to assess the performance and quality of PRNGs. There are other tests such as SmallCrush, Crush, and BigCrush.

### Third party randomization libraries
- Randomizers provided via the standard library isn't quite enough to make a statistical simulation or programs that deal with cryptography. There are third party libraries for such purpose:
	- For non-cryptographic PRNGs: [Xoshiro](https://prng.di.unimi.it/), [RapidHash](https://github.com/Nicoshev/rapidhash)
	- For cryptographic PRNGs: [ChaCha](https://cr.yp.to/chacha.html)

### Using Mersenne Twister
- The Mersenne Twister PRNG is the most popular PRNG across all programming languages. Although it is a bit old by today's standards, it generally produces quality results and has decent performance.
- The random library has support for two Mersenne Twister types:
	- `mt19937` is a MT that generates 32-bit unsigned integers.
	- `mt19937_64` is a MT that generates 64-bit unsigned integers.
- Example:

```C++
#include <iostream>
#include <random> // for std::mt19937

int main()
{
	std::mt19937 mt{}; // Instantiate a 32-bit Mersenne Twister

	// Print a bunch of random numbers
	for (int count{ 1 }; count <= 40; ++count)
	{
		std::cout << mt() << '\t'; // generate a random number

		// If we've printed 5 numbers, start a new row
		if (count % 5 == 0)
			std::cout << '\n';
	}

	return 0;
}
```

>[!important]
>Note that `mt19937` is initialized as a variable, and yet used like a function. There is, in fact, a member function `operator()` that is invoked using the variable name like a function.

### Random Number Distribution
- A 32-bit PRNG will generate random numbers between `0` and `4294967295`.
- There are times when applications do not require a full range of random numbers - but a small range of numbers.
	- An example of that is a Dice game - which requires random numbers in range `1` through `6`.
- A **random number distribution** converts the output of a PRNG into some other distribution of numbers.
	- The most notable random number distribution is **uniform distribution**, which produces outputs between two numbers (inclusive) with equal probability.
	- The random library provides `std::uniform_int_distribution` for that purpose.
- An example of a Dice game that uses uniform distribution:

```C++
#include <iostream>
#include <random> // for std::mt19937 and std::uniform_int_distribution

int main()
{
	std::mt19937 mt{};

	// Create a reusable random number generator that generates uniform numbers between 1 and 6
	std::uniform_int_distribution die6{ 1, 6 }; // for C++14, use std::uniform_int_distribution<> die6{ 1, 6 };

	// Print a bunch of random numbers
	for (int count{ 1 }; count <= 40; ++count)
	{
		std::cout << die6(mt) << '\t'; // generate a roll of the die here

		// If we've printed 10 numbers, start a new row
		if (count % 10 == 0)
			std::cout << '\n';
	}

	return 0;
}
```

### Random seed
- The major problem with PRNGs is that they are deterministic - meaning that they use a seed to initialize the generator, and the sequence of random numbers can be replicated using that same seed.
- In order to circumvent the problem above is to use a number that constantly changes instead of a fixed number. There are two common methods to implement this:
	- Use the system clock
	- Use the system's random device

>[!warning] It's best to seed PRNG only once; DO NOT RESEED.


### Seeding with the system clock
- The C++ standard library provides `std::time()` from `<ctime>` header which returns the current time. PRNGs have a long history of using the current time as its seed.
	- Refer to https://en.cppreference.com/w/cpp/chrono/c/time
- C++ also offers a `<chrono>` header that contains various clocks.
	- `<ctime>` is a C-style header. It's old, not type safe and not as accurate as `<chrono>`.
	- `<chrono>` is contemporary C++ header, it's type safe, and as accurate as the hardware allows. It has extended functionality, and it follows C++ logic (rather than C) so that certain things will be more natural/expressive with C++.
- Example of seeding PRNG with chrono time:

```C++
#include <iostream>
#include <random> // for std::mt19937
#include <chrono> // for std::chrono

int main()
{
	// Seed our Mersenne Twister using steady_clock
	std::mt19937 mt{ static_cast<std::mt19937::result_type>(
		std::chrono::steady_clock::now().time_since_epoch().count()
		) };

	// Create a reusable random number generator that generates uniform numbers between 1 and 6
	std::uniform_int_distribution die6{ 1, 6 }; // for C++14, use std::uniform_int_distribution<> die6{ 1, 6 };

	// Print a bunch of random numbers
	for (int count{ 1 }; count <= 40; ++count)
	{
		std::cout << die6(mt) << '\t'; // generate a roll of the die here

		// If we've printed 10 numbers, start a new row
		if (count % 10 == 0)
			std::cout << '\n';
	}

	return 0;
}
```

- The advantage of the approach above is that the sequence of random numbers is different each time it is ran. However, it is not perfect because if it is ran in quick succession, the seeds generated for each run won't be that different, which can impact the quality of the random results from a statistical standpoint.
- `std::chrono::high_resolution_clock` can be preferred over `steady_clock` because it uses the most granular unit of time.
	- However, `high_resolution_clock` uses the system clock for the current time, which can be changed/rolled back by users. For this reason, `steady_clock` can be preferred instead (it guarantees that users cannot adjust time).

### Seeding with the random device
- The random library contains a type called `std::random_device` that is an implementation-defined PRNG; meaning, the OS will generate a pseudo-random number if it is implemented on their system.
	- Note that `std::random_device` may not work if it is NOT implemented by the OS.
	- Also note that the implementation is NOT required to be non-deterministic, meaning it could produce the same random number sequence on the same OS (though generally not the case).
- For example:

```C++
#include <iostream>
#include <random> // for std::mt19937 and std::random_device

int main()
{
	std::mt19937 mt{ std::random_device{}() };

	// Create a reusable random number generator that generates uniform numbers between 1 and 6
	std::uniform_int_distribution die6{ 1, 6 }; // for C++14, use std::uniform_int_distribution<> die6{ 1, 6 };

	// Print a bunch of random numbers
	for (int count{ 1 }; count <= 40; ++count)
	{
		std::cout << die6(mt) << '\t'; // generate a roll of the die here

		// If we've printed 10 numbers, start a new row
		if (count % 10 == 0)
			std::cout << '\n';
	}

	return 0;
}
```

>[!warning] Only use `std::random_device` as random seed, NOT as PRNG.

### Seed quality and underseeding
- The theoretical maximum number of unique sequences that a PRNG can generate is determined by the number of bits in the PRNG's state.
	- For example, a PRNG with `128` bits of state can theoretically generate up to `2^128` unique output sequences.
- The actual output sequence generated depends on the initial state of the PRNG, which is determined by the seed. Therefore, practically speaking, the number of unique output sequences a PRNG can actually generated is limited by the number of unique seed values given to the PRNG.
	- For example, if a particular seed generation algorithm can only generate 4 different seed values, then the PRNG will only be able to generate at most 4 different output sequences.
- When a PRNG is not provided with enough bits of quality seed data, it is said to be **underseeded**.
- An underseeded PRNG may exhibit any of the following issues:
	- The random sequences generated by the consecutive runs may have a high correlation to each other.
	- Some values will never be able to be generated.
	- The seeds may become predictable, which would make the random numbers predictable.
- A **stuck bit** refers to a bit in the seed value that is always set to either 0 or 1, regardless of the intended randomness.
	- The random number generator that uses a seed with a stuck bit becomes less effective at producing random sequences.
	- For example, if a seed value is supposed to be 32-bit number but one of the bits is always stuck at 0, then the seed can only take on `2^31` unique values instead of `2^32`.
- Stuck bits are caused by hardware, software, or environmental factors.
	- For example, seeding with system clock leads to a stuck bit problem due to the fact that bits that represent larger time units (e.g. years) are effectively stuck.

>[!important]
>Some PRNGs have huge states (e.g. the Mersenne Twister has 19937 bits), and generating quality seeds to match that can be difficult. As a result, PRNGs with large states are often designed to be resilient to being seeded with fewer bits.

### Seed sequence
- The Mersenne Twister has huge state (like 19937 bits) due to the fact that it uses 624 integral values, with each integral value 32-bit or 64-bit in size.
	- When MT is given a random seed (by using the clock or `std::random_device`), the seed is only a single value. This means MT is significantly underseeded, and it has to fill the rest 623 values with "random" data; which is suboptimal.

>[!warning]
>Seeding `std::mt19937` with a single 32-bit value will never generate the number `42` as its first output.

- A way to get around the underseeding problem is to use a seed sequence, which can take in one or more seeds to generate an unbiased sequence of seeds.
	- The random library provides `std::seed_seq` just for this purpose.
	- The seeds given to the seed sequence can be of identical values, but they do lose some quality.

>[!important]
>A good way to get the best use out of the seed sequence is to supply it quality seeds, such as the system clock and the random device.

- When `std::seed_seq` is provided to the `std::mt19937`, the PRNG uses the seed sequence to generate 624 integral values. This ensures that the initial values in the state array are well-distributed and have high entropy, which improves the quality of the random numbers generated.
- Example of using `std::seed_seq` (w/ random device) and `std::mt19937`:

```C++
#include <iostream>
#include <random>

int main()
{
	std::random_device rd{};
	std::seed_seq ss{ rd(), rd(), rd(), rd(), rd(), rd(), rd(), rd() }; // get 8 integers of random numbers from std::random_device for our seed
	std::mt19937 mt{ ss }; // initialize our Mersenne Twister with the std::seed_seq

	// Create a reusable random number generator that generates uniform numbers between 1 and 6
	std::uniform_int_distribution die6{ 1, 6 }; // for C++14, use std::uniform_int_distribution<> die6{ 1, 6 };

	// Print a bunch of random numbers
	for (int count{ 1 }; count <= 40; ++count)
	{
		std::cout << die6(mt) << '\t'; // generate a roll of the die here

		// If we've printed 10 numbers, start a new row
		if (count % 10 == 0)
			std::cout << '\n';
	}

	return 0;
}
```

- Although it's possible to give 624 values of `std::random_device` to `std::seed_seq`, it would likely be slow and risks depleting the pool of random numbers that `std::random_device` uses.
	- Not only that, using same seed values do deteriorate quality a bit.
- There's no need to use one type of seeds, it's better to use a mixture of them; mixing the system clock, random device, or even things like current thread id, address of particular functions, user id, process id, and etc. will work.

>[!important] Warm up the PRNGs
>PRNGs often benefit from "warming up", that is, discarding a certain number of initial values generated before using it for actual random number generation. This is because PRNGs can sometimes exhibit patterns or biases in the initial values they generated; warming up helps ensure that the PRNG reaches a more stable and well-distributed state.

>[!important] Specific values for debugging
>For debugging purposes, it's better to use a specific value (e.g. `5`) to ensure that the program behaves the same way each time it runs. Once everything does execute properly, then it's safe to use seeding techniques.

### Global random numbers (Random.h)
See https://www.learncpp.com/cpp-tutorial/global-random-numbers-random-h/ for writing a random generator that can be used globally. Note that some of the stuff (e.g. Templates) wasn't covered in previous lessons, so that's why I'm skipping it.

## Intro to testing
Refer to https://www.learncpp.com/cpp-tutorial/introduction-to-testing-your-code/

## Code coverage
Refer to https://www.learncpp.com/cpp-tutorial/code-coverage/

## Common semantic errors
Refer to https://www.learncpp.com/cpp-tutorial/common-semantic-errors-in-c/

## Detecting and handling errors
Refer to https://www.learncpp.com/cpp-tutorial/detecting-and-handling-errors/

## Handling invalid input to std::cin
Refer to https://www.learncpp.com/cpp-tutorial/stdcin-and-handling-invalid-input/

## Assert and static_assert
### Preconditions, invariants, and postconditions
- In programming, a **precondition** is any condition that must be true prior to the execution of some section of code (e.g. if statements).
	- This is sometimes known as the **Bouncer Pattern**.
- An **invariant** is a condition that must be true while some section of code is executing.
	- This is often used with loops, where the loop body will only execute so long as the invariant is true.
- A **postcondition** is something that must be true after the execution of some section of code.
	- Usually this means if the result fails the conditional expression, then the program is terminated and/or an error is generated.

### Assertions
- Using a conditional statement to detect an invalid parameter (or to validate some other kind of assumption), along with printing and error message and terminating the program, is such a common method of detecting problems that C++ provides a shortcut method for doing this - an assertion.
- An assertion is an expression that will be true unless there is a bug in the program.
	- If the conditional expression in assertion evaluates to `true`, then it does nothing.
	- If `false`, then it will generate an error and terminate the program (via `std::abort`).
- The error message that an assertion displays typically contains the expression that failed as text, along with the name of the code file, and the line number of the assertion.
	- The actual message varies depending on which compiler is being used.

>[!important] Asserts are used to detect errors while developing and debugging.

- In C++, runtime assertions are implemented via the `assert` preprocessor macro, which lives in the `<cassert>` header.
- Example of an assertion:

```C++
#include <cassert> // for assert()
#include <cmath> // for std::sqrt
#include <iostream>

double calculateTimeUntilObjectHitsGround(double initialHeight, double gravity)
{
  assert(gravity > 0.0); // The object won't reach the ground unless there is positive gravity.

  if (initialHeight <= 0.0)
  {
    // The object is already on the ground. Or buried.
    return 0.0;
  }

  return std::sqrt((2.0 * initialHeight) / gravity);
}

int main()
{
  std::cout << "Took " << calculateTimeUntilObjectHitsGround(100.0, -9.8) << " second(s)\n";

  return 0;
}
```

- In the code above, the function `calculateTimeUntilObjectHitsGround()` executes only when `gravity` is higher than `0`, otherwise the program will terminate. This is essentially the same as `if (gravity > 0.0) std::abort();`.

>[!important] Make assert expressions descriptive.
>A simple conditional expression like `found`, or `someVar > 42` isn't very descriptive, maybe even misleading. It's best practice to make assert expressions descriptive so that it's clear what it is that has gone wrong.
>
>A simple trick to make an assert statement more descriptive is to use `&&` and a string literal. For example, `assert(found && "this value does not exist in database";` is a descriptive assert statement that will only be printed out if `found` is `false`; meaning, the string literal will be shown in the error message when the assert statement is triggered.

### Asserts vs. error handling
- The goal of an assertion is to catch programming errors by documenting something that should never happen.
	- If that thing does happen, then the programmer made an error somewhere, and that error can be identified and fixed.
	- Assertions do not allow recovery from errors.
- Error handling is designed to gracefully handle cases that could happen in release configurations. These may or may not be recoverable, but one should always assume a user of the program may encounter them.
- Assertions are also sometimes used to document cases that were not implemented because they were not needed at the time the programmer wrote the code:

```C++
assert(moved && "Need to handle case where student was just moved to another classroom");
```

### NDEBUG
- The `assert` macro comes with a small performance cost that is incurred each time the assert condition is checked.
- Ideally, asserts should never be encountered in production code, considering the code should already be thoroughly tested.
- Consequently, many devs prefer that asserts are only active in debug builds.
- C++ comes with a way to turn off asserts in production code - if the macro `NDEBUG` is defined, the assert macro gets disabled.
- Some IDEs set `NDEBUG` by default as part of the project settings for release configurations.

### Assert limitations and warnings
- The assert itself can be improperly written. If this happens, the assert will either report an error where none exists, or fail to report a bug where on does exist.
- The assert should have no side effects - otherwise release configuration will not be the same as the debug configuration.
- The assert should be used only in cases where data corruption isn't likely to occur if the program terminates unexpectedly.

### static_assert
- A `static_assert` is an assertion that is checked at compile-time which causes a compile error if triggered.
	- `static_assert` is a keyword, so a header is not required.
- A `static_assert` takes the following form: `static_assert(condition, diagnostic_message)`
- If the condition in `static_assert` is not true, then the diagnostic message is printed. For example:

```C++
static_assert(sizeof(long) == 8, "long must be 8 bytes");
static_assert(sizeof(int) >= 4, "int must be at least 4 bytes");

int main()
{
	return 0;
}
```

- The code above uses `static_assert` to ensure that types have a certain size, otherwise it'd fail the compilation.
- Because `static_assert` is evaluated at compile-time, the condition must be a constant expression.
- `static_assert` can be placed anywhere, including the global namespace.
- `static_assert` is NOT deactivated in release builds.
- In C++17 and above, diagnostic message is optional.

## Implicit type conversion
- Refer to [[#Intro to implicit type conversion]]
- The process of producing a new value of some type from a value of a different type is called a **type conversion**.
- Type conversion can be invoked in one of two ways:
	- Implicitly, meaning compiler does the conversion as needed
	- Explicitly, meaning the programmer requests the conversion
- **Implicit type conversion** (aka automatic type conversion or coercion) is performed automatically by the compiler when one data type is required, but a different data type is supplied.
	- For example, when a variable with `double` type is initialized but the initializer is an integer literal (e.g. `5`), an implicit type conversion takes in place and converts the integer to a double.
	- Another example is when a variable with `float` type is given a double literal (e.g. `5.0`), the value is converted from double to float (e.g. `5.0f`).
- Functions behave the same way as the variable; implicit type conversions occur when the return value of a function does not match the return type.
- Binary operations with mixed data types also triggers implicit type conversions.

>[!warning] When the compiler can't find an acceptable conversion, it will trigger a compile error.

>[!important]
>Brace initialization disallows implicit type conversion. For example, `int x {3.5};` triggers a compile error.

## The standard conversions
- The C++ language standard defines how different fundamental types (and in some cases, compound types) can be converted to other types. These conversion rules are called the **standard conversions**.
- The standard conversions can be broadly divided into 4 categories, each covering different types of conversions:
	- Numeric promotions
	- Numeric conversions
	- Arithmetic conversions
	- Other conversions
- When a type conversion is required, the compiler will see if there are standard conversions that it can use to convert the value to the desired type. The compiler may apply one or two standard conversions in the conversion process.

## Floating point and integral promotion
- In [[#Object sizes and the sizeof operator]], we noted that C++ has minimum size guarantees for each of the fundamental types. However, the actual size of these types can vary based on the compiler and architecture.
	- This variability was allowed so that the `int` and `double` data types could be set to the size that maximizes performance on a given architecture. For example, 32-bit computer will typically be able to process 32-bits of data at a time (in such case, `int` is likely set to 32-bits).

>[!reminder] The number of bits a data type uses is called its **width**.

- Some 32-bit processors can manipulate 8-bit or 16-bit values directly. However, doing so is often slower than manipulating 32-bit values.
	- Other 32-bit CPUs can only operate on 32-bit values, and additional tricks must be employed to manipulate narrower values.

### Numeric promotion
- C++ does not assume a given CPU would be able to efficiently manipulate values that are narrow than the natural data size for that CPU. As such is the case, C++ provides numeric promotion to deal with narrow values.
- A **numeric promotion** is the type conversion of certain narrow numeric types (e.g. `char`) to certain wider numeric types (e.g. `int` or `double`) that can be processed efficiently.
- All numeric promotions are **value-preserving conversion** (aka safe conversion), which means that it guarantees that the source value is converted into an equal value of the destination type without any loss or modification.
- Because promotions are safe, the compiler will freely use numeric promotion as needed, and will not issue a warning when doing so.

>[!important] Numeric promotion reduces redundancy.
>Numeric promotion reduces the need to define a different function (that behaves the same way) for each type that a parameter can take; thereby reducing the redundancy in code. For example, a function with an `int` type parameter can take an `int` type argument as well as `double` type argument.

- The numeric promotion rules are divided into two subcategories: integral promotions and floating point promotions.

### Floating point promotions
- Floating point promotion allows a value of type `float` to be converted to a value of type `double`.
	- As such, a function with a parameter of type `double` accepts not only an argument of `double` type, but also a `float` type.

### Integral promotions
- Integral promotion allows a few things:
	- `signed char` or `signed short` can be converted to `int`
	- `unsigned char`, `char8_t`, and `unsigned short` can be converted to `unsigned int`. They can also be converted to `int` if `int` can hold the entire range of the type.
	- If `char` is signed by default, it follows the signed char conversion rules as stated above. If it is unsigned by default, it follows the unsigned char conversion rules.
	- `bool` can be converted to `int`, with `false` as `0` and `true` as `1`.
- Assuming a byte is equivalent to 8-bit and `int` has the width of 4 bytes or larger (typical), the above basically means that `bool`, `char`, `signed char`, `unsigned char`, `signed short`, and `unsigned short` all get promoted to `int`.
	- This means that a function with an `int` type parameter is able to take arguments of various types (that are convertible).
- There are a few other integral promotion rules that are used less often; refer to https://en.cppreference.com/w/cpp/language/implicit_conversion#Integral_promotion

>[!warning] While integral promotion is value-preserving, it does not necessarily preserve the signedness.

## Numeric conversions
- Some widening type conversions (such as `char` to `short`, or `int` to `long`) are not considered to be numeric promotions because such conversions do not assist in the goal of converting smaller types to larger types that can be processed more efficiently.
- C++ supports another category of numeric type conversions, called numeric conversions, which covers additional type conversions between fundamental types.
	- The distinction between numeric promotion and numeric conversion is mostly academic. However, in certain cases, the compiler will favor promotions over conversions.
- There are five basic types of numeric conversions:
	- Integral type to any other integral type (excluding integral promotions), such as `int` to `short`, `int` to `long`, `short` to `chaf`, and `int` to `unsigned int`.
	- Floating point type to any other floating point type (excluding floating point promotions), such as `double` to `float`, and `double` to `long double`.
	- Floating point type to any integral type
	- Integral type to any floating point type
	- Integral type/floating point type to a bool

### Safe and unsafe conversions
- Unlike numeric promotions (which are always value-preserving, meaning "safe"), many numeric conversions are unsafe; at least one value of the source type cannot be converted into an equal value of the destination type.
- Numeric conversions fall into three general safety categories:
	- **Value-preserving conversions** : safe numeric conversions where the destination type can exactly represent all possible values in the source type (e.g. `int` to `long`).
	- **Reinterpretive conversions** : unsafe numeric conversions where the converted value may be different than the source value, but no data is lost (e.g. `signed`/`unsigned` conversions).
	- **Lossy conversions** : unsafe numeric conversions where data may be lost during the conversion (e.g. `double` to `int`).
- In the case of reinterpretive conversions, converting from a negative `signed int` to an `unsigned int` is considered unsafe due to the fact that the `unsigned int` cannot represent the negative numbers (which means the value is not preserved).
	- Converting from a positive `signed int` to an `unsigned int` is value-preserving, thus safe.
- In the case of lossy conversions, converting from `double` to `float` can result in data loss, due to the fact that precision is lost (the number of significant digits differ between these two types).

>[!warning] Some conversions may fall into different categories depending on the platform.

>[!important] In all cases, converting a value into a type whose range doesn't support that value is unsafe.

## Narrowing conversions, brace initialization, and constexpr initializers

### Narrowing conversions
- A narrowing conversion is a type of conversion where a value of a source type is converted to a value of a destination type whose width is "narrower" than the source type.
	- It is a potentially unsafe numeric conversion where the destination type may not be able to hold all the values of the source type.
- Narrowing conversions include:
	- Converting from a floating point type to an integral type
	- Converting from a floating point type to a narrower floating point type (outside the range or loss of precision)
	- Converting from an integral type to a floating point type
	- Converting from an integral type to a narrower integral type (outside the range or loss of signage)

>[!warning] Narrowing conversions should always be avoided.

### Explicit narrowing conversions using static_cast
- Though narrowing conversions should always be avoided, it is sometimes not avoidable.
	- This is particularly the case when the function parameter and argument may have mismatched types.
- In such cases, it is best to use `static_cast` to explicitly apply narrowing conversion.
- For example:

```C++
void someFcn(int i)
{
}

int main()
{
    double d{ 5.0 };

    someFcn(d); // bad: implicit narrowing conversion will generate compiler warning

    // good: we're explicitly telling the compiler this narrowing conversion is intentional
    someFcn(static_cast<int>(d)); // no warning generated

    return 0;
}
```

>[!important]
>Brace initialization disallows implicit narrowing conversions (causes an error). However, explicit narrowing conversion using `static_cast` is allowed (e.g. `int x { static_cast<int>(3.5) };`).

### Constexpr narrowing conversions
- When the source value of a narrowing conversion is `constexpr`, the specific value to be converted must be known to the compiler. In such cases, the compiler can perform the conversion itself, and then check whether the value was preserved.
	- If the value was not preserved, the compiler can halt compilation with an error.
	- If the value was preserved, the conversion is NOT considered to be narrowing, therefore safe (no error).
- For example:

```C++
#include <iostream>

int main()
{
    constexpr int n1{ 5 };   // note: constexpr
    unsigned int u1 { n1 };  // OKAY: conversion is NOT narrowing

    constexpr int n2 { -5 }; // note: constexpr
    unsigned int u2 { n2 };  // compile error: conversion is narrowing

    return 0;
}
```

- Note that conversion from an integral type to another integral type is NOT considered narrowing if the original value is `constexpr`.
	- Additionally, conversion from an integral type to a floating point type is NOT considered narrowing if the original value is `constexpr`.
	- However, conversion from a floating point type to an integral type is STILL narrowing even if the original value is `constexpr`.
	- Strangely, conversion from a floating point type to a narrow floating type is NOT considered narrowing if the original value is `constexpr` - even though there is a loss of precision.

>[!important]
>Knowing which type conversions are narrowing (or not) is beneficial when dealing with brace initializations. For example,
>- `unsigned int` variable can be initialized with an `int` literal, meaning `u` suffix is not necessary.
>- `float` variable can be initialized with a `double` literal, meaning `f` suffix is not necessary.
>- `double` variable can be initialized with `constexpr int` literal without the use of `static_cast`.

>[!important]
>Floating point types are ranked in this order (greater to lesser):
>- `long double`
>- `double`
>- `float`

## Arithmetic conversions
- Certain operators require that their operands be of the same type. If one of these operators is invoked with operands of different types, one or both of the operands will be implicitly converted to matching types using a set of rules called the **usual arithmetic conversions**.
- The operators that require operators that require operands of the same type are:
	- The binary arithmetic operators (`+`, `-`, `*`, `/`, `%`)
	- The binary relational operators (`<`, `>`, `<=`, `>=`, `==`, `!=`)
	- The binary bitwise arithmetic operators (`&`, `^`, `|`)
	- The conditional operator `?:` (excluding the condition itself)

### The usual arithmetic conversion rules
- The usual arithmetic conversion rules are somewhat complex. The compiler has a ranked list of types that look something like this (highest to lowest):
	- `long double`
	- `double`
	- `float`
	- `long long`
	- `long`
	- `int`
- If one operand is an integral type and the other a floating point type, the integral operand is converted to the type of the floating point operand (no integral promotion takes place).
	- Otherwise, Any integral operands are numerically promoted.
- If one operand is `signed` and the other `unsigned`, special rules apply:
	- If the rank of the `unsigned` operand is greater than the rank of the `signed` operand, then the `signed` operand is converted to the type of the `unsigned` operand.
	- If the type of the `signed` operand can represent all the values of the type of the `unsigned` operand, the type of the `unsigned` operand is converted to the type of the `signed` operand.
	- Otherwise both operands are converted to the corresponding `unsigned` type of the `signed` operand.

>[!important]
>The full rules for the usual arithmetic conversions is here : https://en.cppreference.com/w/cpp/language/usual_arithmetic_conversions

### Signed and unsigned issues
- The prioritization hierarchy and conversion rules can cause some problematic issues when mixing `signed` and `unsigned` values.
- If a binary arithmetic operator is used on a `signed int` and `unsigned int` values and the result is expected to be a negative value, then the actual result is undefined.
	- Due to the conversion rules, the `int` operand is converted to an `unsigned int`, so the result is `unsigned int`, which does not support a negative value.
- If a binary relational operator is used on a `signed int` and `unsigned int` values, the result could vary.
	- `signed int` value is converted to `unsigned int`. The result of the conversion could produce a number greater than the other `unsigned int` operand.

>[!warning]
>Mixing `signed` and `unsigned` integral types can cause unexpected behaviors. This is one of the primary reasons to avoid `unsigned` integers.

## Explicit type conversion (casting) and static_cast
- **Explicit type conversion** refers to when the programmer requests the compiler to convert a value to another type.

### Type casting
- C++ provides **type casting operators** which are operators that the programmer can use to explicitly request for type conversions.
- There are 5 different types of casts:
	- C-style casts
	- Static casts
	- Const casts
	- Dynamic casts
	- Reinterpret casts
- Other than C-style casts, the rest are referred to as **named casts**.

### C-style casts
- In standard C programming, casts are done via the `()` operator, with the name of the type to convert the value placed inside the parentheses (e.g. `(int)x`). This is still used in C++.
- For example:

```C++
#include <iostream>

int main()
{
    int x { 10 };
    int y { 4 };


    double d { (double)x / y }; // convert x to a double so we get floating point division
    std::cout << d << '\n'; // prints 2.5

    return 0;
}
```

- C++ allows the C-style casts to be used more like a function-call (e.g. `double(x)`).
- Although C-style casts seem simple to use, it can actually perform a variety of different conversions depending on context; this can include a static cast, const cast, or reinterpret cast. As a result, C-style casts are at risk for being inadvertently misused and not producing the expected behavior.
	- For this reason, it's best to avoid using C-style casts.

### static_cast
- C++ provides a casting operator called `static_cast`, which can be used to convert a value of one type to another type. It is used like `static_cast<type>(value)`.
- `static_cast` was briefly covered in [[#Explicit type conversion - static_cast]].
- The main advantage of `static_cast` is that it provides compile-time type checking, making it harder to make an inadvertent error.
- `static_cast` is also (intentionally) less powerful than C-style casts, so it does not remove `const`. For example,

```C++
int main()
{
	const int x{ 5 };
	int& ref{ static_cast<int&>(x) }; // invalid: will produce compilation error
	ref = 6;

	return 0;
}
```

>[!important] `static_cast` should always be preferred where a type conversion is required.

## Typedefs and type aliases
### Type aliases
- In C++, `using` is a keyword that creates an alias for an existing data type. To create such a type alias, `using` keyword is used, followed by a nae for the type alias, followed by an equal sign and an existing data type.
	- Once defined, a type alias can be used anywhere a type is needed; same scoping rules as variable identifiers.
- For example:

```C++
using Distance = double; // define Distance as an alias for type double
Distance milesToDestination = 3.4;
```

### Naming type aliases
- Historically, there hasn't been a lot of consistency in how type aliases have been named. There are three common naming conventions:
	- Type aliases that end in a `_t` suffix (e.g. `size_t`, `nullptr_t`).
	- Type aliases that end in a `_type` suffix (e.g. `std::string::size_type`)
	- Type aliases that uses no suffix (e.g. `std::string::iterator`)
- In modern C++, the convention is to name type aliases (or any other type) with a capital letter, and using no suffix (e.g. `Distance`).
- An alias does not actually define a distinct type, meaning it merely introduces a new identifier for an existing type. There can be more than one alias for the same type, and they can be used interchangeably.
	- This can lead to semantic errors, which are not preventable by the compiler. This means that aliases are not **type safe**.

### Typedefs
- A `typedef` keyword (which is short for type definition) is an older way of creating an alias for a type.
	- It is used like `typedef oldType NewType;`.
	- For example, `typedef long Miles;` creates an alias for `long` type that is named `Miles`.
- `using` keyword is preferred over `typedef` because:
	- Syntax for `typedef` can easily be mistaken, like switching the place between the type and the new identifier.
	- Syntax for `typedef` can be hard to read (example omitted).
	- `typedef` suggests a new type being defined, which is NOT the case.

>[!important] In conventional language, the term "typedef" refers to both a `typedef` or a type alias.

### Using type aliases for platform independent coding
- One of the primary uses for type aliases is to hide platform specific details.
	- The same identifier that is used across different platforms can be a type alias for different types depending on the platform; as such, the identifier is used the same way but is implemented differently (and is hidden).
- Because `char`, `short`, `int`, and `long` gives no indication of their size, it is fairly common for cross-platform programs to use type aliases to define aliases that include the type's size in bits.
	- For example, `int8_t` would be an 8-bit signed integer, `int16_t` a 16-bit signed integer, and so on.
	- Using type aliases in this manner helps prevent mistakes and makes it more clear about what kind of assumptions have been made about the size of the variable.
- In order to make sure each aliased type resolves to a type of the right size, type aliases of this kind are typically used in conjunction with preprocessor directives. For example:

```C++
#ifdef INT_2_BYTES
using int8_t = char;
using int16_t = int;
using int32_t = long;
#else
using int8_t = char;
using int16_t = short;
using int32_t = int;
#endif
```

- In the example above, it is made so that the top set of type aliases will be used on machines where integers are only 2 bytes (once `INT_2_BYTES` is defined) and the bottom set will be used on 4 bytes integer machines.
	- The [[#Fixed-width integers and size_t|fixed-width type and size_t type]] are actually just type aliases to various fundamental types.

### Using type aliases to make complex types easier to read
- Another primary use for type aliases is to make complex types easier to read. In advanced C++, types can become complicated and lengthy, and using a type alias for that makes things easier. For example:

```C++
#include <string> // for std::string
#include <vector> // for std::vector
#include <utility> // for std::pair

using VectPairSI = std::vector<std::pair<std::string, int>>; // make VectPairSI an alias for this crazy type

bool hasDuplicates(VectPairSI pairlist) // use VectPairSI in a function parameter
{
    // some code here
    return false;
}

int main()
{
     VectPairSI pairlist; // instantiate a VectPairSI variable

     return 0;
}
```

- In the example above, `std::vector<std::pair<std::string, int>>` is a complex type (which will be covered later) that would've been a pain to type every time it's used, but instead a type alias named `VectPairSI` is used to simplify things.

### Using type aliases to document the meaning of a value
- Type aliases can also help with code documentation and comprehension.
	- This is especially the case with functions, where the function identifier describes the purpose of the function but the meaning of its return value is unclear; type alias can help with that.
- For example:

```C++
using TestScore = int;
TestScore gradeTest();
```

- In the example above, the meaning of the return value of `gradeTest()` is made clear by saying its type is `TestScore`.

>[!important]
>Usually, creating a type alias just to document the return type of a single function isn't worth it, unless there are multiple functions passing or returning such a type.

### Using type aliases for easier code maintenance
- Type aliases allow the programmer to change the underlying type of an object without having to update lots of hardcoded types.
	- For example, if a student's ID number was passed around in the program as a `short` but it needed to be changed to `long` instead, it'd be a hassle to go through the entire program to change the type of the variables and parameters. However, if a type alias was being used, only the type alias has to be changed and then the change will be applied to the entire program.
- While this little perk is nice, caution is necessary wherever a type is changed because the behavior of the program may also change; this is especially the case if the type is changed to an entirely different type family (e.g. `int` to `float`, or `signed` to `unsigned`).
	- The new type may have its own kinks that the program is not ready to deal with.
	- It's best to thoroughly test the program if a new type is in place.

### Downsides of type alias
- While type aliases offer some benefits, they also introduce yet another identifier into the code that needs to be understood.
	- If this isn't offset by some benefit to readability or comprehension, then the type alias is doing more harm than good.
- A poorly utilized type alias can take a familiar type and hide it behind a custom name that needs to be looked up. In some cases, obscuring the type information can also be harmful to understanding how the type should be expected to work.

>[!important] Type aliases should be used primarily in cases where there is a clear benefit to code readability or code maintenance.


## Type deduction for objects using the auto keyword
- This lesson is about using `auto` keyword, which is placed in the place where the data type should be when a variable is initialized; the compiler deduces the correct data type of the variable by the type of the initializer.
- Skipping most of the contents because `auto` is not recommended. Refer to https://www.learncpp.com/cpp-tutorial/type-deduction-for-objects-using-the-auto-keyword/

## Type deduction for functions
- Skipped, refer to https://www.learncpp.com/cpp-tutorial/type-deduction-for-functions/

## Intro to function overloading
- **Function overloading** allows the programmer to create multiple functions with the same name, so long as each identically named function has different parameter types.
	- Each function sharing a name (in the same scope) is called an **overloaded function**.
	- Function overloading reduces the effort to come up with a different function name for each data type.
- For example:

```C++
int add(int x, int y) // integer version
{
    return x + y;
}

double add(double x, double y) // floating point version
{
    return x + y;
}

int main()
{
	std::cout << add(1, 2);
	std::cout << '\n';
	std::cout << add(1.2, 3.4);
    return 0;
}
```

- In the example above, `add()` function is defined twice but naming conflict does not occur; and the function is able to handle either two `int` type arguments or two `double` type arguments.
- When a function call is made to a function that has been overloaded, the compiler will try to match the function call to the appropriate overload based on the arguments used in the function call; this is called **overload resolution**.
	- In the example above, `add(1, 2)` will invoke the integer version of the function, and the `add(1.2, 3.4)` will invoke the floating point version.

>[!warning]
>If an overloaded function is not differentiated, or if a function call to an overloaded function cannot be resolved to an overloaded function, then a compile error will result.

## Function overload differentiation
- Overloaded functions are differentiated by ___number of parameters___ and/or ___type of parameters___.
- Example of differentiation by number of parameters:
	- `add(int, int)` is differentiated from `add(int, int, int)`
- Example of differentiation by type of parameters:
	- `add(int, int)` is differentiated from `add(double, double)`
	- `add(int, double)` is differentiated from `add(double, int)`

>[!warning] Parameter names does NOT affect differentiation.

>[!warning] Return type does NOT affect differentiation.

>[!warning] Type alias or typedef does NOT affect differentiation.

>[!warning] `const` qualifier does NOT affect differentiation.

- A function's **type signature** is defined as the parts of the function header that are used for differentiation of the function; this includes the function name, number of parameters, parameter type, and function-level qualifiers.
	- It notably does NOT include the return type.

## Function overload resolution and ambiguous matches
- The process of matching function calls to a specific overload function is called overload resolution.
- Overload resolution is straightforward and simple when the types of the arguments match the types of the parameters exactly.
- Overload resolution becomes complex when the types of the arguments does NOT match the types of the parameters (and thus type conversions occur).
	- For example, if `print(int x)` and `print(double x)` is defined and a function call with a `float` argument like `print(5.5f)` occurs, the overload resolution goes through complex steps to figure out the best match.

### Resolving overloaded function calls
- When a function call is made to an overloaded function, the compiler steps through a sequence of rules to determine which (if any) of the overloaded functions is the best match.
- At each step, the compiler applies a bunch of different type conversions to the argument(s) in the function call.
	- For each conversion applied, the compiler checks if any of the overloaded functions are now a match.
	- After all the different type conversions have been applied and checked, the step is done.
- The result at each step will be one of three possible outcomes:
	- No matching functions found; the compiler moves on to the next step in the sequence.
	- A single matching function found (the best match); No more steps.
	- More than one matching function found; the compiler issues an error.
- An **ambiguous match** occurs when the compiler finds two or more exact matches for a function call; when this occurs, the compiler will stop matching and issue a compile error stating that it has found an ambiguous function call.

### The argument matching sequence
#### Step 1
- In this step, the compiler tries to find an exact match. This happens in two phases.
- <mark class="hltr-yellow">Phase 1)</mark> the compiler will see if there is an overloaded function where the type of the arguments in the function call exactly matches the type of the parameters in the overloaded functions.
	- For example, `foo(0)` is an exact match with `foo(int)`.
- <mark class="hltr-yellow">Phase 2)</mark> the compiler will apply a number of trivial conversions to the arguments in the function call.
- The **trivial conversions** are a set of specific conversion rules that will modify types (without modifying the value) for purposes of finding a match. These include:
	- lvalue to rvalue conversions
	- qualification conversions (e.g. non-const to const)
	- non-reference to reference conversions
- For example:

```C++
void foo(const int)
{
}

void foo(const double&)
{
}

int main()
{
    int x { 1 };
    foo(x); // x trivially converted from int to const int

    double d { 2.3 };
    foo(d); // d trivially converted from double to const double&

    return 0;
}
```

- In the example above, qualification conversions occur to change `int` to `const int` and `double` to `const double&`.
- Matches made via the trivial conversions are considered exact matches.
- Ambiguous matches can occur with trivial conversions. For example:

```C++
void foo(int)
{
}

void foo(const int&)
{
}

int main()
{
    int x { 1 };
    foo(x); // ambiguous match with foo(int) and foo(const int&)

    return 0;
}
```

- In the example above, `foo(int)` and `foo(const int&)` are both considered exact matches.

#### Step 2
- If exact match is NOT found, the compiler tries to find a match by applying numeric promotion to the argument(s).
	- Certain narrow integral and floating point types can be automatically promoted to wider types, as discussed in [[#Floating point and integral promotion]].
	- If a match is found after numeric promotion, the function call is resolved.
- For example:

```C++
void foo(int)
{
}

void foo(double)
{
}

int main()
{
    foo('a');  // promoted to match foo(int)
    foo(true); // promoted to match foo(int)
    foo(4.5f); // promoted to match foo(double)

    return 0;
}
```

- In the example above, exact match for `foo(char)` could not be found (in step 1), so the compiler promotes the `char` argument to an `int` - which then matches with `foo(int)`. Similarly, `bool` is promoted to `int` then matched with `foo(int)`, just as `float` is promoted to `double` and matched with `foo(double)`.

#### Step 3
- If a match is not found even after numeric promotion, the compiler tries to find a match by applying numeric conversions to the arguments.
	- Refer to [[#Numeric conversions]]
- For example:

```C++
#include <string> // for std::string

void foo(double)
{
}

void foo(std::string)
{
}

int main()
{
    foo('a'); // 'a' converted to match foo(double)

    return 0;
}
```

- In the example above, `foo(char)` does not have an exact match, nor does it have a promotion match (`foo(int)`), and so `char` is numerically converted to a `double` - thus matching with `foo(double)`.

>[!important] Matches made by numeric promotion takes precedence over any matches made by numeric conversions.

#### Step 4
- If a match is NOT found by numeric conversion, the compiler tries to find a match through any user-defined conversions.
	- #todo User-defined conversions not yet covered.

#### Step 5
- If a match is NOT found by user-defined conversion, the compiler will look for a matching function that uses ellipsis.
	- #todo ellipsis not yet covered.

#### Step 6
- If a match is NOT found by this point, the compiler gives up and issues a compile error.

### Examples of ambiguous match
#### Long to int or double

```C++
void foo(int)
{
}

void foo(double)
{
}

int main()
{
    foo(5L); // 5L is type long

    return 0;
}
```

- In the example above, `foo(long)` does not have an exact match. `long` cannot be numerically promoted, and thus the compiler moves onto numeric conversions - where it finds two potential matches. `long` can be numerically converted into either an `int` or `double`; since two possible matches are found, the function call is considered ambiguous.

#### signed int to unsigned int or float

```C++
void foo(unsigned int)
{
}

void foo(float)
{
}

int main()
{
    foo(0);
    return 0;
}
```

- In the example above, `signed int` can be numerically converted to either an `unsigned int` or `float`.

#### double to unsigned int or float

```C++
void foo(unsigned int)
{
}

void foo(float)
{
}

int main()
{
    foo(3.14159);

    return 0;
}
```

- In the example above, `double` can be numerically converted to either an `unsigned int` or `float`.

### Resolving ambiguous matches
- There are a few ways to resolve ambiguous matches:
	- Define a new overloaded function to match the type of the arguments.
	- Explicitly cast the arguments to match one of the overloaded functions.

### Matching for functions with multiple arguments
- If there are multiple arguments, the compiler applies the matching rules to each argument in turn.
	- The function chosen must provide a better match than all the other candidate functions for at least one parameter.
- For example:

```C++
#include <iostream>

void print(char, int)
{
	std::cout << 'a' << '\n';
}

void print(char, double)
{
	std::cout << 'b' << '\n';
}

void print(char, float)
{
	std::cout << 'c' << '\n';
}

int main()
{
	print('x', 'a');

	return 0;
}
```

- In the example above, the matching function to `print(char, char)` is `print(char, int)`, as `char` is numerically promoted to `int`.

### (note) overloaded functions and string literal
- Note that the function call with string literal exactly matches with `const char*` first. If `const char*` is not available but `string_view` is, then it will match with `string_view`.
	- If there is `string_view` and `char`, then it will match with `string_view`.
- For example:

```C++
#include <iostream>
#include <string_view>

void print(std::string_view s)
{
    std::cout << "string_view" << std::endl;
    std::cout << s << '\n';
}

void print(const char* s)
{
    std::cout << "const char*" << std::endl;
    std::cout << s << '\n';
}

int main()
{
    print("Hello, world");

    return 0;
}
```

```console
const char*
Hello, world
```


## Deleting functions
- It's possible to prevent a function call with arguments that doesn't exactly match (without promotion or conversion) from being executed by deleting a function with `= delete` specifier.
- For example:

```C++
#include <iostream>

void printInt(int x)
{
    std::cout << x << '\n';
}

void printInt(char) = delete; // calls to this function will halt compilation
void printInt(bool) = delete; // calls to this function will halt compilation

int main()
{
    printInt(97);   // okay

    printInt('a');  // compile error: function deleted
    printInt(true); // compile error: function deleted

    printInt(5.0);  // compile error: ambiguous match

    return 0;
}
```

- In the example above, `printInt(char)` and `printInt(bool)` is deleted and causes compilation errors.

>[!warning] Deleted functions are candidates in function overload resolution, so these can cause ambiguous matches.

>[!important] `= delete` means "I forbid this", not "this doesn't exist".

### Deleting all non-matching overloads
- #todo This part makes more sense with Templates, so should be revisited later.
- Refer to https://www.learncpp.com/cpp-tutorial/deleting-functions/

## Default arguments
- A default argument is a default value provided for a function parameter.
- For example:

```C++
void print(int x, int y=10) // 10 is the default argument
{
    std::cout << "x: " << x << '\n';
    std::cout << "y: " << y << '\n';
}
```

- When calling a function that has a default argument, the caller can optionally provide an argument for any function parameter that has a default argument.
	- If an argument is provided, then that value is used. If not, the default argument value is used.
- For example:

```C++
#include <iostream>

void print(int x, int y=4) // 4 is the default argument
{
    std::cout << "x: " << x << '\n';
    std::cout << "y: " << y << '\n';
}

int main()
{
    print(1, 2); // y will use user-supplied argument 2
    print(3); // y will use default argument 4, as if we had called print(3, 4)

    return 0;
}
```

```console
x: 1
y: 2
x: 3
y: 4
```

- In the example above, parameter `y` in `print()` function has a default argument of `4`. When `print(1, 2)` is called, the provided argument `2` is used for the function. When `print(3)` is called, the default argument was used.

>[!important] Default argument can be specified only by copy initialization `=`.
>Direct initialization and brace initialization does NOT work for default arguments.

### Multiple default arguments
- A function can have multiple parameters with default arguments.
- For example:

```C++
#include <iostream>

void print(int x=10, int y=20, int z=30)
{
    std::cout << "Values: " << x << " " << y << " " << z << '\n';
}

int main()
{
    print(1, 2, 3); // all explicit arguments
    print(1, 2); // rightmost argument defaulted
    print(1); // two rightmost arguments defaulted
    print(); // all arguments defaulted

    return 0;
}
```

- Note that the arguments can only be defaulted consecutively from the rightmost parameter.
- C++ does not (as of C++23) support a function call where argument is defaulted for select parameters (e.g. `print(,,5)`). This has three major consequences:
	- In a function call, any explicitly provided arguments must be the leftmost arguments (arguments with defaults cannot be skipped).
	- If a parameter is given a default argument, all subsequent parameters (to the right) must also be given default arguments.
	- If more than one parameter has a default argument, the leftmost parameter should be the one most likely to be explicitly set by the user.

### Default arguments cannot be redeclared
- Once declared, a default argument can NOT be declared again in the same translation unit. This is to prevent ambiguity when a default argument is declared in multiple places with different values.
- For a function with a forward declaration and a function definition, the default argument must be declared in the forward declaration.
- For example:

foo.h
```C++
#ifndef FOO_H
#define FOO_H
void print(int x, int y=4);
#endif
```

main.cpp
```C++
#include "foo.h"
#include <iostream>

void print(int x, int y)
{
    std::cout << "x: " << x << '\n';
    std::cout << "y: " << y << '\n';
}

int main()
{
    print(5);

    return 0;
}
```

```console
x: 5
y: 4
```

### Default arguments and function overloading
- Functions with default arguments may be overloaded. For example:

```C++
#include <iostream>
#include <string_view>

void print(std::string_view s)
{
    std::cout << s << '\n';
}

void print(char c = ' ')
{
    std::cout << c << '\n';
}

int main()
{
    print("Hello, world"); // resolves to print(std::string_view)
    print('a');            // resolves to print(char)
    print();               // resolves to print(char)

    return 0;
}
```

- In the example above, the function call `print()` resolved to `print(char)` with the default argument.

### Default arguments and ambiguity
- Default arguments can cause a function call to overloaded function ambiguous.
- For example, if there happened to be multiple overloaded functions that has same number of default arguments (e.g. `print(int x = 5)` and `print(char x = 'a')`), a function call using default arguments (e.g. `print()`) becomes ambiguous - leading to a compile error.
	- For example, if there are two overloaded functions like `print(int x = 5)` and `print(char x = 'a')` and there's a function call like `print()`, the function call is considered ambiguous and causes a compile error.
	- Similarly, `print(int x, int y = 10)` and `print(int x, double y = 20.5)` can cause ambiguity if there is a function call like `print(1)`.

## Template system
- In C++, the **template system** was designed to simplify the process of creating functions (or classes) that are able to work with different data types.
- A **template** describes what a function or class looks like. Unlike a normal definition (where all types must be specified), one or more placeholder types can be used inside a template.
	- A **placeholder type** represents some type that is not known at the time the template is written, but that will be provided later.
- Using a template is a good way to avoid writing redundant overloaded functions just to have a function for each data type.

### Function templates
- A **function template** is a function-like definition that is used to generate one or more overloaded functions, each with a different set of actual types.
- In function template, placeholder types (aka type template parameters or template types) are used for any parameter types, return types, or types used in the function body that will be specified later.
- C++ supports 3 different kinds of template parameters:
	- **Type template parameters**
	- **Non-type template parameters** (e.g. a constexpr value)
	- **Template template parameter**
- Type template parameters are by far the most common, so this lesson will focus on this for now.
- The simple form of function template looks like this:

```C++
template <typename T>
T someFunction(T x, T y)
{
	// function body
}
```

- In the example above, `template <typename T>` is a **template parameter declaration**, where `T` is the type template parameter that is a placeholder for any type. It is placed above the function where `T` is being used as a type for the parameters.
	- Template parameters are specified inside angled brackets `<>`.
	- For each template parameter, the `typename` or `class` keyword is used, followed by the name of the type template parameter (e.g. `T`).

>[!important] There's no difference between the `typename` and `class` keywords in template parameter declarations.

### Creating a templated max function
- Here we convert a simple function that finds a max value between two numbers into a function template.
- Here's the function before templating:

```C++
int max(int x, int y)
{
	return (x < y) ? y : x;
}
```

- In order to cover various data types, `max()` function would have to be overloaded multiple times. Instead, a template function will do the job just fine:

```C++
template <typename T>
T max(T x, T y)
{
	return (x < y) ? y : x;
}
```

### Naming template parameters
- It's conventional to use a single capital letter (starting with `T`) for template parameter name when the template parameter is used in a trivial or obvious way.
	- Especially when it's being used as a placeholder type.
- If a type template parameter has a non-obvious usage or specific requirements that must be met, there are two common conventions for such names:
	- Starting with a capital letter (e.g. `Allocator`).
	- Prefixed with a `T`, then starting with a capital letter (e.g. `TAllocator`).
- As an example, the standard library has an overload of `std::max` that is declared like this:

```C++
template< class T, class Compare >
const T& max( const T& a, const T& b, Compare comp );
```

### Function templates with non-template parameters
- It is possible to create function templates that have both template parameters and non-template parameters. The type template parameter can be matched to any type, and the non-template parameters work like the parameters of normal functions.
- For example:

```C++
// T is a type template parameter
// double is a non-template parameter
// We don't need to provide names for these parameters since they aren't used
template <typename T>
int someFcn(T, double)
{
    return 5;
}

int main()
{
    someFcn(1, 3.4); // matches someFcn(int, double)
    someFcn(1, 3.4f); // matches someFcn(int, double) -- the float is promoted to a double
    someFcn(1.2, 3.4); // matches someFcn(double, double)
    someFcn(1.2f, 3.4); // matches someFcn(float, double)
    someFcn(1.2f, 3.4f); // matches someFcn(float, double) -- the float is promoted to a double

    return 0;
}
```

## Function template instantiation
- Function templates are not actually functions; their code isn't compiled or executed directly. Instead, function templates generate functions (that are compiled and executed).
- Function template follows this syntax:
	- `foo<actual_type>(arg1, arg2);`
	- For example, `max<int>(3, 5);` for the example at [[#Creating a templated max function]]
- The actual type that is specified in the angled brackets when the function template is called is referred to as **template argument**; the specified actual type will be used in place of template type (e.g. `int` replaces `T`).
- For example:

```C++
#include <iostream>

template <typename T>
T max(T x, T y)
{
    return (x < y) ? y : x;
}

int main()
{
    std::cout << max<int>(1, 2) << '\n'

    return 0;
}
```

- The process of creating functions (with specific types) from function templates (with template types) is called **function template instantiation**.
	- When a function is instantiated due to a function call, it's called **implicit instantiation**.
	- A function that is instantiated from a template is called a **specialization**, more commonly referred to as **function instance**.
	- The template from which a specialization is produced is called a **primary template**.
- The code above can be summarized like so:
	- A special function `int max(int x, int y)` was instantiated by a function call `max<int>(1, 2)`, using the primary template `T max(T x, T y)`.
- After all the instantiations are done, this is what the compiler actually compiles using the code above:

```C++
#include <iostream>

// a declaration for our function template (we don't need the definition any more)
template <typename T>
T max(T x, T y);

template<>
int max<int>(int x, int y) // the generated function max<int>(int, int)
{
    return (x < y) ? y : x;
}

int main()
{
    std::cout << max<int>(1, 2) << '\n'; // instantiates and calls function max<int>(int, int)

    return 0;
}
```

- A function template is only instantiated the first time a function call is made in each translation unit. Further calls to the function are routed to the already instantiated function.
	- Conversely, if no function call is made to a function template, the function template won't be instantiated in that translation unit.

>[!important] Compiler doesn't try to resolve a function call to a function template like overloaded functions.
>In other words, template argument specifies the function instance that the compiler will match the function call to - even if the parameter types do not match the actual argument types given to the function call. For example, `foo<double>(1, 2)` will convert the `int` literals to `double`.

### Template argument deduction
- **Template argument deduction** allows the programmer to omit the template argument and have the compiler deduce the actual type based on the type of the argument in the function call; basically calling the template function like a normal function call.
	- For example, `max<int>(1, 2)` can instead be `max(1, 2)`.
	- The function call can also be with empty angled brackets, like `max<>(1, 2)`.
- When the function call has empty angled brackets (e.g. `max<>(1, 2)`), the compiler will only consider template functions.
- When the function call is like a normal function call (e.g. `max(1, 2)`), the compiler will prefer a non-template function over a template function.
- For example:

```C++
#include <iostream>

template <typename T>
T max(T x, T y)
{
    std::cout << "called max<int>(int, int)\n";
    return (x < y) ? y : x;
}

int max(int x, int y)
{
    std::cout << "called max(int, int)\n";
    return (x < y) ? y : x;
}

int main()
{
    std::cout << max<int>(1, 2) << '\n'; // calls max<int>(int, int)
    std::cout << max<>(1, 2) << '\n';    // deduces max<int>(int, int) (non-template functions not considered)
    std::cout << max(1, 2) << '\n';      // calls max(int, int)

    return 0;
}
```

- In the example above, `max<>(1, 2)` calls the template function `max<int>(int, int)`, while `max(1, 2)` calls the non-template function `max(int, int)`. Had the non-template function not exist, `max(1, 2)` would've called the template function `max<int>(int, int)`.

>[!important] Using the normal function call syntax is preferred when calling a template function.
>There are a few reasons for this:
>- The syntax is more concise.
>- It's rare for both non-template function and template function to exist.
>- If there exists both non-template function and template function, then it's preferred for a normal function call to call upon the non-template function.

>[!warning] Improper argument for template function will result in an error.
>Just like with any function, providing an improper type of value to a function that expects a certain type of value will result in a semantic error. Even worse, if the operations inside the function does not support the type of the argument (the type doesn't support the operation), it will result in a compile error.
>
>For example, a function that does a simple addition of two integral values (e.g. `add(int, int)`) will not compile if the function call is `add(std::string, std::string)`.

### Prevent instantiation of function templates with certain arguments
- It is possible to prevent function templates with certain arguments to be called by using `= delete` specifier on a function template specialization.
	- The `= delete` specifier was covered in [[#Deleting functions]].
- For example:

```C++
#include <iostream>
#include <string>

template <typename T>
T addOne(T x)
{
    return x + 1;
}

// Use function template specialization to tell the compiler that addOne(const char*) should emit a compilation error
// const char* will match a string literal
template <>
const char* addOne(const char* x) = delete;

int main()
{
    std::cout << addOne("Hello, world!") << '\n'; // compile error

    return 0;
}
```

- In the example above, using string literal (of type `const char*`) in a function call to template function `addOne()` was prevented.

### Function templates and default arguments for non-template parameters
- Just like normal functions, function templates can have default arguments for non-template parameters.
- For example:

```C++
#include <iostream>

template <typename T>
void print(T val, int times=1)
{
    while (times--)
    {
        std::cout << val;
    }
}

int main()
{
    print(5);      // print 5 1 time
    print('a', 3); // print 'a' 3 times

    return 0;
}
```

```console
5aaa
```

### Function templates with static local variables
- Just like with any normal functions, function templates can have static local variable inside the function body. For example:

```C++
template <typename T>
void printIDAndValue(T value)
{
    static int id{ 0 };
    std::cout << ++id << ") " << value << '\n';
}
```

- However, the main issue with using static local variable inside a function template is that not all instantiated functions share the same static local variable; in other words, instantiated function for a specific type has its own static local variable.
	- It's easy to mistake that there is one static local variable for one template function. But in fact, there is one static local variable for one instantiated function.
	- For example, `printIDAndValue(int)` has its own static local variable and `printIDAndValue(double)` has its own static local variable as well.

### Generic programming
- Because template types can be relaced with any actual type, template types are sometimes called **generic types**.
	- Because templates can be written agnostically of specific types, programming with templates is sometimes called **generic programming**.
- Whereas C++ typically has a strong focus on types and type checking, in contrast, generic programming focuses on the logic of algorithms and design of data structures without worrying so much about type information.

### Conclusion about templates
- Function templates do have a few drawbacks:
	- The code can become bloated and slow to compile because they expand with each call to a unique set of argument types.
	- Function templates tend to produce unreadable error messages that are much harder to decipher than those of regular functions.
- However, these drawbacks are fairly minor compared with the power ands safety that templates bring. A good rule of thumb is to create normal functions at first, and then convert them into function templates if the needs for an overload for different parameter types arise.

## Using function templates in multiple files
- The compiler needs to see the definition of the template function whenever it is instantiated with a specific type. If the definition is not available, the compiler will not be able to generate the necessary code.
	- This means that the definition of the template function needs to be in the same translation unit that it is called from, therefore the template function cannot be declared in another file (where the definition does not exist).
- There are two approaches to separating template definitions in order to keep the code organized: single header file, or separate implementation file.
- **Single header file** : the declaration and definition of the template function are both included in the same header file. This is the most common approach. For example:

add.h
```C++
#ifndef ADD_H
#define ADD_H

template <typename T>
T add(T a, T b) {
    return a + b;
}

#endif // ADD_H
```

main.cpp
```C++
#include "add.h" // import the function template definition
#include <iostream>

int main()
{
    std::cout << add(2, 3) << '\n';
    std::cout << add(5.4 + 6.7) << '\n';

    return 0;
}
```

- **Separate implementation file** : the declaration is in the header file, and the definition is in a separate `.tpp` file, which is included at the end of the header file. This approach can help keep the header file cleaner, but it requires careful management to ensure the `.tpp` file is included correctly. For example:

add.h
```C++
#ifndef ADD_H
#define ADD_H

template <typename T>
T add(T a, T b);

#include "add.tpp"

#endif
```

add.tpp
```C++
template <typename T>
T add(T a, T b)
{
	return a + b;
}
```

main.cpp
```C++
#include "add.h"
#include <iostream>

int main()
{
	std::cout << add(3, 4) << std::endl;
	std::cout << add(7.5, 2.8) << std::endl;
	return 0;
}
```

- While the separate implementation file `.tpp` approach can be useful for organizing larger projects, it is less common and can introduce complexity. Most developers prefer to keep template definitions in the same header file to avoid potential issues with template instantiation.
	- (Note) in visual studio, `.tpp` file is not recognized. It gives a warning about `add()` function not being defined in the header file. Everything still compiles fine without trouble though.

>[!important] Template definitions does not violate the ODR, because the instantiated functions are implicitly inline.

## Function templates with multiple template types
- Calling a template function with multiple arguments of different types will cause a compile error, specifically when call is made with deduction, the template function has only one template type parameter, and non-template function (to match the call) does not exist.
	- For example, `add(2, 3.5)` will cause an error for function template `T add(T x, T y)`.
	- Note that type conversion does not occur when performing template argument deduction (it only occurs for resolving function overloads).
- There are three ways to make a call to a function template with multiple arguments of different types:
	- Explicitly convert the argument(s) to match each other.
	- Don't use deduction (provide an explicit type template argument).
	- Define a function template with multiple template type parameters.

### Use static_cast to convert the arguments to matching types
- For example:

```C++
#include <iostream>

template <typename T>
T max(T x, T y)
{
    return (x < y) ? y : x;
}

int main()
{
    std::cout << max(static_cast<double>(2), 3.5) << '\n'; // convert our int to a double so we can call max(double, double)

    return 0;
}
```

- In the example above, the problematic `max(int, double)` call was fixed to `max(double, double)` with type conversion. Code compiles without error.

### Provide an explicit type template argument
- For example:

```C++
#include <iostream>

template <typename T>
T max(T x, T y)
{
    return (x < y) ? y : x;
}

int main()
{
    // we've explicitly specified type double, so the compiler won't use template argument deduction
    std::cout << max<double>(2, 3.5) << '\n';

    return 0;
}
```

- In the example above, the template argument is set to `double` and so the function call assumes that the both arguments to `max()` are meant to be `double`. When it's not a `double`, the argument is implicitly converted to `double`.

### Function templates with multiple template type parameters
- It is possible to define a function template with multiple template type parameters. For example:

```C++
#include <iostream>

template <typename T, typename U>
void print(T x, U y)
{
	std::cout << "x: " << x << std::endl;
	std::cout << "y: " << y << std::endl;
}

int main()
{
	print(2, 3.5);
	
	return 0;
}
```

- One little caveat is that the return type has to be `void` or `auto`, otherwise implicit type conversions can occur - which can be especially problematic when the narrowing conversion occur.
	- For example, if the function template is `T add(T x, U y)` and the function call is `add(int, double)` (with the logic of adding two numbers), then `int` will be converted to `double` for the arithmetic operation, and then the result (which is `double`) will be converted to `int` type in order to match the return type. The compiler will issue a warning about possible loss of data.

### Abbreviated function templates (C++20)
- C++20 introduces a new use of the `auto` keyword, an **abbreviated function template** : when the `auto` keyword is used as a parameter type in a normal function, the compiler will automatically convert the function into a function template with each auto parameter becoming an independent template type parameter.
- For example:

```C++
auto max(auto x, auto y)
{
    return (x < y) ? y : x;
}
```

- The example above is a shorthand for the following:

```C++
template <typename T, typename U>
auto max(T x, U y)
{
    return (x < y) ? y : x;
}
```

### Function templates may be overloaded
- For example:

```C++
#include <iostream>

// Add two values with matching types
template <typename T>
T add(T x, T y)
{
    return x + y;
}

// Add two values with non-matching types
// As of C++20 we could also use auto add(auto x, auto y)
template <typename T, typename U>
T add(T x, U y)
{
    return x + y;
}

// Add three values with any type
// As of C++20 we could also use auto add(auto x, auto y, auto z)
template <typename T, typename U, typename V>
T add(T x, U y, V z)
{
    return x + y + z;
}

int main()
{
    std::cout << add(1.2, 3.4) << '\n'; // instantiates and calls add<double>()
    std::cout << add(5.6, 7) << '\n';   // instantiates and calls add<double, int>()
    std::cout << add(8, 9, 10) << '\n'; // instantiates and calls add<int, int, int>()

    return 0;
}
```

- Note that the compiler will prefer a function template with one template type parameter over a function template with multiple template type parameters when the function call is with arguments of same type.
	- For example, `add(1.2, 3.4)` instantiates `add<T>(T, T)` instead of `add<T, U>(T, U)`.
- The rules for determining which of multiple matching function templates should be preferred are called "**partial ordering of function templates**". In short, whichever function template is more restrictive/specialized will be preferred.
	- `add<T>(T, T)` is the more restrictive function template than `add<T, U>(T, U)`.

>[!warning]
>If multiple function templates can match a call and the compiler can't determine which is more restrictive, the compiler will error with an ambiguous match.

## Non-type template parameters

>[!reminder]
>A type template parameter serves as a placeholder for an actual type that is passed in as a template argument.

- While type template parameters are by far the most common type of template parameter used, there is another kind of template parameter worth knowing about: the non-type template parameter.
- A **non-type template parameter** is a template parameter with a fixed type that serves as a placeholder for a constant value passed in as a template argument.
	- In other words, it is a template parameter that represents a constant value rather than a type.
	- It allows the dev to create templates that are parameterized by values.
- A non-type template parameter can be any of the following types:
	- An integral type
	- An enumeration type
	- `std::nullptr_t`
	- A floating point type (since C++20)
	- A pointer or reference to an object
	- A pointer or reference to a function
	- A pointer or reference to a member function
	- A literal class type (since C++20)

### Defining non-type template parameters
- Here's a simple example of a function that uses an `int` non-type template parameter:

```C++
#include <iostream>

template <int N> // declare a non-type template parameter of type int named N
void print()
{
    std::cout << N << '\n'; // use value of N here
}

int main()
{
    print<5>(); // 5 is our non-type template argument

    return 0;
}
```

- As seen in the example above, the non-type template parameter is declared as `N` of type `int`. When an integral value `5` is passed as the template argument, `N` becomes `5`.
- The instantiated function may look something like this:

```C++
template <>
void print<5>()
{
    std::cout << 5 << '\n';
}
```

### Uses of non-type template parameters
- As of C++20, function parameters cannot be `constexpr`. This is true for normal functions, `constexpr` functions, and even `consteval` functions.
	- Function parameters cannot be `constexpr` because their values are not determined until runtime. The initialization of function parameters happens when the function is called, which means their values are not known at compile time. Since `constexpr` requires that the value be known and evaluated at compile time, it is not possible to declare function parameters as `constexpr`.
	- Note that the argument can be a constant expression. Be sure not to mix up parameters and arguments.
- Non-type template parameters are particularly useful for situations where certain logic inside a function or a class has to be compiled at compile time.
- Non-type template parameters offer several advantages over normal function parameters:
	- **Compile-Time Evaluation** : non-type template parameters are evaluated at compile time, which can lead to more efficient code. This allows for optimizations that are not possible with runtime parameters.
	- **Type Safety** : Non-type template parameters enforce type safety at compile time. This ensures that only constant expressions of the correct type are used, reducing the risk of runtime errors.
	- **Code Reusability** : Templates with non-type parameters can be reused with different constant values without duplicating code. This makes the code more modular and easier to maintain.
	- **Performance** : Since non-type template parameters are resolved at compile time, they can eliminate the need for runtime checks and computations, leading to faster and more efficient code.
	- **Static Polymorphism** : Non-type template parameters enable static polymorphism, allowing different behaviors to be encoded at compile time based on the template arguments. This can lead to more optimized and specialized code.
	- **Memory Efficiency** : Non-type template parameters can help in creating fixed-size data structures, such as arrays or matrices, without the need for dynamic memory allocation. This can lead to more efficient memory usage.
- An example of Static Polymorphism using non-type template parameter:

```C++
template <typename T, bool IsDebug>
class Logger {
public:
    void log(const T& message) {
        if constexpr (IsDebug) {
            std::cout << "DEBUG: " << message << std::endl;
        } else {
            std::cout << message << std::endl;
        }
    }
};

```

- In the example above, the member function `log()` behaves a little differently, depending on how class `Logger` is instantiated with template argument for the non-type template parameter.
- The standard library provides a class template `std::bitset` which uses a non-type template parameter to specify the number of bits at compile time. For example:

```C++
#include <bitset>
std::bitset<8> bits(0b10101010);
```

- #todo looks like this section will be better understood once there is a better understanding of the classes.

>[!important]
>Non-type template parameters are used primarily when constexpr values needs to be passed to functions so that the functions can be used in contexts that require a constant expression.

### Type deduction for non-type template parameters using auto (C++17)
- As of  C++17, non-type template parameters may use `auto` to have the compiler deduce the non-type template parameter from the template argument. For example,

```C++
#include <iostream>

template <auto N> // deduce non-type template parameter from template argument
void print()
{
    std::cout << N << '\n';
}

int main()
{
    print<5>();   // N deduced as int `5`
    print<'c'>(); // N deduced as char `c`

    return 0;
}
```

- Note that the ambiguous match does not occur because the instantiated functions are `print<5>` and `print<'c'>`, as opposed to `print(int)` and `print(char)` which would've caused ambiguous matches.

## Value categories (lvalues and rvalues)

>[!reminder]
>An expression is a combination of literals, variables, operators, and function calls that can be expected to produce a singular value.

- To help determine how expressions should evaluate and where they can be used, all expressions have two properties: a **type** and a **value category**.
- The **type of an expression** is equivalent to the type of the value, object, or function that results from the evaluated expression.
- The type of an expression must be determinable at compile type. However, the value of an expression may be determined at either compile time (constexpr) or runtime (non-constexpr).
- The **value category of an expression** (or subexpression) indicates whether an expression resolves to a value, a function, or an object of some kind.
	- Prior to C++11, there were only two possible value categories : `lvalue` and `rvalue`.
	- In C++11, in order to support a new feature called **move semantics**, three additional value categories were added : `gvalue`, `prvalue`, and `xvalue`.

### Lvalue and rvalue expressions
- An **lvalue** (aka left value or locator value) is an expression that evaluates to an identifiable object or function (or bit-field).

>[!important]
>The term "identify" is used by the C++ standard, but is not well-defined. An entity (such as an object or function) that has an identity can be differentiated from other similar entities (typically by comparing the addresses of the entity).

- Entities with identities can be accessed via an identifier, reference, or pointer.
	- These typically have a lifetime longer than a single expression or statement.
- Take this example:

```C++
int main()
{
	int x = 5;
	int y = x; // x is an lvalue expression

	return 0;
}
```

- In the example above, the expression `x` is an lvalue expression as it evaluates to variable `x` (which has an identifier).
- Since the introduction of constants into the language, lvalues come in two subtypes :
	- **Modifiable lvalue** is an lvalue whose value can be modified.
	- **Non-modifiable lvalue** is an lvalue whose value can't be modified (const or constexpr).
- For example:

```C++
int main()
{
    int x{};
    const double d{};

    int y { x }; // x is a modifiable lvalue expression
    const double e { d }; // d is a non-modifiable lvalue expression

    return 0;
}
```

- An **rvalue** (aka right value) is an expression that evaluates to a value (and is not an lvalue).
	- Commonly seen rvalues include literals (except C-style string literals, which are lvalues), and the return values of functions and operators.
- Rvalues aren't identifiable (meaning they have to be used immediately), and only exist within the scope of the expression in which they are used.
- For example:

```C++
int return5()
{
    return 5;
}

int main()
{
    int x{ 5 }; // 5 is an rvalue expression
    const double d{ 1.2 }; // 1.2 is an rvalue expression

    int y { x }; // x is a modifiable lvalue expression
    const double e { d }; // d is a non-modifiable lvalue expression
    int z { return5() }; // return5() is an rvalue expression (since the result is returned by value)

    int w { x + 1 }; // x + 1 is an rvalue expression
    int q { static_cast<int>(d) }; // the result of static casting d to an int is an rvalue expression

    return 0;
}
```

>[!important]
>Refer to this [link](https://en.cppreference.com/w/cpp/language/value_category) to see full list of value categories.

### Lvalue references
- A **reference** is an alias for an existing object. Once a reference has been defined, any operation on the reference is applied to the object being referenced.
	- A reference can be used to read or modify the object being referenced.
- Modern C++ contains two types of references: lvalue references, and rvalue references.
	- lvalue reference will be discussed here, whereas rvalue references will be discussed much later.
- An lvalue reference acts as an alias for an existing lvalue (such as a variable).

>[!important]
>Prior to C++11, an lvalue reference was commonly just called a **reference** because there was only one type of reference.

- To declare an lvalue reference type, an ampersand `&` is used in the type declaration. For example, `int&` is a reference to an `int` object.
- An lvalue reference variable is a variable that acts as a reference to an lvalue (usually another variable).
- For example:

```C++
#include <iostream>

int main()
{
    int x { 5 };    // x is a normal integer variable
    int& ref { x }; // ref is an lvalue reference variable that can now be used as an alias for variable x

    std::cout << x << '\n';  // print the value of x (5)
    std::cout << ref << '\n'; // print the value of x via ref (5)

    return 0;
}
```

- In the example above, a variable called `ref` is a reference variable that can be used to read the value of variable `x`.

>[!important]
>The location of ampersand `&` does not make any difference in behavior. For example, `int& x`, `int &x`, and `int & x` behaves the same way. Which you choose is a matter of style. Modern C++ programmers tend to prefer attaching the ampersand to the type, as it makes clearer that the reference is part of the type information, not the identifier.

- As mentioned before, a reference can be used to modify the value of the object being referenced. For example:

```C++
#include <iostream>

int main()
{
    int x { 5 }; // normal integer variable
    int& ref { x }; // ref is now an alias for variable x

    std::cout << x << ref << '\n'; // print 55

    x = 6; // x now has value 6

    std::cout << x << ref << '\n'; // prints 66

    ref = 7; // the object being referenced (x) now has value 7

    std::cout << x << ref << '\n'; // prints 77

    return 0;
}
```

- In the example above, it can be seen that modifying the value of `ref` also modifies the value of `x`. In a sense, `ref` is an alias for `x`.

>[!warning] All references must be initialized.
>Simply declaring a reference variable without an initializer produces an error.

- References are initialized using a form of initialization called **reference initialization**.
	- When a reference is initialized with an object (or function), it is said to be **bound** to that object (or function).
	- The process by which such a reference is bound is called **reference binding**.
	- The object (or function) being referenced is sometimes called the **referent**.

>[!warning] Lvalue references must be bound to a *modifiable* lvalue.
>Reference initialization to a constant value (meaning non-modifiable) causes an error. For this reason, lvalue references are occasionally caled **lvalue references to non-const**, or **non-const reference**.

>[!warning] Once initialized, a reference cannot be *reseated*, meaning it cannot be changed to reference another object.
>Assigning a variable to an already initialized reference only changes the value of the object it is referencing.

>[!warning] References and referents have independent lifetimes.
>A reference can be destroyed before the object it is referencing - which does not affect the referent. However, if the referent is destroyed before the reference, the reference is left referencing an object that no longer exists; meaning it becomes a **dangling reference** which produces undefined behavior.

- References are not objects. A reference is not required to exist or occupy storage. If possible, the compiler will optimize references away by replacing all occurrences of a reference with the referent.
	- However, this isn't always possible. In such cases, references may require storage.
	- This means that the term "reference variable" is a bit of a misnomer, as variables are objects with a name, and references aren't objects.
- Because references aren't objects, they can't be used anywhere an object is required.
	- For example, a reference cannot reference another reference. Even if a reference was initialized with another reference, it would end up referencing the referent that the initializer was bound to.

### Lvalue reference to const
- While normal lvalue reference cannot be bound to a constant value, a `const` reference can. For example:

```C++
int main()
{
    const int x { 5 };    // x is a non-modifiable lvalue
    const int& ref { x }; // okay: ref is a an lvalue reference to a const value

    return 0;
}
```

- An lvalue reference that is bound to a constant value is called an **lvalue reference to a const value** (reference to const, or const reference).
- A const reference can only access the value; they cannot modify it.
- A const reference to a modifiable lvalue (non-const value) is possible. In such a case, the referent is treated as `const` when accessed through the reference.
	- The underlying object remains non-const.
- For example:

```C++
#include <iostream>

int main()
{
    int x { 5 };          // x is a modifiable lvalue
    const int& ref { x }; // okay: we can bind a const reference to a modifiable lvalue

    std::cout << ref << '\n'; // okay: we can access the object through our const reference
    ref = 7;                  // error: we can not modify an object through a const reference

    x = 6;                // okay: x is a modifiable lvalue, we can still modify it through the original identifier

    return 0;
}
```

>[!warning] It's best to avoid using const reference to a non-const value unless it is truly necessary.

>[!important] A const reference can be initialized with an rvalue (e.g. `int& ref = 5;`).
>In such a case, a temporary object is created, to which the const reference is bound to.
>
>The lifetime of the temporary object is extended to match the lifetime of the reference. However, the temporaries returned from a function are not eligible for lifetime extension.

- A const reference can be initialized with a value of a different type, as long as the value can be implicitly converted to the reference type. For example:

```C++
#include <iostream>

int main()
{
    // case 1
    const double& r1 { 5 };  // temporary double initialized with value 5, r1 binds to temporary

    std::cout << r1 << '\n'; // prints 5

    // case 2
    char c { 'a' };
    const int& r2 { c };     // temporary int initialized with value 'a', r2 binds to temporary

    std::cout << r2 << '\n'; // prints 97 (since r2 is a reference to int)

    return 0;
}
```

>[!important]
>When a const lvalue reference binds to a value of a different type, the compiler will create a temporary object of the same type as the reference, initialize it using the value, and then bind the reference to the temporary.
>
>For example, when `char c = 'a';` and `const int& r2 = c;`, `r2` does not reference `c`, but instead references to a temporary object holding the value `97` which is an `int` equivalent to `char` value of `'a'`.

### Constexpr lvalue references (optional)
- When `constexpr` is applied to a reference, it allows the reference to be used in a constant expression.
- Constexpr references can only be bound to objects with static duration (either globals or static locals).
	- This is because the compiler knows where static objects will be instantiated in memory, so it can treat that address as a compile-time constant.
- A constexpr reference cannot bind to a non-static local variable.
	- This is because the address of local variables is not known until the function they are defined within is actually called.
- For example:

```C++
int g_x { 5 };

int main()
{
    [[maybe_unused]] constexpr int& ref1 { g_x }; // ok, can bind to global

    static int s_x { 6 };
    [[maybe_unused]] constexpr int& ref2 { s_x }; // ok, can bind to static local

    int x { 6 };
    [[maybe_unused]] constexpr int& ref3 { x }; // compile error: can't bind to non-static object

    return 0;
}
```

- When defining a constexpr reference to a const variable, both `constexpr` and `const` needs to be applied. For example:

```C++
int main()
{
    static const int s_x { 6 }; // a const int
    [[maybe_unused]] constexpr const int& ref2 { s_x }; // needs both constexpr and const

    return 0;
}
```

>[!warning] Constexpr references aren't typically used.

### Pass by lvalue reference

>[!reminder]
>**Pass-by-value** is a method of passing arguments to a function where the function receives a copy of the variable's value.

- Problem with pass-by-value is that some objects (e.g. a class type) can be expensive to copy.
	- `std::string` is a class type which is expensive to copy.
- Pass-by-reference is a method of passing arguments to a function where the function receives a reference to the original variable, rather than a copy of the variable's value. This allows the function to modify the original variable directly.
	- When using a pass-by-reference, a function parameter is declared as a reference type using ampersand `&` (e.g. `std::string& param`).
	- The reference acts as an alias for the argument.
- For example:

```C++
#include <iostream>
using namespace std;

void increment(int &num) {
    num++; // This modifies the original variable
}

int main() {
    int value = 5;
    increment(value);
    cout << "Value after increment: " << value << endl; // Output will be 6
    return 0;
}
```

>[!warning] Pass-by-reference only works with arguments that are modifiable lvalues (non-const variable).

### Pass by const lvalue reference
- As mentioned in [[#Lvalue reference to const]], a reference to const can bind to modifiable lvalues, non-modifiable lvalues, and rvalues. Therefore, if a parameter is a const reference, then it will be able to bind to any type of argument, including a const type.
- For example:

```C++
#include <iostream>

void printRef(const int& y) // y is a const reference
{
    std::cout << y << '\n';
}

int main()
{
    int x { 5 };
    printRef(x);   // ok: x is a modifiable lvalue, y binds to x

    const int z { 5 };
    printRef(z);   // ok: z is a non-modifiable lvalue, y binds to z

    printRef(5);   // ok: 5 is rvalue literal, y binds to temporary int object

    return 0;
}
```

- Pass-by-const-reference offers the same primary benefit as pass-by-reference (avoiding a copy of the argument) while also guaranteeing that the function can NOT change the value being referenced.

>[!important] Favor pass-by-const-reference over pass-by-reference unless there is a specific reason to do otherwise (e.g. function needs to change the value of an argument).

- As mentioned in [[#Lvalue reference to const]], a const lvalue reference can bind to a value of a different type as long as that value is convertible to the type of the reference.
	- The primary motivation for allowing this is so that a value can be passed as an argument to either a value parameter or a const reference parameter in exactly the same way.
- For example:

```C++
#include <iostream>

void printVal(double d)
{
    std::cout << d << '\n';
}

void printRef(const double& d)
{
    std::cout << d << '\n';
}

int main()
{
    printVal(5); // 5 converted to temporary double, copied to parameter d
    printRef(5); // 5 converted to temporary double, bound to parameter d

    return 0;
}
```

>[!important]
>As a rule of thumb, pass fundamental types by value, and class (or struct) types by const reference.
>
>Other common types to pass by value: enumerated types and `std::string_view`.
>Other common types to pass by (const) reference: `std::string`, `std::array`, and `std::vector`.

### Pass-by-value vs. pass-by-reference
- The cost of copying an object is generally proportional to two things:
	- The size of the object; objects that use more memory take more time to copy.
	- Any additional setup costs; some class types do additional setup when they are instantiated, which also means these setup costs must be paid each time an object is copied.
- Accessing an object through a reference is slightly more expensive than accessing an object through a normal variable identifier.
	- With a variable identifier, the running program can just go to the memory address assigned to that variable and access the value directly.
	- With a reference, there usually is an extra step; the program must first access the reference to determine which object is being referenced, and only then can it go to that memory address for that object and access the value.
	- Sometimes the compiler can optimize code using objects passed by value more highly than code using objects passed by reference. This means code generated to access objects passed by reference is typically slower than the code generated for objects passed by value.

>[!important]
>Favor pass-by-value when objects are cheap to copy (the cost of copying is similar to the cost of binding).
>
>Conversely, favor pass-by-reference when objects are expensive to copy (the cost of copying is well above the cost of binding).

>[!important]
>There isn't an exact standard that states what "cheap to copy" is, but a good rule of thumb is to consider an object to be cheap if it is smaller than 3 memory addresses (e.g. `sizeof(obj) < 3 * sizeof(void*)`).

### std::string_view vs. const std::string&
- Generally speaking, `std::string_view` is cheaper (than `std::string`) to access the value of a `std::string` object, which also means that it is cheaper to copy using `std::string_view`.
- However, there is a choice of using a reference (e.g. `const std::string&`), which is a way to directly access the value of `std::string` object. This is useful in two cases:
	- In C++14 or older, `std::string_view` is not available.
	- The operation inside a function requires specifically a `std::string` object or C-style string (`std::string_view` does not efficiently convert back to `std::string`).
- Other than the specific cases above, `std::string_view` (as a parameter) is more efficient than `const std::string&`. Consider three different arguments `std::string`, `std::string_view`, and `C-style string/literal`:
	- With `std::string` as an argument, `std::string_view` parameter makes an inexpensive conversion. A `const std::string&` parameter makes an inexpensive reference binding. Either way is good.
	- With `std::string_view` as an argument, `std::string_view` parameter makes an inexpensive copy, whereas `const std::string&` parameter requires an expensive explicit conversion. `std::string_view` parameter is better in this case.
	- With `C-style string/literal` as an argument, `std::string_view` parameter makes an inexpensive conversion, whereas `const std::string&` parameter makes an expensive conversion. `std::string_view` parameter is better in this case.

>[!important]
>`std::string_view` as a parameter works well will arguments of different types - `std::string`, `std::string_view`, and `C-style string/literal`.

## Introduction to pointers
### Pointers
- Although the memory address of a variable isn't exposed by default, the access to this information is available; the **address-of operator** `&` returns the memory address of its operand.
	- For example, `&x` returns the memory address of `x`.
- Memory addresses are typically printed as hexadecimal values, often without the `0x` prefix.
- For objects that use more than one byte of memory, address-of will return the memory address of the first byte used by the object.

>[!important]
>The `&` symbol tends to cause confusion because it has different meanings depending on context:
>- When following a type name, `&` denotes an lvalue reference (e.g. `int& ref`).
>- When used in a unary context in an expression, `&` is the address-of operator (e.g. `&x`).
>- When used in a binary context in an expression, `&` is the Bitwise AND operator (e.g. `x & y`).

- The most useful thing that can be done with an address is to access the value stored at that address; the **dereference operator** `*` returns the value at a given memory address as an lvalue. For example:

```C++
#include <iostream>

int main()
{
    int x{ 5 };
    std::cout << x << '\n';  // print the value of variable x
    std::cout << &x << '\n'; // print the memory address of variable x

    std::cout << *(&x) << '\n'; // print the value at the memory address of variable x (parentheses not required, but make it easier to read)

    return 0;
}
```

- A **pointer** is an object that holds a memory address (typically of another variable) as its value.
	- A pointer type is declared using an asterisk `*`, placed between the type name and the variable identifier. For example, `int* x` or `int *x`. The placement is a matter of preference (though this guide suggests next to the type name).
	- A pointer is said to be **pointing** at an object if it holds the address of that object. The object that a pointer is pointing to is often referred to as the **pointee**.

>[!warning]
>In modern C++, the pointers that are discussed in this chapter is sometimes called "raw pointers" or "dumb pointers", in order to differentiate them from "smart pointers" which was introduced into the C++ language more recently (thus covered much later in this guide).

>[!warning]
>When declaring multiple variables on a single line (which should be generally avoided), the asterisk has to be included with each variable. For example, `int* ptr1, * ptr2;`.

### Pointer initialization
- A pointer that has not been initialized (e.g. `int* x;`) is sometimes called a **wild pointer**.
	- Wile pointers contain a garbage address, and dereferencing a wild pointer will result in undefined behavior. Because of this, a pointer should always be initialized to a known value.
- Since pointers hold addresses, when a pointer is assigned/initialized with a value, that value has to be an address.
	- Reminder that the address-of operator `&` can be used to get an address of a value (e.g. `&x`).
- Once a pointer is initialized with an address of another object, the dereference operator `*` can be used to access the value at that address.
- Putting it all together:

```C++
#include <iostream>

int main()
{
    int x{ 5 };
    std::cout << x << '\n'; // print the value of variable x

    int* ptr{ &x }; // ptr holds the address of x
    std::cout << *ptr << '\n'; // use dereference operator to print the value at the address that ptr is holding (which is x's address)

    return 0;
}
```

>[!warning] type of a pointer must match the type of the object being pointed to.
>An `int` pointer must point to an `int` object. If an `int` pointer points to a `double` or any type other than `int`, than it will result in an error.

### Pointers and assignment
- Assignment with pointers can be used in two different ways:
	- To change the pointee (by assigning the pointer a new address).
	- To change the value of the pointee (by assigning the dereferenced pointer a new value).
- An example of pointer assignment changing the pointee:

```C++
#include <iostream>

int main()
{
    int x{ 5 };
    int* ptr{ &x }; // ptr initialized to point at x

    std::cout << *ptr << '\n'; // print the value at the address being pointed to (x's address)

    int y{ 6 };
    ptr = &y; // // change ptr to point at y

    std::cout << *ptr << '\n'; // print the value at the address being pointed to (y's address)

    return 0;
}
```

```console
5
6
```

- An example of pointer assignment changing the value of the pointee:

```C++
#include <iostream>

int main()
{
    int x{ 5 };
    int* ptr{ &x }; // initialize ptr with address of variable x

    std::cout << x << '\n';    // print x's value
    std::cout << *ptr << '\n'; // print the value at the address that ptr is holding (x's address)

    *ptr = 6; // The object at the address held by ptr (x) assigned value 6 (note that ptr is dereferenced here)

    std::cout << x << '\n';
    std::cout << *ptr << '\n'; // print the value at the address that ptr is holding (x's address)

    return 0;
}
```

```console
5
5
6
6
```


### The address-of operator returns a pointer
- Technically speaking, the address-of operator `&` does NOT return the address of its operand (as a literal). Instead, it returns a pointer containing the address of the operand, whose type is derived from the argument.
- For example:

```C++
#include <iostream>
#include <typeinfo>

int main()
{
	int x{ 4 };
	std::cout << typeid(&x).name() << '\n'; // print the type of &x

	return 0;
}
```

- The code above prints `int *` (on Visual Studio) or `pi` (with GCC). The result of `typeid().name()` is compiler-dependent.

### The size of pointers
- The size of a pointer is dependent upon the architecture the executable is compiled for.
	- A 32-bit executable uses 32-bit memory addresses.
	- Consequently, a pointer on a 32-bit machine is 32 bits (4 bytes), which also means a pointer on a 64-bit machine is 64 bits (8 bytes).
- Note that the size of the pointer remains the same regardless of the size of the pointee.

### Dangling pointers
- A **dangling pointer** (invalid pointer) is a pointer that is holding the address of an object that is no longer valid (e.g. because it has been destroyed).
	- Dereferencing a dangling pointer will lead to an undefined behavior. However, any other use of an invalid pointer value is implementation-defined.
- An example of a dangling pointer:

```C++
#include <iostream>

int main()
{
    int x{ 5 };
    int* ptr{ &x };

    std::cout << *ptr << '\n'; // valid

    {
        int y{ 6 };
        ptr = &y;

        std::cout << *ptr << '\n'; // valid
    } // y goes out of scope, and ptr is now dangling

    std::cout << *ptr << '\n'; // undefined behavior from dereferencing a dangling pointer

    return 0;
}
```

### Null pointers
- Besides a memory address, there is one additional value that a pointer can hold; a **null value**, which is a special value that means something has no value.
- When a pointer is holding a null value, it means the pointer is not pointing at anything. Such a pointer is called a **null pointer**.
- There are multiple ways to initialize a null pointer:
	- Using `nullptr` (C++11 and later)
		- e.g. `int* ptr = nullptr;`
	- Using `NULL` (inherited from C. NOT recommended)
		- e.g. `int* ptr = NULL;`
	- Using `0` (NOT recommended)
		- e.g. `int* ptr = 0;` or `int* ptr = (int*)0;`
	- Using `std::nullptr_t`
		- e.g. `std::nullptr_t nullPtr = nullptr; int* ptr = static_cast<int*>(nullPtr);`
	- Using empty direct initialization (which defaults to `nullptr`)
		- e.g. `int* ptr {};`

>[!important] Using `nullptr` to initialize a null pointer is generally recommended in modern C++.
>Use `std::nullptr_t` to explicitly define a type that holds a null pointer. It's less common for pointer initialization, but it is useful for function signatures and template programming.

>[!warning] Dereferencing a null pointer results in undefined behavior.

- A null pointer can be checked by using a conditional to test whether a pointer has value `nullptr` or not (e.g. `if (ptr == nullptr)`).
	- Another way is to simply omit the `== nullptr` part (e.g. `if (ptr)`), which works because pointers get implicitly converted to a boolean value (`false` if null pointer, `true` otherwise).

>[!warning] Conditionals can only be used to differentiate null pointers from non-null pointers.
>There is no convenient way to determine whether a non-null pointer is pointing to a valid object or an invalid object (dangling).

>[!important] Avoid dereferencing a null pointer by using a conditional to ensure a pointer is non-null.
>Also, it is the dev's responsibility to ensure that all pointers to an object that has just been destroyed are properly set to `nullptr`.

### Pointer vs. reference
- Pointers and references both provide a way to indirectly access another object. The primary difference is that with pointers, the address-of and dereference happens explicitly, whereas with references, they happen implicitly.
- There are some other differences between pointers and references:
	- References are not objects, whereas pointers are.
	- References can NOT be reseated (changed to reference something else), while pointers can change their pointee.
	- References must always be bound to an object, while pointers can point to nothing.
	- References are "safe" (outside of dangling references), but pointers are inherently dangerous (discussed later).

>[!important] Use references when you want to ensure that an object is always valid and prefer cleaner syntax.

>[!important] Use pointers when you need to allow for nullability, perform dynamic memory management, or need more flexible ownership semantics.

- References are generally safer to use, so it's best to favor references over pointers.

### Pointers and const
- `const` works on pointers in two different ways : `const int*` and `int* const`.
	- The difference between those two lies in what is being made constant; the pointer itself or the value being pointed to.
- `const int*` means that the pointer points to a constant integer. In other words, it is a non-const pointer that points to a `const int` value (its value cannot be changed). For example:

```C++
const int* ptr = &x;
*ptr = 5; // Error: cannot modify the value through the pointer.
ptr = &y; // Okay: can change the poitner to point to another integer.
```

>[!warning]
>While `const int*` can point to a constant integer, `int*` cannot and it will cause a compile error.

- `int* const` means that the pointer itself is a const pointer. In other words, the pointer cannot be changed to point to another address, but the value of the integer it points to can be modified. For example:

```C++
int* const ptr = &x;
*ptr = 5;  // Okay: Can modify the value through the pointer.
ptr = &y;  // Error: Cannot change the pointer itself.
```

>[!important]
>`const int*` is referred to as **pointer-to-const**. `int* const` is referred to as **const pointer**.

- It is possible to combine pointer-to-const and const pointer, which makes **const-pointer-to-const**. It cannot be changed to point to another address, nor can the value of the pointee be changed.
	- It can only be dereferenced to get the value it is pointing at.

## Intro to pass by address
### Pass by address

>[!reminder]
>Values can be passed to a function via pass-by-value or pass-by-reference.

- C++ provides a third way to pass values to a function called pass-by-address.
- **Pass-by-address** means passing the memory address of a variable to a function, allowing the function to access and modify the actual variable.
	- This is typically done by using a pointer for a function parameter (e.g. `int* ptr`), and then making a function call with an argument that has an address-of operator (e.g. `&arg`).
- For example:

```C++
#include <iostream>
using namespace std;

void increment(int* ptr) {
    (*ptr)++;  // Dereference the pointer and increment the value
}

int main() {
    int x = 10;
    increment(&x);  // Pass the address of x
    cout << "x = " << x << endl;  // Output: x = 11
    return 0;
}
```

- **Key characteristics of pass-by-address:**
	- **Modifying the original variable**: since the function gets the address of the variable, it can modify the original value stored at that address.
	- **Memory efficiency**: instead of copying large objects, only the address (usually 4 or 8 bytes) is passed, making it efficient when dealing with large data structures.
	- **Pointer syntax**: a pointer is used in the function's parameter to receive the address.

>[!warning] Pass-by-address deals with a pointer, which means there should be a safe guard against a null pointer.
>Either set a logic for when the argument is NOT a null pointer, or terminate early (using return or static_return) if it is a null pointer.

### Pass by address cannot handle rvalue
- Pass-by-address does not work with an rvalue. This is because an rvalue is a temporary value that does not have a memory address, and pointers require a valid memory address to point to.
	- If an rvalue is passed (to a function that uses pass by address), then a compilation error will occur.
- An rvalue can be handled by pass-by-value, or pass-by-reference-to-const.

>[!reminder]
>Unlike pass-by-reference, pass-by-reference-to-const can handle rvalue; a temporary object is made for the rvalue.

### Null pointer as default argument
- One of the common uses for pass-by-address is to allow a function to accept an "optional" argument. For example:

```C++
#include <iostream>

void printIDNumber(const int *id=nullptr)
{
    if (id)
        std::cout << "Your ID number is " << *id << ".\n";
    else
        std::cout << "Your ID number is not known.\n";
}

int main()
{
    printIDNumber(); // we don't know the user's ID yet

    int userid { 34 };
    printIDNumber(&userid); // we know the user's ID now

    return 0;
}
```

- In the example above, because the default argument is set to `nullptr`, when the function call is made without an argument, it defaults to a null pointer - which the function deals with accordingly.

>[!important] Function overloading with either pass-by-value or const-pass-by-reference may be better.

### Pass by address by reference
- Consider a function `nullify(int* ptr2)` whose purpose is to set the pointer (with a function call `nullify(ptr)`) to a null pointer `ptr2 = nullptr;`. Unlike pass-by-address where the pointer is able to modify the value of the pointee, the function is unable to change the address the pointer is pointing to; this is because a copy of the pointer is made, and any changes to that copy does not affect the original pointer.
- In order to modify the address that a pointer is holding, a **pass-by-address-by-reference** is needed. For example:

```C++
#include <iostream>

void nullify(int*& refptr) // refptr is now a reference to a pointer
{
    refptr = nullptr; // Make the function parameter a null pointer
}

int main()
{
    int x{ 5 };
    int* ptr{ &x }; // ptr points to x

    std::cout << "ptr is " << (ptr ? "non-null\n" : "null\n");

    nullify(ptr);

    std::cout << "ptr is " << (ptr ? "non-null\n" : "null\n");
    return 0;
}
```

### std::nullptr_t
- `std::nullptr_t`, defined in header `<cstddef>`, is the type for `nullptr`. It is useful for when writing a function that only accepts a null pointer. For example:

```C++
#include <iostream>
#include <cstddef> // for std::nullptr_t

void print(std::nullptr_t)
{
    std::cout << "in print(std::nullptr_t)\n";
}

void print(int*)
{
    std::cout << "in print(int*)\n";
}

int main()
{
    print(nullptr); // calls print(std::nullptr_t)

    int x { 5 };
    int* ptr { &x };

    print(ptr); // calls print(int*)

    ptr = nullptr;
    print(ptr); // calls print(int*) (since ptr has type int*)

    return 0;
}
```

### Pass-by-address vs. pass-by-reference
- Pass-by-address is preferred over pass-by-reference in these scenarios:
	- Dynamic memory management: necessary for allocating and freeing memory with `new` and `delete`.
	- Passing null or optional values: pointers can be null, unlike references.
	- Modifying multiple variables: pointers can modify multiple variables explicitly via addresses.
	- Array manipulation: pointers allow efficient iteration and manipulation of array elements.
	- Interfacing with C-style APIs: C functions expect pointers, not references.
	- Multiple levels of indirection: when dealing with pointers-to-pointers (or higher levels).
	- Low-level system programming: required for direct memory access and hardware interaction.
- Pass-by-reference is preferred over pass-by-address in these scenarios:
	- Modifying variables or objects in functions without the complexity of pointers.
	- Passing large objects or structs efficiently, without copying.
	- Operator overloading for classes, keeping the syntax clean.
	- Generic programming with function templates, avoiding pointer complications.
	- Avoiding pointer-related issues, such as null pointers or pointer arithmetic errors.

## Return by reference and return by address
- When a function returns a value, a copy of that value is made. If the return type of the function is a class type (e.g. `std::string`), this can be expensive. There are two ways to avoid making a copy from a function return: return-by-reference and return-by-address.

### Return by reference
- **Return-by-reference** means that a function returns a reference to an object, rather than returning a copy of the object. When returning by reference, the caller of the function gets direct access to the original object, allowing modifications to the returned value to affect the original object.
- Key characteristics of return-by-reference:
	- **No copy is made**: the function returns a reference to an existing object, so no new object is created or copied.
	- **Modifications affect the original**: if the function returns a non-const reference, the caller can modify the returned object, and those changes will affect the original object.
	- **The object must outlive the function**: the object being returned by reference must have a lifetime that extends beyond the function's scope. Returning a reference to a local variable will result in undefined behavior.
- For example:

```C++
int& getElement(int arr[], int index) {
    return arr[index];  // Returns a reference to an element in the array
}

int main() {
    int numbers[] = {1, 2, 3, 4, 5};
    getElement(numbers, 2) = 10;  // Modifies the 3rd element of the array
    cout << numbers[2];  // Output: 10
    return 0;
}
```

- In the example above, `getElement()` returns a reference to an element in the array `numbers[]`. Using the reference returned by the function, an element in the array can be modified.

### Return by const reference
- Sometimes it's preferrable to prevent the caller from modifying the returned reference (referenced object). This can be done by using `const` keyword. For example:

```C++
const int& getElement(const int arr[], int index) {
    return arr[index];  // Returns a const reference
}

int main() {
    int numbers[] = {1, 2, 3, 4, 5};
    const int& elem = getElement(numbers, 2);  // elem is a const reference
    cout << elem;  // Output: 3
    // elem = 10;  // Error: Cannot modify a const reference
}
```

>[!warning]
>A return by non-const reference to a const object does NOT work. Only return by const reference works in this case.

>[!warning]
>While const reference bound to a literal can create a temporary object that has an extended lifetime (thus making the reference valid), this does not apply to a literal that is returned by const reference (thus making the reference invalid).
>
>This is true regardless of whether the literal was returned directly (e.g. `return 5`) or indirectly (e.g. `foo(5)`).
>
>Note that return by const reference to a literal results with a dangling reference, which does not always raise a warning or an error.

### Returning local variables by reference
- Returning a local variable inside a function causes an undefined behavior as the lifetime of the local variable is limited to the end of the function scope.
- However, a local variable inside a function can be returned by reference if its lifetime is than that of the function; which can be achieved by using the `static` keyword.
- For example:

```C++
#include <iostream>
#include <string>

const std::string& getProgramName() // returns a const reference
{
    static std::string s_programName { "Calculator" }; // has static duration, destroyed at end of program

    return s_programName;
}

int main()
{
    std::cout << "This program is named " << getProgramName();

    return 0;
}
```

```console
This program is named Calculator
```

- An issue with returning a static local variable by reference can occur if the function modifies the value of the local variable (with each function call). For example:

```C++
#include <iostream>
#include <string>

const int& getNextId()
{
    static int s_x{ 0 }; // note: variable is non-const
    ++s_x; // generate the next id
    return s_x; // and return a reference to it
}

int main()
{
    const int& id1 { getNextId() }; // id1 is a reference
    const int& id2 { getNextId() }; // id2 is a reference

    std::cout << id1 << id2 << '\n';

    return 0;
}
```

```console
22
```

- In the example above, the intended result might've been `12` with `id1` being assigned `1` and `id2` being assigned `2`, but because both `id1` and `id2` references the same static variable, they both hold the value of `2` (which prints out `22` at the end).
- It's best to avoid modifying the value of the static local variable, and one of the best way to prevent the modification is to use `const` (e.g. `static const int&`).
	- This topic ties to [[#Avoid non-const global variables]].
- It is possible to assign a normal variable with a copy of the returned reference. For example:

```C++
#include <iostream>
#include <string>

const int& getNextId()
{
    static int s_x{ 0 };
    ++s_x;
    return s_x;
}

int main()
{
    const int id1 { getNextId() }; // id1 is a normal variable now and receives a copy of the value returned by reference from getNextId()
    const int id2 { getNextId() }; // id2 is a normal variable now and receives a copy of the value returned by reference from getNextId()

    std::cout << id1 << id2 << '\n';

    return 0;
}
```

```console
12
```

- It is possible to combine pass-by-reference and return-by-reference:

```C++
#include <iostream>
#include <string>

// Takes two std::string objects, returns the one that comes first alphabetically
const std::string& firstAlphabetical(const std::string& a, const std::string& b)
{
	return (a < b) ? a : b; // We can use operator< on std::string to determine which comes first alphabetically
}

int main()
{
	std::string hello { "Hello" };
	std::string world { "World" };

	std::cout << firstAlphabetical(hello, world) << '\n';

	return 0;
}
```

```console
Hello
```

### Combining pass by address and return by reference
- For example:

```C++
#include <iostream>
using namespace std;

// Function that returns a reference to an element from the array
int& getElementByReference(int* arr, int index) {
    return *(arr + index);  // Return a reference to the element at the given index
}

int main() {
    int numbers[] = {10, 20, 30, 40, 50};  // An array of 5 integers

    // Get a reference to the 3rd element (index 2) and modify it
    getElementByReference(numbers, 2) = 100;  // Modify the 3rd element to 100

    // Output the modified array
    for (int i = 0; i < 5; i++) {
        cout << numbers[i] << " ";  // Output: 10 20 100 40 50
    }

    return 0;
}
```


### Return by address
- <mark class="hltr-trippy">Return-by-address</mark> is a method where a function returns a pointer (i.e. the address) to an object or a variable.
	- This approach allows the calling code to access and manipulate the object directly via its address.
	- Returning by address if often used to avoid copying large objects or to allow a function to return dynamically allocated memory.
- Key pointers of return-by-address:
	- **Returns a pointer**: instead of returning a copy of the object, the function returns a pointer to the object, allowing the caller to access the original object.
	- **Modifying the object**: the caller can use the returned address to modify the object (if it's not a `const` pointer).
	- **Dynamic memory management**: return by address is commonly used when returning dynamically allocated memory using `new` or similar constructs.
	- **Risk of dangling pointers**: if the function returns the address of a local object (automatic storage duration), it results in undefined behavior, as the object is destroyed when the function ends.
- An example of returning address of a global variable:

```C++
int globalVar = 100;

int* getGlobalVarAddress() {
    return &globalVar;  // Return the address of globalVar
}

int main() {
    int* ptr = getGlobalVarAddress();  // Get the address of globalVar
    cout << *ptr << endl;  // Output: 100
    *ptr = 200;            // Modify globalVar through the pointer
    cout << globalVar;     // Output: 200
}
```

- An example of returning address of a static local variable:

```C++
#include <iostream>
#include <string>

int* getStaticVarAddress()
{
    static int x = 5;
    return &x;
}

int main()
{
    int* ptr = getStaticVarAddress();
    std::cout << *ptr << std::endl;
    *ptr = 300;
    std::cout << *ptr << std::endl;

    return 0;
}
```

- The object being returned by address must outlive the scope of the function returning the address, otherwise the caller will receive a dangling pointer.
- The major advantage of return by address (over return by reference) is that the function can return `nullptr` if there is no valid object to return.
	- Conversely, the disadvantage is that the caller has to do a `nullptr` check before dereferencing the return value.

## In and out parameters
- A function and its caller communicate with each other via two mechanisms: parameters and return values.
	- When a function is called, the caller provides arguments, which the function receives via its parameters. These arguments can be passed by value, reference, or address.
- Typically, a parameter is used to pass data into a function which is then used to generate some kind of result that is passed back to the caller as a return value. However, it is possible to use parameters to return data from a function to the caller.

### In parameters
- In most cases, a function parameter is used only to receive an input from the caller. Parameters that are used only for receiving input from the caller are sometimes called **in-parameters**.
- For example:

```C++
#include <iostream>

void print(int x) // x is an in parameter
{
    std::cout << x << '\n';
}

void print(const std::string& s) // s is an in parameter
{
    std::cout << s << '\n';
}

int main()
{
    print(5);
    std::string s { "Hello, world!" };
    print(s);

    return 0;
}
```

- In-parameters are typically passed by value or by const reference.

### Out parameters
- An **out-parameter** is a parameter that is passed to a function with the intention that the function will modify it and provide a result (or output) back to the caller through that parameter.
	- Unlike a regular parameter (in-parameter) that is used to pass data into a function, an out-parameter is used to return data from a function.
- Out-parameters are typically implemented using:
	- Pointers (pass-by-address)
	- References (pass-by-reference)
- Using a pointer as an out-parameter:

```C++
void getCoordinates(int* x, int* y) {
    *x = 10;  // Modify the value pointed to by x
    *y = 20;  // Modify the value pointed to by y
}

int main() {
    int a, b;
    getCoordinates(&a, &b);  // Pass the address of a and b
    cout << "x: " << a << ", y: " << b << endl;  // Output: x: 10, y: 20
}
```

- Using a reference as an out-parameter:

```C++
void getCoordinates(int& x, int& y) {
    x = 10;  // Modify x directly
    y = 20;  // Modify y directly
}

int main() {
    int a, b;
    getCoordinates(a, b);  // Pass variables directly (no need for addresses)
    cout << "x: " << a << ", y: " << b << endl;  // Output: x: 10, y: 20
}
```

- The main difference between using a pointer or a reference is that the pointer can be null whereas the reference cannot.
- Out-parameter is useful for a few reasons:
	- Out-parameters can be used to return multiple values from a function (a normal return is limited to one value).
	- Out-parameter can be used to modify a variable directly.
	- Out-parameter can be used to avoid returning large objects by value (which can involve copying).
- Example of using out-parameter to return multiple values:

```C++
void divide(int dividend, int divisor, int& quotient, int& remainder) {
    quotient = dividend / divisor;
    remainder = dividend % divisor;
}

int main() {
    int quotient, remainder;
    divide(10, 3, quotient, remainder);  // quotient = 3, remainder = 1
    cout << "Quotient: " << quotient << ", Remainder: " << remainder << endl;
}
```

>[!warning] Avoid overusing out-parameters.
>While out-parameters can be useful, overusing them can make code harder to read and maintain. In many cases, returning a tuple or a struct that contains multiple values can be a cleaner solution.


## Type deduction with pointers, references, and const

### Type deduction default behaviors
>[!reminder] `auto` keyword can be used to have the compiler deduce the type of a variable from the initializer.

- `auto` keyword (type deduction) will drop `const` from its initializer by default, unless `const` qualifier is added before the `auto` keyword (e.g. `const auto someConstVar;`).
- `auto` keyword (type deduction) will drop the reference qualifier `&` from its initializer by default, unless the reference qualifier is added after the `auto` keyword (e.g. `auto& someRef;`).
- `auto` keyword (type deduction) does NOT drop pointers.
	- `auto` and `auto*` essentially does the same. However, if the initializer is dereferenced, `auto*` will not compile.

### Top-level and low-level const
- The terms top-level const and low-level const refer to different types of `const` qualifiers, depending on where the `const` is applied in a declaration. These qualifiers define whether the object itself is constant or whether the data being pointed to (or referenced) is constant.

#### Top-level const
- A <mark class="hltr-trippy">top-level const</mark> refers to the const-qualification of the object itself. In other words, the object (whether it is a primitive type, a pointer, or a reference) is constant and cannot be modified.
- Top-level const is about preventing changes to the object, but it does not impose restrictions on what the object points to, if the object is a pointer.
- Example of top-level const:

```C++
const int x = 5; // value of x cannot be changed.
int* const ptr = nullptr; // ptr itself cannot be modified.
```

#### Low-level const
- A <mark class="hltr-trippy">low-level const</mark> applies to the data pointed to (or referred to) by an object. It indicates that the object being pointed to cannot be modified, even though the pointer (or reference) itself may not be constant.
- Example of low-level const:

```C++
const int x = 5;
const int* ptr = &x; // canot modify the value of *ptr
const int& ref = x; // cannot modify the value of ref
```

>[!important] Top-level const and low-level const can be combined.
>For example: `const int* const ptr = &x;`

### Type deduction and const references
- If the initializer is a reference to const, the reference is dropped first (and then reapplied if applicable), and then any top-level const is dropped from the result. For example:

```C++
#include <string>

int main()
{
    const std::string x = "Hello World";
    const std::string& ref = x;
    auto y = ref;

    return 0;
}
```

- In the example above, the type deduction drops both `const` qualifier and the reference qualifier. `y` is simply a `std::string` object with value `"Hello World"`.
- The `const` qualifier can be reapplied (e.g. `const auto`), along with the reference qualifier (e.g. `const auto&`).

### (const) auto reference to const object
- When `auto&` is bound to a `const` object, the reference is deduced as `const` type.
	- In other words, if the object you're binding to is `const`, the deduced type will automatically include the `const` qualifier, and the reference cannot be used to modify the object.
- Although `auto&` deduces the `const` qualifier from the object, the `const` qualifier can be explicitly declared in the reference type (e.g. `const auto&`).
	- When `const auto&` is used, even if the initializer is non-const, the reference will be `const`.
	- `const auto&` is able to bind to a temporary object created from a literal (rvalue initializer).

>[!warning]
>Do not confuse (1) the use of `auto` with `const` initializer, and (2) the use of `auto&` with `const` initializer.


### Type deduction and constexpr
- `auto` and `constexpr` can work together, but their interaction follows some specific rules.

#### constexpr auto for variables
- When you declare a variable as `constexpr auto`, the type is deduced from the initializer, and the compiler ensures that the variable is a **constant** that must be evaluated at compile time.
- For example:

```C++
constexpr auto x = 42; // x is deduced as a constant int with the value 42
```

#### constexpr auto with functions (C++14)
- When using `constexpr auto` with a function, it means that the return type of the function is deduced by the compiler, and the function is capable of being evaluated at compile time if the arguments are constant expressions.
	- The return type of a `constexpr` function using `auto` can only be deduced in C++ 14 and above. In C++11 and below, the return type has to be explicitly specified for `constexpr` functions.
- For example:

```C++
constexpr auto square(auto x)
{
	return x * x;
}

int main()
{
	constexpr auto result = square(5); // Deduced as int, compile-time eval
}
```

- In the example above, since `square()` is called with a constant expression `5`, the result is computed at compile time.

>[!warning]
>If a variable is declared using `auto` without the `constexpr` keyword but its initializer is a constant expression, the variable will not necessarily be initialized at compile time. Instead, it will be initialized at runtime, even though the initializer is a constant expression.
>
>For example, `auto y = square(10);` may deduce an `int` type, but the result may be calculated at runtime. Essentially, this is the same with `auto y = 10;` (because `10` is a constant expression).

#### constexpr auto references
- You can use `constexpr` with `auto&` or `auto&&` when dealing with references.
	- This ensures that the reference itself is bound to a constant expression, and the type is deduced as a reference.
- For example:

```C++
constexpr int value = 10;
constexpr auto& ref = value; // ref is a constexpr reference to a const int
```

- In the example above, `ref` is deduced to be a `const int` reference to `value`. Because both `value` and `ref` are `constexpr`, their evaluation happens at compile time.

>[!reminder]
>`constexpr` implies `cosnt` for objects, but not for functions.

#### constexpr auto reference to const object

>[!warning]
>Constant expressions involving `constexpr` and `const` is rather difficult subject to deal with; especially so with `constexpr`. What I've wrote for this section is an answer from ChatGPT, so take it with a grain of salt.

- A `constexpr` reference can only be bound to an object or value that is constant expression. Since a `const` object is a constant expression (if it's initialized with a compile-time constant), it can be used to bind a `constexpr` reference.
- When a `constexpr` reference is bound to a `const` object, it enforces the same compile-time evaluation and immutability.
- For example:

```C++
constexpr int value = 10;
constexpr const int& ref = value;
```

### Type deduction and pointers
- Type deduction does not drop pointers. As such, `auto` will deduce to a pointer if the initializer is a pointer (e.g. `auto ptr2 = ptr1;`).
	- An asterisk can be used in conjunction with pointer type deduction (`auto*`) to make it explicit that the deduced type is a pointer (e.g. `auto* ptr2 = ptr1;`).

>[!warning]
>Deducing a pointer type with either `auto` or `auto*` makes no real difference. However, `auto` is more flexible because it can deduce both pointer types and non-pointer types. When `auto*` is used and the initializer is not a pointer type, then a compile error will occur.

#### Type deduction and const pointers
- `const auto` and `auto const` does the same thing, just as `const int` and `int const` is the same.
- However, the order of the `const` qualifier matters when `auto*` is involved.
	- A `const auto*` means "make the deduced pointer type a pointer to const" (pointer to const, e.g. `const int*`).
	- A `auto* const` means "make the deduced pointer type a const pointer" (a const pointer, e.g. `int const*`).
- An example where the initializer is a const pointer to const:

```C++
#include <string>

int main()
{
    std::string s{};
    const std::string* const ptr { &s };

    auto ptr1{ ptr };  // const std::string*
    auto* ptr2{ ptr }; // const std::string*

    auto const ptr3{ ptr };  // const std::string* const
    const auto ptr4{ ptr };  // const std::string* const

    auto* const ptr5{ ptr }; // const std::string* const
    const auto* ptr6{ ptr }; // const std::string*

    const auto const ptr7{ ptr };  // error: const qualifer can not be applied twice
    const auto* const ptr8{ ptr }; // const std::string* const

    return 0;
}
```

## std::optional (C++17)
- `std::optional` represents an optional object that may or may not contain a value, essentially wrapping a type to indicate the presence or absence of a value.
- An `std::optional` object either:
	- contains a value (which can be accessed safely).
	- does not contain a value (i.e. is in an empty or nullopt state).
- `std::optional` is useful for situations where a function or operation might not return a valid value, but you don't want to use special sentinel values (like `0`, `-1`, or `nullptr`) or exceptions to represent the absence of a result.
- `std::optional` lives in a header called `<optional>`.
	- Include the header like so: `#include <optional>`
- A simple way to declare an `std::optional` object (defaults to no value):
	- `std::optional<int> optInt;`
- You can assign a value or use `std::nullopt` to indicate the absence of a value:
	- `optInt = 42;`
	- `optInt = std::nullopt;`
	- You can also use `.reset()` to rest the object to an empty state (equivalent to `std::nullopt`).
- You can check if an `std::optional` object has a value by using its member function `.has_value()`, which returns `true` if the object does hold a value.
- The value of an `std::optional` object can be accessed via its member function `.value()`.
	- Be aware that calling `.value()` on an empty `std::optional` will throw an exception (`std::bad_optional_access`).
	- A safer way to access the value is to use the dereference operator `*` or `.value_or(default_value)` which provides a default value if the `std::optional` object is empty.
- For example:

```C++
std::optional<int> opt = 10;
std::cout << *opt << '\n';            // Outputs 10

std::cout << opt.value_or(0) << '\n'; // Outputs 10 if opt has a value, otherwise 0
```

- `std::optional` is ideal for functions that might fail but can't throw exceptions (or where using sentinel values is problematic).
- Instead of pairing the return value with a `bool` to indicate success or failure (using `std::pair<bool, T>`), `std::optional` can be used to directly return either a valid result (success) or an empty state (failure). For example,

```C++
std::optional<int> divide(int a, int b)
{
    if (b == 0) {
        return std::nullopt;  // No valid result (division by zero)
    } else {
        return a / b;
    }
}
```

- When a function has optional arguments, using `std::optional` can indicate that the parameter is optional in a more structured way than using default values. For example:

```C++
void printMessage(std::optional<std::string> name)
{
    if (name) {
        std::cout << "Hello, " << *name << '\n';
    } else {
        std::cout << "Hello, World!\n";
    }
}
```


## Intro to compound data types
- Compound data types (aka composite data types) are data types that can be constructed from fundamental data types (or other compound data types). These types allow the dev to group multiple values together, providing a way to manage and manipulate related data as a single unit.
- C++ supports the following compound types:
	- Functions
	- Arrays
	- Pointer types
	- Pointer to member types
	- Reference types
	- Enumerated types
	- Class types


## Intro to user-defined types
- A <mark class="hltr-trippy">user-defined type (UDT)</mark> is a data type that is defined by the programmer (user), rather than being one of the built-in types like `int`, `char`, or `float`.
	- User-defined types allow you to create more complex data structures that better model real-world entities or organize data and behavior in a way that suits your application's needs.
	- Defining a user-defined type is called a <mark class="hltr-trippy">type definition</mark>.
- There are several ways to define user-defined types, including:
	- classes (`class`)
	- structures (`struct`)
	- Unions (`union`)
	- Enumerations (`enum`)
	- Type aliases (`typedef`, `using`)
- As covered in [[#Typedefs and type aliases]], an alias for an existing type can be made (which counts as user-defined type). For example,

```C++
#include <iostream>

using length = int; // define a type alias with identifier 'length'

int main()
{
    length x { 5 }; // we can use 'length' here since we defined it above
    std::cout << x << '\n';

    return 0;
}
```

- By convention, user-defined types are named starting with a capital letter and without using a suffix (e.g. `Fraction`).
- In a multi-file program, it's best to place type definitions in header files. These header files can be included into any code file that requires that type definition.
- Type definitions doesn't allow for forward declarations. The compiler typically needs to see the full definition to use a given type.
	- This means that types are exempt from the one-definition rule; given type is allowed to be defined in multiple code files. However, all of the type definitions must be identical (otherwise undefined behavior will occur).
- In a more recent trend, user-defined type is being referred to as program-defined types instead. The term "user-defined" is a little too vague and encompassing, as it could include even the type definitions from the standard library. It makes more sense to say program-defined type, in order to indicate "a type defined within your own program".

## Intro to enum types
### Unscoped enumerations
- An <mark class="hltr-trippy">enum (short for enumeration)</mark> is a user-defined type that consists of a set of named integral constants.
	- It is used to define a type that can only take one of a limited, predefined set of values, making your code more readable, organized, and type-safe when working with a fixed set of related values.

#### Type definition using enum
- An `enum` is declared using the keyword `enum`, followed by a name and a list of **named constants** enclosed in curly braces. For example:

```C++
enum Color
{
	Red,
	Green,
	Blue
};
```

>[!important] Always end type definition with a semicolon.

- By default, the named constants in `enum` are implicitly assigned integer values starting from `0`.
	- In the example above, `Red` is assigned `0`, Green a `1`, and Blue a `2`.
	- The named constants are also called <mark class="hltr-trippy">enumerators</mark>.

#### Variable declaration using enum
- Having defined an `enum` type, variables can be declared using the type. For example:

```C++
Color favoriteColor = Blue;

if (favoriteColor == Blue) {
    std::cout << "You like blue!" << std::endl;
}
```

>[!warning] Variable of `enum` type can only be assigned a value using its named constants.
>Even though named constants are assigned integer values, assigning an `enum` variable with an integer value (matching one of the named constants) results in an error.

#### Custom value assignment for enum constants
- You can explicitly assign custom integer values to enum constants. For example:

```C++
enum ErrorCode {
    Success = 0,
    NotFound = 404,
    ServerError = 500
};

ErrorCode code = NotFound;
if (code == 404) {
    std::cout << "Resource not found!" << std::endl;
}
```

>[!warning] Named constants in enum cannot be assigned values outside its scope.

### Scoped enumerations
- In C++11 and above, a more type-safe version of `enum` is introduced, which is called `enum class` (or scoped enum). Unlike traditional enums, `enum class` prevents implicit conversion to integers and avoids naming collisions in the global scope.
- An example of `enum class`:

```C++
enum class Direction {
    North,
    South,
    East,
    West
};

Direction dir = Direction::North;

if (dir == Direction::North) {
    std::cout << "Heading north!" << std::endl;
}
```

- Note that the scope resolution operator `::` is used to access the enumerators.
- The main differences between unscoped and scoped enums are:
	- Enumerators in `enum class` cannot be implicitly converted to an integer. In other words, each enum constants are NOT given integer values.
	- Enumerators in `enum` class are scoped within `enum class`.
	- `enum class` is more type-safe, as there aren't any risk for naming conflicts.
	- `enum class` is preferred in modern C++.

>[!important] Named constants in `enum class` still hold integer values.
>Just like with unscoped enums, named constants in scoped enums hold integer values by default (starting at `0`). Custom values can be assigned to them as well.
>
>Note that even though named constants in scoped enums hold integer values, they cannot be directly compared to an integer value because implicit conversion to integer is NOT allowed. Explicit conversion (e.g. `static_cast<int>`) must be used on named constants in order to make comparison with an integer value.

#### Enum class and type-safety
- Traditional (unscoped) enum can result in unintended behavior. For example:

```C++
enum Color { Red, Green, Blue };
enum TrafficLight { RedLight, GreenLight, YellowLight };

int main() {
    Color color = Red;  // OK
    TrafficLight light = Red;  // Error
}
```

- In the example above, assigning `Red` to `light` was not intended, but it is an easy mistake to make considering a traffic light can be red.
- Scoped enums are free from the issue mentioned above:

```C++
enum class Color { Red, Green, Blue };
enum class TrafficLight { Red, Green, Yellow };

int main() {
    Color color = Color::Red;  // No ambiguity, `Color::Red` is required
    TrafficLight light = TrafficLight::Red;  // Also clear, must use `TrafficLight::Red`
}
```

### Enum constant integer value increment
- For both scoped and unscoped, the named constants in enumeration are assigned integer values by default, starting at `0` (for the first named constant). For each named constant, the integer value is incremented by `1`.
- When a custom integer value is assigned to a named constant and the named constants that come afterwards are not assigned custom values, then those constant values are assigned values that are incremented from the custom value. For example:

```C++
enum Animal
{
    cat = -3,    // values can be negative
    dog,         // -2
    pig,         // -1
    horse = 5,
    giraffe = 5, // shares same value as horse
    chicken,     // 6
};
```

### Value-initializing an enumeration
- When a variable is defined with an enumeration type but is not initialized with a value (using empty brace initialization), the enum variable is default initialized with a `0`.
	- If none of its named constants are assigned custom values (meaning the first one defaults to `0`), then the enum variable is initialized with the first named constant.
	- However, if there is a named constant that is assigned a custom value of `0` (and the first named constant is assigned a value other than `0`), then the enum variable is initialized with that named constant.
	- Even if there are not any named constants with value of `0`, the enumeration will still be assigned a value of `0`.

>[!warning]
>If the first named constant in an enumeration is not assigned custom value (defaulting to `0`) and a named constant (other than the first) is assigned a custom value of `0`, then enum type variable that is default initialized will equal to both of those named constants. In other words, it will have named constants with duplicate values.

>[!important] Make enumerator representing `0` be meaningful.
>Enumerator representing `0` should either be the best default meaning that represents the enumeration type, or be a meaning that represents invalid/unknown.

### Enumeration size and underlying type (base)
- The specific integral type used to represent the value of enumerators is called the enumeration's <mark class="hltr-trippy">underlying type</mark> (or **base**).
- C++ standard does not specify which specific integral type should be used as the underlying type, so the choice is implementation-defined.
	- Most compilers will use `int` as the underlying type, unless a larger type is required to store the enumerator values. However, this may not be true for all compilers or platforms.
- It is possible to explicitly specify an underlying type for an enumeration. The underlying type must be an integral type. For example:

```C++
#include <cstdint>  // for std::int8_t
#include <iostream>

// Use an 8-bit integer as the enum underlying type
enum Color : std::int8_t
{
    black,
    red,
    blue,
};

int main()
{
    Color c{ black };
    std::cout << sizeof(c) << '\n'; // prints 1 (byte)

    return 0;
}
```


### Uses of enums
1. **Code clarity** : enums make your code more readable and meaningful by replacing magic numbers (like `0`, `1`, `-1`, etc.) with descriptive names.
2. **Compile-time type safety** : enums prevent accidental assignment of invalid values, as only the predefined constants can be used.
3. **Group related constants** : enums allow you to group related constants together under a single type, keeping your code organized.
4. **Switch statements** : enums are often used in `switch` statements to make decisions based on predefined states or categories. For example,

```C++
switch (dir) {
    case Direction::North:
        std::cout << "Going north!";
        break;
    case Direction::South:
        std::cout << "Going south!";
        break;
    // and so on...
}
```

### Real-life scenarios using enumerations
#### Traffic light system

```C++
enum class TrafficLight {
    Red,
    Yellow,
    Green
};

void displayTrafficLight(TrafficLight light) {
    switch (light) {
        case TrafficLight::Red:
            std::cout << "Stop!" << std::endl;
            break;
        case TrafficLight::Yellow:
            std::cout << "Get ready to stop!" << std::endl;
            break;
        case TrafficLight::Green:
            std::cout << "Go!" << std::endl;
            break;
    }
}

int main() {
    TrafficLight currentLight = TrafficLight::Red;
    displayTrafficLight(currentLight);
}
```

#### Order status in an e-commerce system

```C++
enum class OrderStatus {
    Pending,
    Shipped,
    Delivered,
    Cancelled
};

void printOrderStatus(OrderStatus status) {
    switch (status) {
        case OrderStatus::Pending:
            std::cout << "Your order is pending." << std::endl;
            break;
        case OrderStatus::Shipped:
            std::cout << "Your order has been shipped." << std::endl;
            break;
        case OrderStatus::Delivered:
            std::cout << "Your order has been delivered." << std::endl;
            break;
        case OrderStatus::Cancelled:
            std::cout << "Your order has been cancelled." << std::endl;
            break;
    }
}

int main() {
    OrderStatus myOrder = OrderStatus::Shipped;
    printOrderStatus(myOrder);
}
```

#### Error codes in a network application

```C++
enum class NetworkError {
    Success = 0,
    Timeout = 1,
    ConnectionLost = 2,
    InvalidRequest = 3
};

NetworkError sendRequest() {
    // Simulate a network error
    return NetworkError::Timeout;
}

int main() {
    NetworkError error = sendRequest();
    if (error == NetworkError::Timeout) {
        std::cout << "Network timeout occurred!" << std::endl;
    }
}
```

#### Log levels in a logging system

```C++
enum class LogLevel {
    Info,
    Warning,
    Error
};

void logMessage(LogLevel level, const std::string& message) {
    switch (level) {
        case LogLevel::Info:
            std::cout << "[INFO]: " << message << std::endl;
            break;
        case LogLevel::Warning:
            std::cout << "[WARNING]: " << message << std::endl;
            break;
        case LogLevel::Error:
            std::cout << "[ERROR]: " << message << std::endl;
            break;
    }
}

int main() {
    logMessage(LogLevel::Warning, "Disk space is running low.");
}
```

### Getting the name of an enumerator

```C++
#include <iostream>
#include <string_view>

enum Color
{
    black,
    red,
    blue,
};

constexpr std::string_view getColorName(Color color)
{
    switch (color)
    {
    case black: return "black";
    case red:   return "red";
    case blue:  return "blue";
    default:    return "???";
    }
}

int main()
{
    constexpr Color shirt{ blue };

    std::cout << "Your shirt is " << getColorName(shirt) << '\n';

    return 0;
}
```

### Getting an enumeration from an input string

```C++
#include <iostream>
#include <optional> // for std::optional
#include <string>
#include <string_view>

enum Pet
{
    cat,   // 0
    dog,   // 1
    pig,   // 2
    whale, // 3
};

constexpr std::string_view getPetName(Pet pet)
{
    switch (pet)
    {
    case cat:   return "cat";
    case dog:   return "dog";
    case pig:   return "pig";
    case whale: return "whale";
    default:    return "???";
    }
}

constexpr std::optional<Pet> getPetFromString(std::string_view sv)
{
    if (sv == "cat")   return cat;
    if (sv == "dog")   return dog;
    if (sv == "pig")   return pig;
    if (sv == "whale") return whale;

    return {};
}

int main()
{
    std::cout << "Enter a pet: cat, dog, pig, or whale: ";
    std::string s{};
    std::cin >> s;

    std::optional<Pet> pet { getPetFromString(s) };

    if (!pet)
        std::cout << "You entered an invalid pet\n";
    else
        std::cout << "You entered: " << getPetName(*pet) << '\n';

    return 0;
}
```

### Using enum statements (C++20)
- Introduced in C++20, a `using enum` statement imports all of the enumerators from an enum into the current scope.
	- When used with an `enum class` type, this allows us to access the enumerators without having to prefix each with the name of the `enum class`.
- For example:

```C++
#include <iostream>
#include <string_view>

enum class Color
{
    black,
    red,
    blue,
};

constexpr std::string_view getColor(Color color)
{
    using enum Color; // bring all Color enumerators into current scope (C++20)
    // We can now access the enumerators of Color without using a Color:: prefix

    switch (color)
    {
    case black: return "black"; // note: black instead of Color::black
    case red:   return "red";
    case blue:  return "blue";
    default:    return "???";
    }
}

int main()
{
    Color shirt{ Color::blue };

    std::cout << "Your shirt is " << getColor(shirt) << '\n';

    return 0;
}
```

## Intro to overloading the I/O operators
- Operator overloading allows you to redefine or "overload" the functionality of existing operators (such as `+`, `-`, `*`, etc.) for user-defined types.

### Overloading << operator to print an enumerator
- In the context of streaming output, `<<` is a stream insertion operator that takes two operands (meaning it is binary).
	- Left operand is often `std::cout`, which actually has a type of `std::ostream`.
	- Right operand ranges from `int`, `float`, and etc.
- `<<` operator can be thought of like a function that takes two arguments. First argument (left operand) is a reference to the output stream object (e.g. `std::ostream& out`) that will be returned from the function. For example:

```C++
std::ostream& operator<<(std::ostream& os, const T& obj)
{
	// write obj to stream
	return os;
}
```

- In order to print an enumerator (as string), two things must be achieved:
	- [[#Getting the name of an enumerator]]
	- [[#Intro to function overloading|Function overloading]]
- For example:

```C++
#include <iostream>
#include <string_view>

enum Color
{
	black,
	red,
	blue,
};

constexpr std::string_view getColorName(const Color& color)
{
    switch (color)
    {
    case black: return "black";
    case red:   return "red";
    case blue:  return "blue";
    default:    return "???";
    }
}

// Teach operator<< how to print a Color
// std::ostream is the type of std::cout, std::cerr, etc...
// The return type and parameter type are references (to prevent copies from being made)
std::ostream& operator<<(std::ostream& out, const Color& color)
{
    out << getColorName(color); // print our color's name to whatever output stream out
    return out;                 // operator<< conventionally returns its left operand

    // The above can be condensed to the following single line:
    // return out << getColorName(color)
}

int main()
{
	Color shirt{ blue };
	std::cout << "Your shirt is " << shirt << '\n'; // it works!

	return 0;
}
```

>[!important] `constexpr` works well with `std::string_view`.
>There are multiple benefits to using `constexpr` with `std::string_view`:
>- Compile-time evaluation
>- No dynamic memory allocation
>- Reduced runtime overhead
>- Immutability
>- Efficient memory usage

### Overloading >> operator to input an enumerator

```C++
#include <iostream>
#include <limits>
#include <optional>
#include <string>
#include <string_view>

enum Pet
{
    cat,   // 0
    dog,   // 1
    pig,   // 2
    whale, // 3
};

constexpr std::string_view getPetName(Pet pet)
{
    switch (pet)
    {
    case cat:   return "cat";
    case dog:   return "dog";
    case pig:   return "pig";
    case whale: return "whale";
    default:    return "???";
    }
}

constexpr std::optional<Pet> getPetFromString(std::string_view sv)
{
    if (sv == "cat")   return cat;
    if (sv == "dog")   return dog;
    if (sv == "pig")   return pig;
    if (sv == "whale") return whale;

    return {};
}

// pet is an in/out parameter
std::istream& operator>>(std::istream& in, Pet& pet)
{
    std::string s{};
    in >> s; // get input string from user

    std::optional<Pet> match { getPetFromString(s) };
    if (match) // if we found a match
    {
        pet = *match; // dereference std::optional to get matching enumerator
        return in;
    }

    // We didn't find a match, so input must have been invalid
    // so we will set input stream to fail state
    in.setstate(std::ios_base::failbit);

    // On an extraction failure, operator>> zero-initializes fundamental types
    // Uncomment the following line to make this operator do the same thing
    // pet = {};

    return in;
}

int main()
{
    std::cout << "Enter a pet: cat, dog, pig, or whale: ";
    Pet pet{};
    std::cin >> pet;

    if (std::cin) // if we found a match
        std::cout << "You chose: " << getPetName(pet) << '\n';
    else
    {
        std::cin.clear(); // reset the input stream to good
        std::cin.ignore(std::numeric_limits<std::streamsize>::max(), '\n');
        std::cout << "Your pet was not valid\n";
    }

    return 0;
}
```

## Intro to structs
### Basic syntax of struct
- A `struct` (short for structure) is a user-defined type that groups together variables/functions (known as **data members**) under one name.
	- The members of a `struct` can be of different types, allowing you to store related information as a single entity.
	- A `struct` is primarily used to represent data structures or objects that naturally group multiple attributes together.
- Basic syntax of a `struct`:

```C++
struct Student
{
	int id;
	std::string name = "John"; // default value
	char grade;
};
```

### Struct initialization
- Empty initialization of a `struct` will initialize its members with their default values.
	- If default values aren't set, then there will be garbage data.
- A `struct` can be initialized with a group of values inside the braces. For example:

```C++
Student john = {0, "John", 'A'};
```

- The number of values inside the braces has to be either equal or less than the number of members in `struct`. For example:

```C++
Student john = {0}; // Initializes only the id
```

- A `struct` can be initialized with another struct of the same type. For example:

```C++
Student a = {0, "John", 'A'};
Student b = a;
```

### Member selection and assignment
- Once a `struct` is initialized, its member can be accessed with the **member selection operator** `.`:

```C++
std::cout << john.id << std::endl;
std::cout << john.name << std::enl;
```

- Each member of a `struct` can be assigned a custom value:

```C++
john.id = 7;
john.grade = 'C';
```

- Similar to `struct` initialization, multiple members can be assigned their corresponding values:

```C++
john = {3, "John", 'B'};
```

### Member function for struct
- A member function can be defined in a `struct`. For example:

```C++
#include <iostream>
#include <string>

struct Student {
    int id;
    std::string name;
    char grade;

    // Member function to display student info
    void display() const {
        std::cout << "ID: " << id << ", Name: " << name << ", Grade: " << grade << "\n";
    }
};

int main() {
    Student student1 = {1, "Alice", 'B'};
    student1.display();  // Calls the display function to print student info

    return 0;
}
```

>[!important] Constant Member Function
>When a function has `const` placed after the closing parentheses in its declaration, it means that the function is a constant member function. A constant member function does not modify the state of the object it is called on. In other words, the function promises not to change any of the member variables (unless they are marked as `mutable`), and you can safely call this function on a `const` object.

### Aggregate data type
- In general programming, an **aggregate data type** (aka aggregate) is any type that can contain multiple data members.
	- Some types of aggregates allow members to have different types (e.g. structs), while others require that all members be of a single type (e.g. arrays).
- In C++, an <mark class="hltr-trippy">aggregate</mark> is a type that allows simple, straightforward initialization using brace-enclosed initializer lists.
	- Aggregates are types (typically structs or classes) that do not require special constructors or initializers and can be initialized directly with a set of values for their members.

>[!advanced]
>A class, struct, array, or union is considered an aggregate if it satisfies all of the following conditions:
>- No user-provided constructors.
>- No private or protected non-static data members.
>- No virtual functions.
>- No base classes.

- The simplest and most common way to initialize an aggregate is through aggregate initialization, which uses brace-enclosed lists to directly initialize each member in order. For example:

```C++
#include <iostream>

struct Point {
    int x;
    int y;
};

struct Rectangle {
    Point topLeft;
    Point bottomRight;
};

int main() {
    Point p1 = {10, 20};  // Aggregate initialization of Point
    Rectangle rect = {{0, 0}, {10, 20}};  // Nested aggregate initialization of Rectangle
    
    std::cout << "Rectangle: (" << rect.topLeft.x << ", " << rect.topLeft.y << "), ";
    std::cout << "(" << rect.bottomRight.x << ", " << rect.bottomRight.y << ")\n";
    
    return 0;
}
```

### Overloading << operator to print a struct

```C++
#include <iostream>

struct Employee
{
    int id {};
    int age {};
    double wage {};
};

std::ostream& operator<<(std::ostream& out, const Employee& e)
{
    out << e.id << ' ' << e.age << ' ' << e.wage;
    return out;
}

int main()
{
    Employee joe { 2, 28 }; // joe.wage will be value-initialized to 0.0
    std::cout << joe << '\n';

    return 0;
}
```

### Returning structs

```C++
#include <iostream>

struct Point3d
{
    double x { 0.0 };
    double y { 0.0 };
    double z { 0.0 };
};

Point3d getZeroPoint()
{
    // We can create a variable and return the variable (we'll improve this below)
    Point3d temp { 0.0, 0.0, 0.0 };
    return temp;
}

int main()
{
    Point3d zero{ getZeroPoint() };

    if (zero.x == 0.0 && zero.y == 0.0 && zero.z == 0.0)
        std::cout << "The point is zero\n";
    else
        std::cout << "The point is not zero\n";

    return 0;
}
```

- The return type can be deduced, so it is not necessary to create a temporary `struct` object to return it:

```C++
Point3d getZeroPoint()
{
	return {0.0, 0.0, 0.0};
}
```

### Struct inside another struct
- There are two ways to include other `struct` inside a `struct`:
	- Define a `struct` (in global scope), and use it as a member of another `struct`.
	- Define a `struct` inside another `struct`.
- Example of using a `struct` as a member of another `struct`:

```C++
#include <iostream>

struct Employee
{
    int id {};
    int age {};
    double wage {};
};

struct Company
{
    int numberOfEmployees {};
    Employee CEO {}; // Employee is a struct within the Company struct
};

int main()
{
    Company myCompany{ 7, { 1, 32, 55000.0 } }; // Nested initialization list to initialize Employee
    std::cout << myCompany.CEO.wage << '\n'; // print the CEO's wage

    return 0;
}
```

- Example of defining a `struct` inside a `struct`:

```C++
#include <iostream>

struct Company
{
    struct Employee // accessed via Company::Employee
    {
        int id{};
        int age{};
        double wage{};
    };

    int numberOfEmployees{};
    Employee CEO{}; // Employee is a struct within the Company struct
};

int main()
{
    Company myCompany{ 7, { 1, 32, 55000.0 } }; // Nested initialization list to initialize Employee
    std::cout << myCompany.CEO.wage << '\n'; // print the CEO's wage

    return 0;
}
```

### Struct size and data structure alignment
- Typically, the size of a `struct` is the sum of the size of all its members. However, there are times when the compiler will add gaps into structures for performance reasons - which is called **padding**.

### Member selection for pointers to structs

```C++
#include <iostream>

struct Employee
{
    int id{};
    int age{};
    double wage{};
};

int main()
{
    Employee joe{ 1, 34, 65000.0 };

    ++joe.age;
    joe.wage = 68000.0;

    Employee* ptr{ &joe };
    std::cout << (*ptr).id << '\n'; // Not great but works: First dereference ptr, then use member selection

    return 0;
}
```

- To make a cleaner syntax, C++ offers a <mark class="hltr-trippy">member selection from pointer operator</mark> `->` (aka arrow operator) that can be used to select members from a pointer to an object. For example:

```C++
#include <iostream>

struct Employee
{
    int id{};
    int age{};
    double wage{};
};

int main()
{
    Employee joe{ 1, 34, 65000.0 };

    ++joe.age;
    joe.wage = 68000.0;

    Employee* ptr{ &joe };
    std::cout << ptr->id << '\n'; // Better: use -> to select member from pointer to object

    return 0;
}
```

- In the example above, `ptr->id` is equivalent to `(*ptr).id`.

#### Chaining -> operator

```C++
#include <iostream>

struct Point
{
    double x {};
    double y {};
};

struct Triangle
{
    Point* a {};
    Point* b {};
    Point* c {};
};

int main()
{
    Point a {1,2};
    Point b {3,7};
    Point c {10,2};

    Triangle tr { &a, &b, &c };
    Triangle* ptr {&tr};

    // ptr is a pointer to a Triangle, which contains members that are pointers to a Point
    // To access member y of Point c of the Triangle pointed to by ptr, the following are equivalent:

    // access via operator.
    std::cout << (*(*ptr).c).y << '\n'; // ugly!

    // access via operator->
    std::cout << ptr -> c -> y << '\n'; // much nicer
}
```

#### Mixing pointers and non-pointers to members

```C++
#include <iostream>
#include <string>

struct Paw
{
    int claws{};
};

struct Animal
{
    std::string name{};
    Paw paw{};
};

int main()
{
    Animal puma{ "Puma", { 5 } };

    Animal* ptr{ &puma };

    // ptr is a pointer, use ->
    // paw is not a pointer, use .

    std::cout << (ptr->paw).claws << '\n';

    return 0;
}
```

### Templated struct
- It is possible to use templates with `struct` to make it **generic**.
	- This allows you to write a `struct` that works with different data types without duplicating code.
- Syntax for templated `struct`:

```C++
template <typename T>
struct MyStruct {
    T data;  // Member of type T

    void print() const {
        std::cout << data << std::endl;
    }
};
```

- In the example above, `T` is a template parameter representing the type that will be provided when an instance of the `struct` is created. The type `T` can be any type (e.g. `int`, `double`, etc.).
- Example of defining and using a templated `struct`:

```C++
#include <iostream>
#include <string>

template <typename T>
struct Box {
    T value;  // Generic value of type T

    void print() const {
        std::cout << "Value: " << value << std::endl;
    }
};

int main() {
    Box<int> intBox;      // Box that holds an int
    intBox.value = 42;
    intBox.print();

    Box<double> doubleBox;  // Box that holds a double
    doubleBox.value = 3.14;
    doubleBox.print();

    Box<std::string> strBox;  // Box that holds a string
    strBox.value = "Hello";
    strBox.print();

    return 0;
}
```

#### Templated struct with multiple parameters

```C++
#include <iostream>

template <typename T, typename U>
struct Pair {
    T first;
    U second;

    void print() const {
        std::cout << "First: " << first << ", Second: " << second << std::endl;
    }
};

int main() {
    Pair<int, double> p1 = {42, 3.14};  // A pair of int and double
    p1.print();

    Pair<std::string, int> p2 = {"Age", 30};  // A pair of string and int
    p2.print();

    return 0;
}
```


#### Templated struct partial specialization

```C++
#include <iostream>
#include <string>

template <typename T>
struct Box {
    T value;

    void print() const {
        std::cout << "Generic value: " << value << std::endl;
    }
};

// Specialization for std::string
template <>
struct Box<std::string> {
    std::string value;

    void print() const {
        std::cout << "Specialized string value: " << value << std::endl;
    }
};

int main() {
    Box<int> intBox = {42};       // Uses the generic template
    intBox.print();

    Box<std::string> strBox = {"Hello"};  // Uses the specialized version
    strBox.print();

    return 0;
}
```

#### Templated struct with default parameters

```C++
#include <iostream>

template <typename T = int>
struct Box {
    T value;

    void print() const {
        std::cout << "Value: " << value << std::endl;
    }
};

int main() {
    Box<> defaultBox;  // Uses the default type 'int'
    defaultBox.value = 100;
    defaultBox.print();

    Box<double> doubleBox;  // Uses 'double' explicitly
    doubleBox.value = 3.14;
    doubleBox.print();

    return 0;
}
```

#### Templated function with templated struct as parameter

```C++
#include <iostream>

template <typename T>
struct Pair
{
    T first{};
    T second{};
};

template <typename T>
constexpr T max(Pair<T> p)
{
    return (p.first < p.second ? p.second : p.first);
}

int main()
{
    Pair<int> p1{ 5, 6 };
    std::cout << max<int>(p1) << " is larger\n"; // explicit call to max<int>

    Pair<double> p2{ 1.2, 3.4 };
    std::cout << max(p2) << " is larger\n"; // call to max<double> using template argument deduction (prefer this)

    return 0;
}
```

With multiple template types:

```C++
#include <iostream>

template <typename T, typename U>
struct Pair
{
    T first{};
    U second{};
};

template <typename T, typename U>
void print(Pair<T, U> p)
{
    std::cout << '[' << p.first << ", " << p.second << ']';
}

int main()
{
    Pair<int, double> p1{ 1, 2.3 }; // a pair holding an int and a double
    Pair<double, int> p2{ 4.5, 6 }; // a pair holding a double and an int
    Pair<int, int> p3{ 7, 8 };      // a pair holding two ints

    print(p2);

    return 0;
}
```

#### Using templated struct in multiple files

pair.h
```C++
#ifndef PAIR_H
#define PAIR_H

template <typename T>
struct Pair
{
    T first{};
    T second{};
};

template <typename T>
constexpr T max(Pair<T> p)
{
    return (p.first < p.second ? p.second : p.first);
}

#endif
```

foo.cpp
```C++
#include "pair.h"
#include <iostream>

void foo()
{
    Pair<int> p1{ 1, 2 };
    std::cout << max(p1) << " is larger\n";
}
```

main.cpp
```C++
#include "pair.h"
#include <iostream>

void foo(); // forward declaration for function foo()

int main()
{
    Pair<double> p2 { 3.4, 5.6 };
    std::cout << max(p2) << " is larger\n";

    foo();

    return 0;
}
```

#### Using alias for templated struct
- An alias template is a convenient way to create a new name (alias) for a template type or a more complex type.
	- This can simplify code by allowing you to refer to template specializations with shorter or more descriptive names, especially when dealing with complex template types.
- Alias template are defined using the `using` keyword, followed by a name for the alias and the type expression that the alias represents.

```C++
#include <iostream>

template <typename T>
struct Pair
{
    T first{};
    T second{};
};

// Here's our alias template
// Alias templates must be defined in global scope
template <typename T>
using Coord = Pair<T>; // Coord is an alias for Pair<T>

// Our print function template needs to know that Coord's template parameter T is a type template parameter
template <typename T>
void print(const Coord<T>& c)
{
    std::cout << c.first << ' ' << c.second << '\n';
}

int main()
{
    Coord<int> p1 { 1, 2 }; // Pre C++-20: We must explicitly specify all type template argument
    Coord p2 { 1, 2 };      // In C++20, we can use alias template deduction to deduce the template arguments in cases where CTAD works

    std::cout << p1.first << ' ' << p1.second << '\n';
    print(p2);

    return 0;
}
```

## Intro to constructors
- A <mark class="hltr-trippy">constructor</mark> is a special member function that is called automatically when an object of a `class` or `struct` is created. Its primary purpose is to initialize the object's members with specific values or default values.
	- Constructors have the same name as the `class` or `struct` and do not have a return type.
- Syntax of using constructor in `struct`:

```C++
#include <iostream>

struct Person {
    std::string name;
    int age;

    // Constructor
    Person(const std::string& name, int age) : name(name), age(age) {
        std::cout << "Constructor called for " << name << "\n";
    }
};

int main() {
    Person p("Alice", 30);  // Constructor initializes `name` and `age`
    std::cout << "Name: " << p.name << ", Age: " << p.age << std::endl;
}
```

- In the example above, the constructor `Person(const std::string& name, int age)` initializes `name` and `age`.
	- The <mark class="hltr-trippy">member initializer list</mark> (`: name(name), age(age)`) initializes `name` and `age` directly, which is more efficient than assignment in the constructor body.
	- When `Person p("Alice", 30);` is called, this invokes the constructor, initializing `name` to `Alice` and `age` to `30`.

>[!important]
>Note that with a constructor, `struct` is initialized using paratheses (e.g. `Person p("Alice", 30);`) as opposed to braces (e.g. `Person p = {"Alice", 30};`). This shows that the constructor is a function whose main purpose is to initialize the object's members.

>[!important]
>The members in a member initializer list are always initialized in the order in which they are defined inside the struct or class.

### Types of constructors
#### Default constructor
- <mark class="hltr-trippy">Default constructor</mark> initializes members to default values, or leaves them uninitialized.
	- An **implicit default constructor** is created if a default constructor is not provided.

```C++
struct Person
{
	std::string name;
	int age;

	Person() : name("Unknown"), age(0) {}
};
```

#### Parameterized constructor
- <mark class="hltr-trippy">Parameterized constructor</mark> initializes members with values passed as arguments.

```C++
struct Person
{
	std::string name;
	int age;

	Person(const std::string& name, int age) : name(name), age(age) {}
};
```

#### Copy constructor
- <mark class="hltr-trippy">Copy constructor</mark> moves resources from a temporary object to a new one, which is efficient for objects holding dynamically allocated resources.
	- An **implicit copy constructor** is created if a copy constructor is not provided.

```C++
struct Person
{
	std::string name;
	int age;

	Person(const Person& other) : name(other.name), age(other.age) {}
};
```

>[!warning]
>A copy constructor should not do anything other than copy an object. This is because the compiler may optimize the copy constructor out in certain cases. If you are relying on the copy constructor for some behavior other than just copying, that behavior may or may not occur.

>[!important]
>A copy constructor is essential for classes that:
>- Manage dynamically allocated resources, requiring deep copies.
>- Are passed or returned by value.
>- Are used in standard library containers that might need to copy objecdts.
>- Should explicitly forbid copying to enforce unique ownership.

### Parameterized constructor with default arguments

```C++
struct Foo {
	int m_x;
	int m_y;

	Foo(int x=0, int y=0) : m_x(x), m_y(y) {}
};
```

>[!warning]
>If default arguments are supplied, the parameterized constructor will act as a default constructor. If there is another default constructor (meaning there are two), default initialization will become ambiguous and result in a compile error.

### Multiple constructors

```C++
#include <iostream>

struct Rectangle {
    int width, height;

    // Default constructor
    Rectangle() : width(1), height(1) {}

    // Parameterized constructor
    Rectangle(int w, int h) : width(w), height(h) {}

    // Copy constructor
    Rectangle(const Rectangle& other) : width(other.width), height(other.height) {}
};

int main() {
    Rectangle rect1;            // Calls default constructor
    Rectangle rect2(5, 10);      // Calls parameterized constructor
    Rectangle rect3(rect2);      // Calls copy constructor

    std::cout << "rect1: " << rect1.width << "x" << rect1.height << std::endl;
    std::cout << "rect2: " << rect2.width << "x" << rect2.height << std::endl;
    std::cout << "rect3: " << rect3.width << "x" << rect3.height << std::endl;
}
```

### Using constructor with templates

```C++
template <typename T, typename U>
struct Rectangle {
	T width;
	U height;

	Rectangle(T w, U h) : width(w), height(h) {}
};

int main() {
	Rectangle<int, int> rect1(2, 4);
	Rectangle<double, double> rect2(3.1, 7.4);
	Rectangle<int, float> rect3(5, 1.1f);
	
	std::cout << rect1.width << ',' << rect1.height << std::endl;
	std::cout << rect2.width << ',' << rect2.height << std::endl;
	std::cout << rect3.width << ',' << rect3.height << std::endl;
}
```

### Delegating constructors
- Constructors are allowed to delegate (transfer responsibility for) initialization to another constructor from the same struct/class type.
	- This process is called <mark class="hltr-trippy">constructor chaining</mark>, and such constructors are called <mark class="hltr-trippy">delegating constructors</mark>.
- For example:

```C++
#include <iostream>

struct Employee {
	std::string m_name;
	int m_id;

	Employee(std::string_view name) : Employee(name, 0) {
		std::cout << "delegated" << std::endl;
	}
	Employee(std::string_view name, int id) : m_name(name), m_id(id) {
		std::cout << m_name << ' ' << m_id << std::endl;
	}
};

int main() {
	Employee john("John", 5);
	Employee jane("Jane");

	return 0;
}
```

```console
John 5
Jane 0
delegated
```

>[!warning]
>A constructor that delegates to another constructor is not allowed to do any member initialization itself. In other words, a constructor can delegate or initialize, but not both.

>[!warning]
>It is possible for one constructor to delegate to another constructor, which delegates back to the first constructor. This forms an infinite loop, and will cause the program to run out of memory and crash. Make sure that all of the constructors resolve to a non-delegating constructor.

### Braces for initialization
- Braces `{}` invoke **list initialization** (uniform initialization) and are generally safer as they prevent narrowing conversions (e.g. initializing an `int` from a `double`).
- When used in a member initializer list, braces offer more consistent behavior.
- For example:

```C++
struct Foo {
	int m_x;
	int m_y;

	Foo(int x, int y) : m_x{x}, m_y{y} {}
};

Foo obj1{10, 12}; // list initialization
Foo obj2(7, 11); // direct initialization still works
```

## Class template argument deduction (C++17)

>[!important]
>Templates used with `struct` are often called **class templates**. Though, `class` and `struct` are not the same thing.

- <mark class="hltr-trippy">Class template argument deduction (CTAD)</mark> is a feature that lets the compiler automatically deduce template arguments for class templates based on the arguments passed to the constructor.
	- This was introduced in C++17.
- For example:

```C++
#include <iostream>

template <typename T1, typename T2>
struct Pair {
    T1 first;
    T2 second;

    Pair(T1 a, T2 b) : first(a), second(b) {}
};

int main() {
    Pair<int, double> p1(10, 3.14);  // Explicit template arguments <int, double>
    std::cout << "Pair: " << p1.first << ", " << p1.second << std::endl;

	Pair p2(3, 5.5f); // Class template argument deduction to <int, float>
	std::cout << "Pair: " << p2.first << ", " << p2.second << std::endl;
}
```

- In C++14 and below, `Pair p2(3, 5.5f);` would cause a compile error. Template argument types must be explicitly stated (e.g. `Pair<int, float> p2(3, 5.5f)`).

>[!warning] CTAD can't be used to initialize a (non-static) member of another `struct`.
>All template arguments must be explicitly specified.

>[!warning] CTAD doesn't work with function parameters.
>All template arguments must be explicitly specified.

### Deduction guides (C++17)
- <mark class="hltr-trippy">Deduction guides</mark> are mechanisms that help the compiler deduce template arguments when creating an instance of a class template (or a templated struct).
	- Deduction guides reduce the need to explicitly specify template arguments in certain situations, making code more concise and readable.
- A deduction guide provides a mapping between constructor parameters and the template arguments. The guide tells the compiler which template arguments to use based on the arguments passed to the constructor, and this affects how instances of the templated struct or class are created.

>[!important]
>CTAD can deduce template arguments without deduction guides in some cases, specifically when the class template has a constructor that enables the compiler to infer types from its parameters.
>
>However, CTAD may require explicit deduction guides in more complex situations, such as:
>- **Overloaded constructors** : if there are multiple constructors, the compiler might not know which one to use, and deduction guides help clarify this.
>- **Multiple template parameters** : if the types of multiple parameters don't correspond directly to the template parameters, the compiler may need additional guidance.
>- **Non-matching parameter types** : when the constructor parameters do not directly match the template arguments, deduction guides clarify the intended types.

- Syntax of deduction guides:

```C++
template <typename T1, typename T2>
struct Pair {
	T1 first;
	T2 second;

	Pair(T1 a, T2 b) : first(a), second(b) {}
};

// Deduction guide for Pair<T1, T2>
template <typename T1, typename T2>
Pair(T1, T2) -> Pair<T1, T2>;
```

>[!important]
>C++20 added the ability for the compiler to automatically generate deduction guides for aggregates (structs), so deduction guides should only need to be provided for C++17 compatibility.

#### When CTAD require deduction guides
- Multiple constructors with ambiguity:

```C++
#include <iostream>
#include <string>

template <typename T>
struct ValueWrapper {
    T value;

    // Constructor for a direct value of type T
    ValueWrapper(T v) : value(v) {}

    // Constructor for an int that converts to type T (int to string)
    ValueWrapper(int i) : value(std::to_string(i)) {}
};

// Deduction guide to clarify T when an int is passed
ValueWrapper(int) -> ValueWrapper<std::string>;

int main() {
    ValueWrapper v1("Hello");    // CTAD deduces ValueWrapper<const char*>
    ValueWrapper v2(42);         // Deduction guide deduces ValueWrapper<std::string>

    std::cout << "v1: " << v1.value << "\nv2: " << v2.value << std::endl;
}
```

- Default or non-template parameters:

```C++
#include <iostream>
#include <string>

template <typename T = int>
struct Container {
    T value;

    Container(T v) : value(v) {}      // Constructor taking a T
    Container() : value(T{}) {}       // Default constructor
};

// Deduction guide to handle the case with no parameters
Container() -> Container<int>;        // Deduces Container<int> when no argument is provided

int main() {
    Container c1(3.14);  // Deduces Container<double>
    Container c2;        // Uses deduction guide to deduce Container<int>

    std::cout << "c1: " << c1.value << "\nc2: " << c2.value << std::endl;
}
```

- Non-template parameters in constructor:

```C++
#include <iostream>
#include <utility>

template <typename T1, typename T2>
struct Pair {
    T1 first;
    T2 second;

    // Constructor taking a std::pair
    Pair(std::pair<T1, T2> p) : first(p.first), second(p.second) {}
};

// Deduction guide for std::pair initialization
template <typename T1, typename T2>
Pair(std::pair<T1, T2>) -> Pair<T1, T2>;

int main() {
    std::pair<int, double> p = {10, 3.14};
    Pair pair(p);  // Deduction guide deduces Pair<int, double>

    std::cout << "First: " << pair.first << ", Second: " << pair.second << std::endl;
}
```

- Conversions with mixed types:

```C++
#include <iostream>
#include <vector>

template <typename T>
struct Matrix {
    int rows;
    int cols;
    std::vector<T> data;

    // Constructor that takes dimensions and a default value
    Matrix(int r, int c, T defaultValue) : rows(r), cols(c), data(r * c, defaultValue) {}
};

// Deduction guide for Matrix dimensions and value type
Matrix(int, int, double) -> Matrix<double>;

int main() {
    Matrix m(2, 3, 1.0);  // Deduction guide deduces Matrix<double>

    std::cout << "Matrix rows: " << m.rows << ", cols: " << m.cols << std::endl;
}
```

## Intro to object-oriented programming
- <mark class="hltr-trippy">Object-oriented programming (OOP)</mark> is a programming paradigm based on the concept of **objects**, which represent real-world entities, combining both **data** (attributes or properties) and **behavior** (methods or functions) into a single unit.
	- OOP makes it easier to model complex systems, promote code reuse, and manage code structure through **encapsulation**, **modularity**, and **abstraction**.
- Key concepts of OOP includes:
	- Classes and objects
	- Encapsulation
	- Abstraction
	- Inheritance
	- Polymorphism

### Classes and objects
- A <mark class="hltr-trippy">class</mark> is a blueprint for creating objects, which defines a set of attributes and behaviors that the objects (instantiated from the class) will have.
- An <mark class="hltr-trippy">object</mark> is an instance of a class, representing a specific entity that has attributes (data) and methods (behaviors).
	- Each object can have unique values for its attributes but shares the same structure and behavior as other objects of the same class.

### Encapsulation
- <mark class="hltr-trippy">Encapsulation</mark> is the building of data (attributes) and methods (functions) that operate on the data within a single unit (class).
	- It restricts direct access to certain components of an object to protect its state and prevent unintended interference or misuse.
- An <mark class="hltr-trippy">access modifier</mark> is a modifier given to a data or method that governs how they are accessed by the user.
	- In C++, access modifiers are `public`, `protected`, and `private`. These will be discussed later.

### Abstraction
- <mark class="hltr-trippy">Abstraction</mark> means representing only the essential features and hiding the complex implementation details from the user.
	- This allows to interact with objects at a high level without needing to understand how the object is implemented.
- Abstraction is often achieved through <mark class="hltr-trippy">abstract classes</mark> and <mark class="hltr-trippy">interfaces</mark> (or **pure virtual functions**), which define what methods an object should have but not how those methods should be implemented.

### Inheritance
- <mark class="hltr-trippy">Inheritance</mark> is a mechanism where a new class (called a **derived class** or **subclass**) inherits attributes and methods from an existing class (known as the **base class** or **superclass**).
	- The derived class can extend or modify the base class's behavior, promoting code reuse and creating a hierarchical relationship between classes.
- Inheritance enables polymorphism, allowing for flexibility in function calls and object handling across related classes.

### Polymorphism
- <mark class="hltr-trippy">Polymorphism</mark> allows objects of different classes to be treated as objects of a common base class.
	- It means "many forms" and enables a single function to behave differently based on the object that invokes it.
- <mark class="hltr-trippy">Compile-time polymorphism</mark> : achieved through function overloading and operator overloading, where the function call is resolved at compile time.
- <mark class="hltr-trippy">Runtime polymorphism</mark> : achieved through virtual functions and method overriding, where a base class pointer or reference can call derived class methods, and the function call is resolved at runtime.


## Intro to classes
### Invariants
- An <mark class="hltr-trippy">invariant</mark> is a condition or property that remains true throughout the execution of a program or within a specific scope, such as during the lifetime of a function, loop, or an object.
	- Invariants are essential in ensuring correctness and stability in software, as they provide guaranteed conditions that developers can rely on, helping prevent unexpected behavior.
- Types of (local) invariants:
	- <mark class="hltr-trippy">Loop invariants</mark> : conditions that remain true before and after each iteration of a loop.
	- <mark class="hltr-trippy">Class invariants</mark> : properties that hold true for an object in a valid state, typically maintained between method calls.
- <mark class="hltr-trippy">Global invariant</mark> is a condition or property that holds true for an entire system, application, or program throughout its execution.
	- It applies at a broader scope than local invariants (e.g. class or loop invariants) and governs the overall integrity of the system as a whole.
	- Includes data relationships and constraints.
- Related to invariants:
	- <mark class="hltr-trippy">Preconditions</mark> : conditions that must be true *before* a function or operation is executed.
	- <mark class="hltr-trippy">Postconditions</mark> : conditions that must be true *after* a function or operation is executed.
- Preconditions and postconditions are NOT invariants, but they can help enforce invariants:
	- Preconditions ensure that a function receives valid input, helping maintain the invariant state of an object.
	- Postconditions ensure that the function produces valid output or leaves the system in a valid state, preserving invariants.

#### Example : loop invariant
- Loop invariant :

```C++
#include <vector>
#include <iostream>

int findMin(const std::vector<int>& numbers) {
    int min = numbers[0];  // Initial invariant: min is at least one element in the array
    for (int i = 1; i < numbers.size(); ++i) {
        if (numbers[i] < min) {
            min = numbers[i];  // Invariant: min is always the smallest seen so far
        }
    }
    return min;  // Final invariant: min is the smallest in the entire array
}
```

- Class invariant :

```C++
#include <stdexcept>

class Rectangle {
    int width;
    int height;

public:
    Rectangle(int w, int h) : width(w), height(h) {
        if (width <= 0 || height <= 0) {
            throw std::invalid_argument("Width and height must be positive");
        }
    }

    int area() const {
        // Invariant: width and height should always be positive
        return width * height;
    }
};
```

#### Complex class invariant
- Class invariants become complex when the members (of a `struct`) must have correlated values:

```C++
#include <string>

struct Employee
{
    std::string name { };
    char firstInitial { }; // should always hold first character of `name` (or `0`)
};
```

- In the example above, the value of `firstInitial` must always match with the first character of `name`.
- Correlations between members aren't always obvious to developers, so it is difficult to maintain such complex class invariants. This is the case, even if functions are used to update members, as it relies on the user to be aware and use these functions.
	- `struct` just don't have the mechanics required to solve this problem in an elegant way.

>[!important]
>`struct` is able to maintain class invariants, by using constructors to make sure its members are initialized with valid values. However, it is difficult to maintain the invariants throughout the lifetime of the object because its members are public; a user can easily access them and modify their values to an invalid state.

### Classes
- A <mark class="hltr-trippy">class</mark> is a blueprint for creating objects, providing a way to define the structure (attributes) and behaviors (methods) of an object.
	- It groups related data and functions together, encapsulating them as a single entity.
	- It is a natural way to define and enforce **invariants** for data that belongs to objects. A well-designed class uses **encapsulation** to control how its data is accessed and modified, helping to maintain these invariants.
	- `class` keyword is used to define a class type.

>[!important] A `class` is very similar to `struct`, with only difference the use of encapsulation in `class`.

- Key aspects of a `class`:
	- Data members (attributes)
	- Member functions (methods)
	- Access specifiers
	- Constructors
	- Destructors
- <mark class="hltr-trippy">Data members (attributes)</mark> are variables within `class` that store the state or properties of an object (created from the `class`).
- <mark class="hltr-trippy">Member functions (methods)</mark> are functions within `class` that define behaviors or actions an object (created from the `class`) can perform.
- <mark class="hltr-trippy">Access specifiers</mark> control visibility and access to the members of the `class`.
	- `public` : accessible from outside the class.
	- `protected` : accessible within the class and by derived classes.
	- `private` : accessible only within the class itself.
- <mark class="hltr-trippy">Constructor</mark> is a special function that is called when an object is created/instantiated from a `class`. It initializes the object's data members.
- <mark class="hltr-trippy">Destructor</mark> is a special function called when an object is destroyed. It's used for cleanup, like releasing resources if needed.
- Example of a simple class `Car`:

```C++
#include <iostream>
#include <string>

class Car {
private:
    std::string color;
    std::string make;
    int year;

public:
    // Constructor
    Car(const std::string& carColor, const std::string& carMake, int carYear)
        : color(carColor), make(carMake), year(carYear) {}

    // Member function to display car details
    void displayInfo() const {
        std::cout << "Car: " << make << ", " << color << ", Year: " << year << std::endl;
    }
};

int main() {
    // Creating an object of Car
    Car myCar("Red", "Toyota", 2020);
    myCar.displayInfo();  // Output: Car: Toyota, Red, Year: 2020
    return 0;
}
```

- Explanation of the example above:
	- **Class definition** : `class Car` defines the structure and behavior of a `Car`.
	- **Data members** : `color`, `make`, and `year` are private attributes representing properties of a car.
	- **Constructor** : initializes the `Car` object's data members.
	- **Member function** : `displayInfo()` is a public function that outputs the car's details.

### How classes use invariants
1. <mark class="hltr-trippy">Encapsulation and access control</mark>
	- Classes hide their internal data using `private` or `protected` access specifiers, exposing only necessary operations through `public` methods.
	- This prevents external code from directly modifying internal data, allowing the class to control how its members are changed and to enforce invariants.
2. <mark class="hltr-trippy">Constructors and invariant setup</mark>
	- When an object is created, the constructor ensures that the initial state is valid and adheres to the class invariants. If the required conditions aren't met, the constructor can throw an exception to prevent the creation of an invalid object.
3. <mark class="hltr-trippy">Member functions and invariant maintenance</mark>
	- Member functions are used to modify the object's state, but these functions are designed to ensure that any change still satisfies the invariants.
	- Methods can include checks or restrictions to prevent operations that would lead to invalid states.
4. <mark class="hltr-trippy">Destructors and invariant teardown</mark>
	- The destructor ensures that any required cleanup adheres to invariants, especially for resources managed by the class.

#### Example: class with an invariant
- Consider a `BankAccount` class that has a balance invariant: the balance should never be negative. For example:

```C++
#include <stdexcept>
#include <string>

class BankAccount {
private:
    double balance;      // invariant: balance >= 0
    std::string owner;

public:
    // Constructor sets up invariant: balance >= 0
    BankAccount(double initialBalance, const std::string& ownerName)
        : balance(initialBalance), owner(ownerName) {
        if (balance < 0) {
            throw std::invalid_argument("Initial balance cannot be negative");
        }
    }

    // Deposit method enforces invariant by ensuring balance remains non-negative
    void deposit(double amount) {
        if (amount < 0) {
            throw std::invalid_argument("Cannot deposit a negative amount");
        }
        balance += amount;
    }

    // Withdraw method ensures balance never goes below 0
    void withdraw(double amount) {
        if (amount < 0) {
            throw std::invalid_argument("Cannot withdraw a negative amount");
        }
        if (balance - amount < 0) {
            throw std::runtime_error("Insufficient funds for withdrawal");
        }
        balance -= amount;
    }

    double getBalance() const {
        return balance;
    }
};
```

### Const class objects
- Same as how objects of a fundamental data type (`int`, `double`, etc.) can be made constant via the `const` keyword, class type objects (`struct` and `class`) can also be made constant using the `const` keyword. For example:

```C++
struct Date
{
    int year {};
    int month {};
    int day {};
};

int main()
{
    const Date today { 2020, 10, 14 }; // const class type object

    return 0;
}
```

- Modifying the data members of a const object is NOT allowed:

```C++
struct Date
{
    int year {};
    int month {};
    int day {};

    void incrementDay()
    {
        ++day;
    }
};

int main()
{
    const Date today { 2020, 10, 14 }; // const

    today.day += 1;        // compile error: can't modify member of const object
    today.incrementDay();  // compile error: can't call member function that modifies member of const object

    return 0;
}
```

### Const member functions
- Const objects may not call non-const member functions:

```C++
#include <iostream>

struct Date
{
    int year {};
    int month {};
    int day {};

    void print()
    {
        std::cout << year << '/' << month << '/' << day;
    }
};

int main()
{
    const Date today { 2020, 10, 14 }; // const

    today.print();  // compile error: can't call non-const member function

    return 0;
}
```

- A <mark class="hltr-trippy">const member function</mark> is a member function that guarantees it will not modify the object or call any non-const member functions.
	- A const object may call const member functions without any issues.
	- A const member function is made by appending `const` keyword in between the parameter list and the function body.
- For example:

```C++
#include <iostream>

struct Date
{
    int year {};
    int month {};
    int day {};

    void print() const // now a const member function
    {
        std::cout << year << '/' << month << '/' << day;
    }
};

int main()
{
    const Date today { 2020, 10, 14 }; // const

    today.print();  // ok: const object can call const member function

    return 0;
}
```

>[!warning] Do not make constructors `const`.

- A const member function that attempts to change a member variable or call a non-const member function will cause a compile error to occur. For example:

```C++
struct Date
{
    int year {};
    int month {};
    int day {};

    void incrementDay() const // made const
    {
        ++day; // compile error: const function can't modify member
    }
};

int main()
{
    const Date today { 2020, 10, 14 }; // const

    today.incrementDay();

    return 0;
}
```

>[!important] Const member functions may be called on non-const objects.
>If a member function does not modify the state of the object, then it is generally a good idea to have it as a const member function so that it can be called on both const and non-const objects.
>
>Consider a case where a function (e.g. `foo()`) receives a non-const class object (e.g. `Bar`) by a pass-by-const-reference. If there exists a non-const member function side the non-const class object, which is then called in the function, it will result in a compile error.

>[!important] It is possible to overload a member function to have a const and non-const version of the same function.


### Access specifiers
- Each member of a `class` type has a property called an <mark class="hltr-trippy">access level</mark> that determines who can access that member.
- C++ has three different access levels: public, private, and protected.
	- A member with a public access level is called a <mark class="hltr-trippy">public member</mark>. The same is for the rest.
- Members in a `class` type are `private` by default.
- Access level is explicitly set on a member by using an access specifier, such as `public`, `private`, and `protected`. For example:

```C++
class Date
{
// Any members defined here would default to private

public: // here's our public access specifier

    void print() const // public due to above public: specifier
    {
        // members can access other private members
        std::cout << m_year << '/' << m_month << '/' << m_day;
    }

private: // here's our private access specifier

    int m_year { 2020 };  // private due to above private: specifier
    int m_month { 14 }; // private due to above private: specifier
    int m_day { 10 };   // private due to above private: specifier
};

int main()
{
    Date d{};
    d.print();  // okay, main() allowed to access public members

    return 0;
}
```

#### Access level chart

| Access level | Access specifier | Member access | Derived class access | Public access |
|--------------|------------------|---------------|----------------------|---------------|
| Public       | `public:`        | yes           | yes                  | yes           |
| Protected    | `protected:`     | yes           | yes                  | no            |
| Private      | `private:`       | yes           | no                   | no            |

### Derived class
- A <mark class="hltr-trippy">derived class</mark> is a class that **inherits** from another class (known as the **base class** or **parent class**).
	- The derived class has access to the **public** and **protected** members of the base class.
	- It can also add its own attributes and methods or override base class methods.
- <mark class="hltr-trippy">Inheritance</mark> allows you to create a new class with features of an existing class, making it useful for reusing code and creating a hierarchy of related classes.
- Syntax for derived class `Dog`, given base class `Animal`:

```C++
class Dog : public animal {
	// members
};
```

#### Key concepts of derived classes
- **Inheritance**
	- The derived class inherits all non-private members from the base class.
	- This allows the derived class to reuse code from the base class while adding or modifying functionality.
- **Access specifiers**
	- The access specifier used in inheritance affects how the base class members are accessible in the derived class.
	- Commonly, `public` inheritance is used, meaning public and protected members of the base class retain their visibility in the derived class.
- **Overriding**
	- Derived classes can redefine (override) virtual methods of the base class to provide specialized behavior. This is called runtime polymorphism and is achieved through virtual functions.
- **Adding new members**
	- The derived class can introduce new data members and member functions that are unique to it, which extends the behavior of the base class.

#### Virtual functions and overriding
- A virtual function is a function in a base class that is declared with the keyword `virtual`.
	- It allows derived classes to override the function with their own implementation.
	- Virtual functions enable runtime polymorphism, meaning that the appropriate function implementation is chosen based on the actual object type at runtime rather than at compile time.
- Declaring a virtual function:

```C++
class Base {
public:
    virtual void display() const {
        std::cout << "Base class display" << std::endl;
    }
};
```

- Overriding a base class method in a derived class:

```C++
class Dervied : class Base {
public:
	void display() const {
		std::cout << "Derived class display" << std::endl;
	}
};
```

- C++11 and above, `override` keyword can be used to indicate that the function is intended to override a base class version (but it is not necessary):

```C++
class Dervied : class Base {
public:
	void display() const override {
		std::cout << "Derived class display" << std::endl;
	}
};
```

>[!warning]
>If a method in the base class is **NOT** declared as `virtual`, overriding does not work in the derived class in the same way. Without the `virtual` keyword in the base class, the function in the derived class is treated as a **separate function**, not an override, and **runtime polymorphism is not enabled**.
>
>Though it may seem like it works just fine without the `virtual` keyword, the base class method is just hiding, and there are cases where the base class method is exposed via base pointers or references (more on this later).

- It is possible to call a base class's virtual method inside a derived class using a [[#Scope resolution operator]] `::` to explicitly specify the base class and method to call.
	- Additionally, base class can be called from derived class object using member access operator `.` and then the base class's virtual method can be accessed with the scope resolution operator `::`.
- For example:

```C++
#include <iostream>

class Base {
public:
    virtual void show() const {
        std::cout << "Base class show method" << std::endl;
    }
};

class Derived : public Base {
public:
    void show() const override {
        std::cout << "Derived class show method" << std::endl;

        // Call the base class's show() method
        Base::show();
    }
};

int main() {
    Derived d;
    d.show(); // Calls Derived's show() and then Base's show() within Derived
    d.Base::show(); // Calls Base's show() directly from the Derived
    return 0;
}
```

#### Example of derived class

```C++
#include <iostream>
#include <string>

class Animal {  // Base class
public:
    void eat() const {  // Common behavior
        std::cout << "Animal is eating." << std::endl;
    }

    virtual void speak() const {  // Virtual function for polymorphism
        std::cout << "Animal sound." << std::endl;
    }
};

class Dog : public Animal {  // Derived class using public inheritance
public:
    void speak() const override {  // Override the speak method
        std::cout << "Woof!" << std::endl;
    }

    void fetch() const {  // Unique behavior for Dog
        std::cout << "Dog is fetching the ball." << std::endl;
    }
};

int main() {
    Animal genericAnimal;
    Dog myDog;

    genericAnimal.eat();     // Output: Animal is eating.
    genericAnimal.speak();   // Output: Animal sound.
    
    myDog.eat();             // Output: Animal is eating.
    myDog.speak();           // Output: Woof!
    myDog.fetch();           // Output: Dog is fetching the ball.

    return 0;
}
```

- `Animal` is a base class that provides common behaviors (`eat`) and a virtual method (`speak`) for derived classes to override.
- `Dog` is a derived class that inherits from `Animal` and overrides `speak` with a specialized implementation. It also adds a new behavior, `fetch`.
- Both `genericAnimal` and `myDog` can use the `eat` function (as provided from the base class `Animal`), while `myDog` can also use `fetch` and has its own version of `speak`.

### Access functions: getters and setters
- An <mark class="hltr-trippy">access function</mark> is a trivial public member function whose job is to retrieve or change the value of a private member variable.
- There are two access functions : getters and setters.
- Getters (aka accessors) are public member functions that return the value of a private member variable.
- Setters (aka mutators) are public member functions that set the value of a private member variable.
- Example of using access functions:

```C++
#include <iostream>

class Date
{
private:
    int m_year { 2020 };
    int m_month { 10 };
    int m_day { 14 };

public:
    void print()
    {
        std::cout << m_year << '/' << m_month << '/' << m_day << '\n';
    }

    int getYear() const { return m_year; }        // getter for year
    void setYear(int year) { m_year = year; }     // setter for year

    int getMonth() const  { return m_month; }     // getter for month
    void setMonth(int month) { m_month = month; } // setter for month

    int getDay() const { return m_day; }          // getter for day
    void setDay(int day) { m_day = day; }         // setter for day
};

int main()
{
    Date d{};
    d.setYear(2021);
    std::cout << "The year is: " << d.getYear() << '\n';

    return 0;
}
```

```console
The year is: 2021
```

>[!warning]
>There is a lot of debate on whether getters and setters are truly necessary, as it can be seen that it is just adding extra steps to access the data members. The benefits of encapsulation will be discussed later on.

#### Getter: return by reference

```C++
#include <iostream>
#include <string>

class Employee
{
	std::string m_name{};

public:
	void setName(std::string_view name) { m_name = name; }
	const std::string& getName() const { return m_name; } //  getter returns by const reference
};

int main()
{
	Employee joe{}; // joe exists until end of function
	joe.setName("Joe");

	std::cout << joe.getName(); // returns joe.m_name by reference

	return 0;
}
```

- In general, the type of the reference and the type of the data member should be the same to avoid unnecessary conversions.
	- If anything, `auto&` is a useful way to ensure that no conversions occur.

>[!warning]
>If a class is made temporarily (e.g. being created inside an initializer), making a reference to the reference returned by a getter would result in a dangling reference.

>[!warning] Do not return non-const references to private data members
>Always use const reference. Using non-const reference allows the caller to have direct access, which defeats the purpose of having access functions.

### The benefits of encapsulation
- <mark class="hltr-trippy">Encapsulation</mark> is a fundamental principle of OOP which involves bundling data (attributes) and methods (functions) that operate on the data within a single unit, typically a class, and restricting direct access to some of the components.
- The <mark class="hltr-trippy">interface</mark> of a class type (aka class interface) defines how a user of the class type will interact with objects of the class type.
	- Because only public members can be accessed from outside of the class type, the public members of a class type forms its interface.
	- An interface is an implicit contract between the author of a class and the user of a class. If an existing interface is ever changed, any code that uses it may break. Therefore, it is important to ensure the interfaces for our class types are well-designed and stable (doesn't change much).
- The <mark class="hltr-trippy">implementation</mark> of a class type consists of the code that actually makes the class behave as intended.
	- This includes both the member variables that store data, and the bodies of the member functions that contain the program logic and manipulate the member variables.
- <mark class="hltr-trippy">Data hiding</mark> (aka **information hiding** or **data abstraction**) is a technique used to enforce the separation of interface and implementation by hiding (making inaccessible) the implementation of a program-defined data type from users.
	- Data hiding helps maintaining invariants by 1) preventing direct access to its private members, 2) providing access functions that modifies the private members only in a valid way, and 3) making necessary changes to members that are correlated with the private members.
- For example:

```C++
#include <iostream>
#include <string>
#include <string_view>

class Employee // members are private by default
{
    std::string m_name{};
    char m_firstInitial{};

public:
    void setName(std::string_view name)
    {
        m_name = name;
        m_firstInitial = name.front(); // use std::string::front() to get first letter of `name`
    }

    void print() const
    {
        std::cout << "Employee " << m_name << " has first initial " << m_firstInitial << '\n';
    }
};

int main()
{
    Employee e{};
    e.setName("John");
    e.print();

    e.setName("Mark");
    e.print();

    return 0;
}
```

- In the example above, direct access to `m_name` is prevented and any changes to `m_name` via `setName()` also affects `m_firstInitial` (and thus `print()` works correctly).

#### Non-member functions improve encapsulation
- Using non-member functions can enhance encapsulation by allowing a class to expose only the essential interface, keeping its internal workings hidden and separated from the main logic.
	- This approach promotes better modularity and clearer design, as it reduces the responsibility of the class to only those tasks it absolutely needs to perform.
- For example:

```C++
#include <iostream>

class Rectangle {
public:
	Rectangle(double w, double h) : width(w), height(h) {}
	double getWidth() const { return width; }
	double getHeight() const { return height; }

private:
	double width, height;
};

double perimeter(const Rectangle& rect) {
	return 2 * (rect.getWidth() + rect.getHeight());
}

int main() {
	Rectangle model(4.0, 5.5);

	std::cout << perimeter(model) << std::endl;

	return 0;
}
```

- Using non-member functions contribute to encapsulation in many ways:
	- **Minimizes class responsibilities & reduces access needs** : number of functions tied to the implementation is reduced, reducing clutter and likelihood of breaking encapsulation.
	- **Supports better modularity and separation of concerns** : non-member functions can be located in separate files, and functionality can be extended without altering the class directly.
	- **Enhances flexibility and code reusability** : non-member functions are usable with other types if needed.
- Another example of using non-member function to enhance encapsulation:

```C++
class Account {
public:
    Account(double balance) : balance(balance) {}
    void deposit(double amount) { if (amount > 0) balance += amount; }
    void withdraw(double amount) { if (amount > 0 && amount <= balance) balance -= amount; }
    double getBalance() const { return balance; }

private:
    double balance;
};

// Non-member utility function
double transfer(Account& from, Account& to, double amount) {
    if (amount > 0 && from.getBalance() >= amount) {
        from.withdraw(amount);
        to.deposit(amount);
        return amount;
    }
    return 0.0;  // Transfer failed
}
```

### Copy elision
- <mark class="hltr-trippy">Copy elision</mark> is a compiler optimization that eliminates unnecessary copying or moving of objects.
	- This allows the compiler to create an object directly in its final location, avoiding the overhead of creating temporary objects.
	- It can happen in certain situations, even without enabling optimization flags, and in some cases, it is required (since C++17).
- Copy elision can occur with return-by-value. When a function returns an object by value, the compiler can directly construct the return value in the location where it will be used, bypassing the need for a temporary copy. For example:

```C++
#include <iostream>

class MyClass {
private:
	int m_x;
	int m_y;

public:
	MyClass(int x, int y) : m_x(x), m_y(y) {
		std::cout << "Normal initialization" << std::endl;
	}

	MyClass(const MyClass& temp) : m_x(temp.m_x), m_y(temp.m_y) {
		std::cout << "Copy initialization" << std::endl;
	}
};

MyClass createObject(int x, int y) {
	return MyClass(x, y);
}

int main() {
	MyClass obj1(5, 2);
	MyClass obj2(obj1); // Copy constructor is called.
	MyClass obj3 = createObject(3, 7); // Copy constructor is NOT called
	MyClass obj4{ createObject(8, 1) }; // Copy constructor is NOT called

	return 0;
}
```

```console
Normal initialization
Copy initialization
Normal initialization
Normal initialization
```

- In the example above, without copy elision, using `createObject()` as an initializer would've made a temporary object and invoked copy initialization. But with copy elision, copy initialization does NOT occur.
- When an object is initialized directly from a temporary, the compiler also skips the copy construction and directly initializes the object. For example:

```C++
MyClass obj5 = MyClass(9, 6); // Copy constructor is NOT called
```

>[!important]
>Since C++17, copy elision is guaranteed in certain cases, such as:
>- When an object is returned from a function by value.
>- When an object is constructed by direct initialization or copy initialization from a temporary.

### Converting constructors and the explicit keyword
- A <mark class="hltr-trippy">converting constructor</mark> is a constructor that allows implicit type conversion from one type to another.
	- It typically takes a single parameter (or a set of parameters) and enables the compiler to convert from the constructor's parameter type(s) to the type of the class.
	- Converting constructor is needed in order to convert from a fundamental type to a user-defined type.
- For example:

```C++
class MyClass {
public:
    MyClass(int value) : data(value) {}  // Converting constructor
private:
    int data;
};

void func(MyClass obj) {
    // function that accepts MyClass object
}

int main() {
    func(10);  // MyClass(10) implicitly called to convert int to MyClass
}
```

- In the example above, the constructor `MyClass(int value)` allows implicit conversion from `int` to `MyClass`.

>[!warning] Issues with implicit conversions
>While convenient, implicit conversions can lead to unexpected results, especially in cases of:
>- Accidental conversions that result in unexpected behavior.
>- Ambiguity in code readability, where conversions occur without being explicitly indicated.

- The `explicit` keyword prevents the compiler from using the constructor for implicit conversions.
	- When a constructor is marked `explicit`, it can only be used for direct initialization, and any attempt at implicit conversion will result in a compilation error.
- For example:

```C++
class MyClass {
public:
    explicit MyClass(int value) : data(value) {}  // Explicit converting constructor
private:
    int data;
};

void func(MyClass obj) {}

int main() {
    func(10);  // Error: no implicit conversion from int to MyClass
    func(MyClass(10));  // Works: explicit conversion
}
```

>[!warning] Do not make copy (and move) constructors `explicit`.
>Default constructors without parameters, or constructors that take multiple arguments aren't typically made `explicit`.

>[!important] Constructors that take a single argument should usually be made `explicit`.

### Constexpr class type
- In order to make a class type that can be evaluated at compile-time, the class type must be made `constexpr`. This can be done so by defining a `constexpr` constructor.
	- For its member functions to work in constant expressions, mark them as `constexpr` as well.
- For example:

```C++
class Point {
public:
    constexpr Point(double x, double y) : x_(x), y_(y) {}

    constexpr double getX() const { return x_; }
    constexpr double getY() const { return y_; }

    constexpr Point add(const Point& other) const {
        return Point(x_ + other.x_, y_ + other.y_);
    }

private:
    double x_, y_;
};

int main() {
    constexpr Point p1(3.5, 4.2);          // Compile-time object
    constexpr Point p2(1.5, 2.8);
    constexpr Point p3 = p1.add(p2);       // Compile-time addition

    // Run-time creation of Point
    Point p4(7.2, 6.1);
}
```

>[!important]
>Data members in a `constexpr` class type must be types that are `constexpr` compatible; such as `int`, `double`, `std::array`, and etc. Note that pointers to dynamically allocated memory are NOT compatible.

>[!important] In order for `constexpr` class type to be evaluated at compile-time, the object definition must also be `constexpr`.

>[!warning] C++14 and above, `constexpr` member functions are no longer implicitly `const`.
>In order to ensure that the member function does not modify any of the data members, it must be made a `const` member function explicitly.

### Special pointer to the instance of the class
- The `this` pointer is a special pointer available in all non-static member functions of a class. It points to the instance of the class on which the member function is called.
	- It provides direct access to the current object and can be used to differentiate between member variables and parameters in methods (hence, **disambiguation**).
	- `this` is automatically passed to each non-static member function.
- As mentioned in [[#Member selection for pointers to structs]], member selection from pointer operator (arrow operator) `->` can be used to access a member from a pointer to a `class`.
	- For example, `(*MyClass).foo()` can be re-written as `MyClass->foo()`.
- Since `this` is a pointer to the current object, `->` can be used to access a member of the current object (e.g. `this->member`).
- For example:

```C++
#include <iostream>
#include <string>

class Person {
public:
    Person(const std::string& name) : name(name) {}

    void introduce() {
        std::cout << "Hello, my name is " << this->name << "." << std::endl;
    }

private:
    std::string name;
};

int main() {
    Person person("Alice");
    person.introduce();  // Outputs: Hello, my name is Alice.
    return 0;
}
```

- In the example above, the `name` of the current `Person` instance is called inside the `introduce()` function.

>[!important] In a `const` member function, `this` is treated as a pointer to a `const` instance of the class.

### Method chaining
- <mark class="hltr-trippy">Method chaining</mark> is a technique where multiple methods are called in a single statement by chaining them together.
	- Each method in the chain returns a reference (often `*this`) to the object itself, allowing subsequent methods to be called directly on the returned object.
- For example:

```C++
#include <iostream>

class Box {
public:
    Box& setLength(double l) {
        length = l;
        return *this;
    }
    
    Box& setWidth(double w) {
        width = w;
        return *this;
    }
    
    Box& setHeight(double h) {
        height = h;
        return *this;
    }
    
    void displayDimensions() const {
        std::cout << "Length: " << length << ", Width: " << width << ", Height: " << height << "\n";
    }

private:
    double length{0}, width{0}, height{0};
};

int main() {
    Box box;
    box.setLength(10.5).setWidth(5.5).setHeight(7.0).displayDimensions();  // Method chaining

    return 0;
}
```

- In the example above, each method (`setLength`, `setWidth`, `setHeight`) returns a reference to the current instance of the `Box` class (e.g. `*this`). This allows the chaining of the methods.
- Common use cases for method chaining:
	- **Builder patterns** : often used to construct objects with a series of configurations.
	- **Query building** : common in database libraries or search filters, where criteria are added step-by-step.
	- **Math libraries** : for expressions like `{C++} Vector().scale(2).add(Vector(1,1)).normalize()`.

>[!warning]
>While method chaining is powerful, excessive chaining can sometimes reduce readability if the chain grows too long or involves too many calls.

#### Builder pattern
- The <mark class="hltr-trippy">builder pattern</mark> is a creational design pattern in OOP that separates the construction of a complex object from its representation.
	- This pattern is particularly useful when creating objects that require multiple steps or complex configurations.
	- Instead of having a complex constructor with many parameters, the builder pattern allows an object to be constructed step-by-step in a readable and flexible way.
- Key components of the builder pattern:
	- **Builder** : a separate object responsible for constructing the product.
	- **Fluent interface** : the builder methods return the builder itself, enabling method chaining.
	- **Director** (optional) : A class that can be used to manage and streamline the building process, especially if the construction process is complex.
	- **Immutable object** : the final object built is usually immutable, meaning its properties cannot be changed after construction.
- For example:

```C++
#include <iostream>
#include <string>

class House {
public:
    // Members are public for simplicity but could be private with getters.
    std::string windows;
    std::string doors;
    std::string roof;

    void show() const {
        std::cout << "House with " << windows << ", " << doors << ", and " << roof << ".\n";
    }
};

class HouseBuilder {
private:
    House house;

public:
    HouseBuilder& setWindows(const std::string& windows) {
        house.windows = windows;
        return *this;  // Returns a reference to the current builder
    }

    HouseBuilder& setDoors(const std::string& doors) {
        house.doors = doors;
        return *this;
    }

    HouseBuilder& setRoof(const std::string& roof) {
        house.roof = roof;
        return *this;
    }

    // Build method to return the constructed House
    House build() const {
        return house;
    }
};

int main() {
    House house = HouseBuilder()
        .setWindows("Double-glazed windows")
        .setDoors("Wooden doors")
        .setRoof("Gabled roof")
        .build();

    house.show();  // Outputs: House with Double-glazed windows, Wooden doors, and Gabled roof.

    return 0;
}
```

- In the example above, `House` class is the product which is built by the builder `HouseBuilder` class. 
- The builder pattern is useful when constructing an object with a long list of parameters, especially if many are optional.

[[design_patterns_for_graphics_programming|Speaking of design patterns..]]

### Organizing classes in a multi-file setup
#### 1. Separate interface and implementation
- Declare the class and its member functions without implementation details in a header file (e.g. `ClassName.h`):

```C++ title:ClassName.h
#ifndef CLASSNAME_H
#define CLASSNAME_H

class ClassName {
public:
    ClassName();
    void someMethod() const;
private:
    int memberVar;
};

#endif
```

- Implement the class's member functions in a source file (e.g. `ClassName.cpp`):

```C++ title:ClassName.cpp
#include "ClassName.h"

ClassName::ClassName() : memberVar(0) {}

void ClassName::someMethod() const {
    // Implementation details
}
```

#### 2. Avoid including unnecessary headers
- Avoid including headers in other heads unless strictly necessary. This reduces compile time and dependency issues.
- If a member function only requires a type in its parameter list, prefer **forward declarations** over including full headers in the class declaration. For example:

```C++ title:ClassName.h
// Forward declare AnotherClass
class AnotherClass;

class ClassName {
public:
    void doSomethingWith(AnotherClass& obj);  // No need to include "AnotherClass.h" here
};
```

#### 3. Use inline functions for simple member functions
- Simple functions, especially getters and setters, can be defined inline within the header file to potentially reduce call overhead.
- Mark these as `inline` to avoid linker errors with multiple inclusions.
- For example:

```C++ title:ClassName.h
#ifndef CLASSNAME_H
#define CLASSNAME_H

class ClassName {
public:
    ClassName();
    int getMemberVar() const;
    void someMethod() const;
private:
    int memberVar;
};

inline int ClassName::getMemberVar() const { return memberVar; }

#endif
```

>[!important]
>Member functions inside class definition are implicitly inline. However, once it is defined outside the class definition, it is no longer implicitly inline - which opens up the risk for the violation of ODR.

>[!warning] Avoid putting non-inline member function definitions in headers unless required.

>[!note] Personally, I think this is just overcomplicating some bullshit.

#### 4. Use include guards
- Use `#ifndef`/`#define`/`#endif` include guards or `#pragma once` to prevent multiple inclusions of the same header.

#### 5. Group headers by purpose and use `namespace`
- Use dedicated headers for related functionality or a logical grouping of classes.
	- For instance, `Physics.h` might group all physics-related classes.
- Use namespaces to group related classes logically and prevent name conflicts. For example:

```C++
// Physics.h
namespace Physics {
    class RigidBody;
    class Vector3;
}
```

#### Example

Car.h
```C++
#ifndef CAR_H
#define CAR_H

class Engine;  // Forward declaration

class Car {
public:
    Car();
    void start();

private:
    Engine* engine;  // Use pointer or reference to avoid including "Engine.h"
};

#endif
```

Car.cpp
```C++
#include "Car.h"
#include "Engine.h"  // Only include here, where Engine implementation is needed

Car::Car() : engine(nullptr) {}

void Car::start() {
    // Use engine here
}
```

### Member types
- <mark class="hltr-trippy">Member types</mark> refer to types that are defined inside a class or struct. These can be:
	- Type aliases (using `typedef` or `using`)
	- Nested types
	- Member template types
- Member types are defined inside the class definition and are typically used to describe types that are closely related to the class itself.
	- These types can be accessed through instances of the class or via the class name.

#### Member type aliases
- A <mark class="hltr-trippy">member type alias</mark> allows you to define a type within the class that can be used to reference another type. For example:

```C++
class MyClass {
public:
    using MyInt = int;   // Member type alias
    typedef double MyDouble;  // Another way of doing it with typedef
};

MyClass::MyInt a = 5;  // Usage of the member type alias
MyClass::MyDouble b = 3.14;  // Usage of the typedef member type
```

#### Nested types
- A <mark class="hltr-trippy">nested class</mark> is a class that is defined inside another class.
	- It can be used to model entities that are logically part of the outer class.
- For example:

```C++
class OuterClass {
public:
    class NestedClass {  // A member type that is a class
    public:
        void print() { std::cout << "Inside Nested Class\n"; }
    };
};

OuterClass::NestedClass nestedObj;
nestedObj.print();  // Usage of the nested class type
```

- In the example above, `NestedClass` is a member type of `OuterClass`.
- Like nested class, a <mark class="hltr-trippy">nested enum</mark> is a type that is defined inside a class.
	- It is useful for limiting the scope of the enum to only be relevant to the class.
- For example:

```C++
class MyClass {
public:
    enum Color { Red, Green, Blue };  // A nested enum
};

MyClass::Color c = MyClass::Red;  // Usage of the nested enum
```

#### Member template types
- A class can define member templates that allow the creation of types based on template parameters. For example:

```C++
class MyClass {
public:
    template<typename T>
    class NestedTemplateClass {  // Member template type
    public:
        T value;
    };
};

MyClass::NestedTemplateClass<int> obj;  // Usage of the nested template class
obj.value = 10;
```

### Destructors
- A <mark class="hltr-trippy">destructor</mark> is a special member function of a class that is called when an object of that class is destroyed.
	- Its primary role is to clean up resources that the object may have acquired during its lifetime, such as memory, file handles, or network connections.
	- **Automatic invocation** : a destructor is automatically called when an object goes out of scope or is explicitly deleted. However, a it cannot be called explicitly.
	- A class can have only **one destructor**.
	- If a destructor is not declared, then it is implicitly generated by the compiler.
- A destructor must have the same name as the class, preceded by a tilde `~`.
	- Destructors do not take parameters and cannot be overloaded.
	- No return value.
- For example:

```C++
class MyClass {
public:
    // Constructor
    MyClass() {
        // Initialization code
    }

    // Destructor
    ~MyClass() {
        // Cleanup code
    }
};
```

>[!warning]
>`std::exit()` function can be used to terminate a program immediately. When the program is terminated immediately, it means that it skips all calls to the destructors - which might become troublesome if some of the necessary cleanups are relying upon the destructors.

#### Example of using destructor in network program

```C++
class NetworkData
{
private:
    std::string m_serverName{};
    DataStore m_dataQueue{};

public:
	NetworkData(std::string_view serverName)
		: m_serverName { serverName }
	{
	}

	~NetworkData()
	{
		sendData(); // make sure all data is sent before object is destroyed
	}

	void addData(std::string_view data)
	{
		m_dataQueue.add(data);
	}

	void sendData()
	{
		// connect to server
		// send all data
		// clear data
	}
};

int main()
{
    NetworkData n("someipAddress");

    n.addData("somedata1");
    n.addData("somedata2");

    return 0;
}
```

- In the example above, the destructor ensures that the existing data is sent out in case the program halts prematurely (e.g. connection loss).

#### Destructors for derived classes
- When an object of a derived class is destroyed, the destructor of the derived class is called first, followed by the destructor of the base class.
	- This process ensures that the resources managed by the derived class are cleaned up before the base class resources.
- For example:

```C++
#include <iostream>

class Base {
public:
    Base() {
        std::cout << "Base Constructor\n";
    }

    ~Base() {
        std::cout << "Base Destructor\n";
    }
};

class Derived : public Base {
public:
    Derived() {
        std::cout << "Derived Constructor\n";
    }

    ~Derived() {
        std::cout << "Derived Destructor\n";
    }
};

int main() {
    Derived obj;  // Object of derived class
    // Destructor of Derived is called first, then the Base class destructor
    return 0;
}
```

```console
Base Constructor
Derived Constructor
Derived Destructor
Base Destructor
```

### Class templates with member functions

```C++
#include <ios>       // for std::boolalpha
#include <iostream>

template <typename T>
class Pair
{
private:
    T m_first{};
    T m_second{};

public:
    // When we define a member function inside the class definition,
    // the template parameter declaration belonging to the class applies
    Pair(const T& first, const T& second)
        : m_first{ first }
        , m_second{ second }
    {
    }

    bool isEqual(const Pair<T>& pair);
};

// When we define a member function outside the class definition,
// we need to resupply a template parameter declaration
template <typename T>
bool Pair<T>::isEqual(const Pair<T>& pair)
{
    return m_first == pair.m_first && m_second == pair.m_second;
}

int main()
{
    Pair p1{ 5, 6 }; // uses CTAD to infer type Pair<int>
    std::cout << std::boolalpha << "isEqual(5, 6): " << p1.isEqual( Pair{5, 6} ) << '\n';
    std::cout << std::boolalpha << "isEqual(5, 7): " << p1.isEqual( Pair{5, 7} ) << '\n';

    return 0;
}
```

>[!important]
>Member functions defined inside the class template definition do not require template parameter declaration. In the example above, note that the constructor is `Pair()` instead of `Pair<T>()`.

### Static member variable
- A <mark class="hltr-trippy">static member variable</mark> is a variable that is shared by all instances of a class rather than each instance having its own copy.
	- Any modification to the static variable in one object will be reflected across all other objects of the same class.
	- Static member variables can be accessed without creating an object of the class.
	- Static member variables must be defined outside the class definition (unless `const` or `constexpr`).
- For example:

```C++
#include <iostream>
using namespace std;

class MyClass {
public:
    static int count;  // Static member variable declaration

    MyClass() {
        count++;  // Increment count each time an object is created
    }

    static void showCount() {
        cout << "Number of objects created: " << count << endl;
    }
};

// Definition and initialization of static variable
int MyClass::count = 0;

int main() {
    MyClass obj1;
    MyClass obj2;
    MyClass obj3;

    // Accessing static member variable through the class name
    MyClass::showCount();  // Output: Number of objects created: 3

    return 0;
}
```

>[!warning]
>Since static variables are shared by all instances, concurrent modifications in multi-threading environments could lead to data races if not properly synchronized.

>[!important] Static members may use type deduction (`auto` and CTAD).
>Conversely, it means that non-static members may not use type deduction.

### Static member functions
- A <mark class="hltr-trippy">static member function</mark> is a function that belongs to the class itself, rather than any instance of the class.
	- Static member functions are useful for operations that are related to the class but do not require any data from specific instances (they can be called without creating an object of the class).
- For example:

```C++
#include <iostream>

class MyClass {
public:
    static int count;  // Static member variable
    static void incrementCount() {
        count++;  // Accessing static variable
    }
    static void showCount() {
        std::cout << "Count: " << count << std::endl;
    }
};

// Definition of the static member variable outside the class
int MyClass::count = 0;

int main() {
    MyClass::incrementCount();  // Call static member function without an instance
    MyClass::showCount();       // Outputs: Count: 1

    MyClass obj;
    obj.incrementCount();       // Can also call via an instance, but it's not common
    MyClass::showCount();       // Outputs: Count: 2

    return 0;
}
```

- Since static member functions do not belong to an instance, they do not have access to the `this` pointer and cannot refer to non-static members directly.
	- However, they can access static members.
- The `const` qualifier is meaningless for a static member function because it cannot access non-static member variables.
- Although a derived class can inherit static functions, they are still called at the class level and do not exhibit polymorphic behavior. This also means that the static member functions cannot be `virtual`.

>[!important] Static member functions are mostly used as utilities.
>A class can be used to group similar utility functions together. For example, `Math` class can include functions such as `square(int x)`, `multiply(int x, int y)`, and etc.

>[!important] Modern C++ favors non-member functions when possible.
>That said, use static member functions if:
>- The function needs direct access to private static data or members.
>- The function's purpose is highly specific to the class and benefits from being visibly associated with it.

### Real-world scenarios using static members
#### Tracking the number of active instances

```C++
class NetworkConnection {
private:
    static int activeConnections; // Shared among all instances

public:
    NetworkConnection() { ++activeConnections; }
    ~NetworkConnection() { --activeConnections; }

    static int getActiveConnections() { return activeConnections; } // Public accessor
};

int NetworkConnection::activeConnections = 0; // Define and initialize outside the class

// Usage
int main() {
    NetworkConnection conn1;
    NetworkConnection conn2;
    std::cout << "Active Connections: " << NetworkConnection::getActiveConnections() << std::endl; // Outputs: 2
    return 0;
}
```

#### Configuration management

```C++
class Logger {
private:
    static bool verboseMode; // Shared configuration setting

    static void logInternal(const std::string& message) {
        if (verboseMode) {
            std::cout << "[VERBOSE] " << message << std::endl;
        } else {
            std::cout << message << std::endl;
        }
    }

public:
    static void setVerboseMode(bool mode) { verboseMode = mode; } // Public interface
    static void log(const std::string& message) { logInternal(message); }
};

bool Logger::verboseMode = false; // Initialize the static variable

// Usage
int main() {
    Logger::setVerboseMode(true);    // Set global configuration
    Logger::log("Starting application..."); // Uses verbose mode
    return 0;
}
```

#### Connection management

```C++
class DatabaseConnection {
private:
    static int activeConnections;
    static const int maxConnections = 5;

public:
    DatabaseConnection() {
        if (activeConnections >= maxConnections) {
            throw std::runtime_error("Max connections reached");
        }
        ++activeConnections;
    }

    ~DatabaseConnection() {
        --activeConnections;
    }

    static int getActiveConnectionCount() {
        return activeConnections;
    }
};

int DatabaseConnection::activeConnections = 0; // Initialize static variable

// Usage
int main() {
    try {
        DatabaseConnection conn1;
        DatabaseConnection conn2;
        std::cout << "Active connections: " << DatabaseConnection::getActiveConnectionCount() << std::endl;
    } catch (const std::runtime_error& e) {
        std::cerr << e.what() << std::endl;
    }
    return 0;
}
```

