---
aliases: [KNOU C++ Class Notes]
tags: [computer_science, KNOU, school, class]
status: ongoing
edited: 2021-10-31
---

# KNOU C++ Class Notes
Notes going over
- basics
- variables and arrays
- pointers and references
- functions

#todo Pointers, Reference, and Overloading deserves its own notes.

## Basics
- File extension is `*.cpp`
- Single line comments with `//`
- Preprocessing Directive (선행처리기 지시어) is declared on top of the file
- Preprocessing Directive is the very first thing that is processed by the compiler
- Preprocessing Directive `#include` means to import codes from a header file
- Preprocessing means translating the source for the compiler, before the compilation takes place
- All Preprocessing Directives start with `#`
- Some examples of Preprocessing Directives: `#define`, `#undef`, `#if`, `ifdef`, etc
- Header file does not require file extension, however, it is rule of thumb to use `*.h`, `*.hh`, or `*.hpp`
- The most used header for printing to console is `iostream`
- C programming used `stdio` for printing
- C programming is data oriented language, whereas C++ programming is Object oriented
- `std::cout` means Character Output. It converts input value to characters
- Bitwise Operators, such as `>>` and `<<`, are used to insert values into an object (dunno if this is correct interpretation, the teacher is a bit of an arrogant asshole who can only explain in his own words)
- `endl` means end line, and is the same thing as newline
- `std::cin` means Character Input. It waits for input at the console. Used with `>> variable`, which inserts input characters into the variable (as the data type of the variable)

## Variables and Arrays
- Scope (명칭공간) is defines the space where variable names belong to. It helps to differentiate variables with the same name. (e.g. Local variables inside a function, global variables, or variables from other classes)
- `std` is a scope where standard libraries are defined at
- Local variable takes priority over Global variable
- A global variable can be called with `::`, as such `::variable`
- A scope can be defined like so -> `namespace duku {int count;}`
- A namespace can be declared so that it doesn't have to be mentioned every time -> `using namespace std` so that `std::cout` is now just `cout`
- A variable is a memory space that holds data (a shitty definition, says the teacher, but he's the one that gave this definition?)
- You can declare a variable like `int number;` or `int count, total, numbers;`
- Simply declaring a variable like `int number;` will fill it with garbage data (data that was at the memory address)
- There are several ways to initialize a variable -> `int total(0)`, `int total{0}`, `int total = {0}`, and etc

---

In C++, both the `=` and `{}` syntaxes can be used to initialize variables, and in most cases, they have the same efficiency. However, there are some differences in behavior that might affect which one you choose to use.

1. **Uniform Initialization (Curly Brackets `{}`)**: This was introduced in C++11 to provide a consistent syntax for initialization in all scenarios. It prevents narrowing conversions (which can cause data loss), and it can be used to initialize user-defined types, arrays, and STL containers. For example:

```cpp
int a{5}; // OK
int b{3.14}; // Error: narrowing conversion
std::vector<int> v{1, 2, 3, 4, 5}; // OK
```

2. **Copy Initialization (`=`)**: This is the traditional way to initialize variables in C++. It allows narrowing conversions, but it can't be used to directly initialize arrays or complex types. For example:

```cpp
int a = 5; // OK
int b = 3.14; // OK, but b will be 3 due to truncation
std::vector<int> v = {1, 2, 3, 4, 5}; // OK
```

In terms of performance, both methods are typically optimized by the compiler to be equally efficient. The choice between `{}` and `=` often comes down to coding style and the specific requirements of your code. For modern C++ code, many developers prefer `{}` because it is more consistent and prevents narrowing conversions. However, `=` is still widely used and perfectly acceptable in many situations. It's always a good idea to understand the differences and choose the method that best fits your needs.

---

- Curly brackets `{ .. }` is often used for function, construct, arrays, and sets
- Data type `auto` automatically matches the variable's data type to the data it is initialized with. (e.g. `auto total(5); // same thing as int total(5);`)
- `const` is a constant, meaning it only holds the data it is initialized with, and never changes afterwards
- An array can be initialized like `float fArray[4];`, which creates an array that takes in 4 float values
- An array `fArray` is a constant. `fArray[0]` is a variable.
- 2 dimensional array is like `int Arr2D[4][3]`, which creates an array that holds integers in a 4 rows and 3 columns matrix
- Array can be initialized like this: `int a[3]{1,2,3};` or `int a[3]{1}; //the rest are zeroes` or `int a[]={1,2,3}; //size becomes 3`

## Pointers and References
- Pointer is a variable that points to the memory location of other variables/objects
- `*` signifies a pointer, like `int *iPtr;`
- `&` grabs the memory address of a variable.
Example 1 using pointer
```c++
int count(10); // variable count that holds integer value 10
int *ptr = &count; // pointer that holds memory address of variable count

*ptr = 20; // changes value of count to 20
```
Example 2 using pointer
```c++
int a{10};

int *ptr{&a};

cout << "value a : " << a << endl;
cout << "value ptr : " << ptr << endl;
cout << "value *ptr : " << *ptr << endl;
```
prints
```
value a : 10
value ptr : 0x7fffffffd91c
value *ptr : 10
```
- The meaning of `*` for when initializing a pointer means the pointer points to a memory location (e.g. `int *ptr{&a}; // takes the memory addr of a`)
- The meaning of `*` for when using a pointer means it will change the value at the memory address (e.g. `*ptr = 20; // will change the value of a`)
- To change where the pointer points at -> `ptr = &b;`, note the lack of `*`
- Another interpretation of `*` when initializing a pointer, is that it defines the dimension at which the pointer can access
```c++
// example of pointer "dimension"
int a{10};
int *ptr = &a; // a pointer that points at a
int **ptr2 = &ptr; // a pointer that points at a pointer
int ***ptr3 = &ptr2; // a pointer-pointer-pointer
```
Note that `ptr3` can only access pointers at `**` level, meaning `ptr2` and not `ptr`.
```c++
// continuation of pointer "dimension"
int a{10};
int *ptr{&a};
int **ptr2{&ptr};
int ***ptr3{&ptr2};

cout << ptr3 << endl; // prints memory location of ptr2
cout << *ptr3 << endl; // prints memory location of ptr
cout << **ptr3 << endl; // prints memory location of a
cout << ***ptr3 << endl; // prints the value of a
```
- Dynamic Memory Allocation (동적 메모리 할당) refers to performing memory allocation manually by programmer
- `new` allocates a memory (e.g. `ptrVar = new TypeName;`)
- `delete` returns the memory (e.g. `delete ptrVar;`)
```c++
int *intPtr;
intPtr = new int; // allocates a memory space (of nothing)
*intPtr = 10; // the memory space now has 10
```
- Reference (참조) is an alias for already existing variable. Once a reference is initialized to a variable, it cannot be changed to refer to another variable.
- Reference cannot be initialized by itself, like `int &aRef;`, which would error. Instead it must refer to a variable, like so `int &aRef = a;`
- Reference is used like any other variable
- Reference cannot change the value of a constant
- Once initialized, a Reference cannot refer to any other variable
- Reference is much similar to Pointer, except Reference is much simpler to use. More on the differences [here](https://www.geeksforgeeks.org/pointers-vs-references-cpp/)
- Example code for Reference : [[knou_cpp_assignment#RecTest cpp|RecTest.cpp]]

## Functions
- Function is a group of program statements that is assigned a name
- Since a function has a name, a pointer can point to its address
- Function Overloading means a function can have multiple definitions. This can be implemented by changing the data type of the input parameters. An example of this can be found at [[knou_cpp_assignment#GetMax cpp|GetMax.cpp]]