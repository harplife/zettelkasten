# Getting Started
- Following the guide https://www.learncpp.com

## Introduction to C/C++
### Before C++, there was C
- The C language was developed in 1972 by Dennis Ritchie at Bell Telephone laboratories, primarily as a systems programming language (a language to write operating systems with).
- C ended up being so efficient and flexible that in 1973, Ritchie and Ken Thompson rewrote most of the Unix operating systems using C (as opposed to Assembly).
	- Unlike Assembly, which produces programs that can only run on specific CPUs, C has excellent portability, allowing Unix to be easily recompiled on many different types of computers.
	- C and Unix had their fortunes tied together.
- In 1978, Brian Kernighan and Dennis Ritchie published a book called "The C Programming Language".
	- This book was commonly known as K&R.
	- This book provided an informal specification for the language and became a de facto standard.
- In 1983, the American National Standards Institute (ANSI) formed a committee to establish a formal standard for C.
	- In 1989, the C89 standard was released. It's more commonly known as ANSI C.
	- In 1990, the International Organization for Standardization (ISO) adopted ANSI C. This became known as C90.
- In 1999, the ISO committee released a new version of C called C99.
	- C99 adopted many features which had already made their way into compilers as extensions, or had been implemented in C++.

### C++
- In 1979, C++ was developed by Bjarne Stroustrup at Bell Labs as an extension to C.
- C++ adds many new feature to the C language, and is perhaps best thought of as a superset of C (though not strictly true).
- C++ is an object-oriented language. More on this will be covered later.
- C++ was standardized in 1998 by the ISO committee.
	- A minor update to the language was released in 2003, called C++03.
- Five major updates to the C++ language (C++11, 14, 17, 20, and 23) have been made since then, each adding additional functionality.
	- C++11 in particular added a huge number of new capabilities, and is widely considered to be the new baseline version of the language.
- Each new formal release of the language is called a **Language Standard** or **Language Specification**.
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
	- The compiler translates your C++ code into machine language instructions. These instructions are stored in an intermediate file called an **object file**. The object file also contains metadata that is required or useful in subsequent steps.
- Object files are typically named `name.o` or `name.obj`, where the `name` is the same name as the `name.cpp` file it was produced from.
- Installing a compiler will be covered later.

### Step 5: Linking object files and libraries
- 