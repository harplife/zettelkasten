---
aliases: [KNOU C++ Class Assignment, 8 Basic Problems for C++]
tags: [computer_science, KNOU, school, class, c++, assignment]
status: ongoing
edited: 2021-11-01
---

# KNOU C++ Class Assignment
Following are 8 problems given as an assignment.
The problems are given in a following format:
1. An incomplete code is given
2. A problem asks to complete the code that fits a number of conditions

Refer to [[knou_cpp_notes|KNOU C++ Class Notes]]

## FirstStep.cpp
Following program prints a line of characters.

### Code
```c++
#include <iostream>

int main()
{
    std::cout << "one small step" << std::endl;
    return 0;
}
```

### Condition
1. Change the code so that line 5 becomes
`cout << "one small step" << endl;`

### Solution
add below line 1 following code
```c++
using namespace std; // c++ standard library
```

## FindMaxInArr.cpp
Following program computes the max value from a data array.

### Code
```c++
#include <iostream>
using namespace std;

int main()
{
    int data[10] = { 10, 23, 5, 9, 22, 48, 12, 10, 55, 31 };
    int  ㈀;  // set 1st value from data as max

    cout << "Data : " << ㈁ ;  // print 1st value from data
    for (       ㈂       ) {   // iterate the rest 9 from data
        cout << "  " << ㈃ ;   // print data at i
        if (max < ㈃ )   // if data at i is bigger than max,
            max = ㈃;    // then set data at i as new max
    }
    cout << endl << endl;
    cout << "The max value is : " << max << endl;
    return 0;
}
```

### Condition
1. Fill in the blanks, following the instructions in the comment(s)

### Solution
1. ㈀ = `max{data[0]}`
2. ㈁ = `data[0]`
3. ㈂ = `int i=1; i<10; i++`
4. ㈃ = `data[i]`

## IntPtr.cpp
Following program uses a Pointer to change the value of another variable.

### Code
```c++
#include <iostream>
using namespace std;

int main()
{
    int  a = 10, b = 100;
    int  ㈀ ; 	// pointer ptr holds memory address of a

    cout << "a's value : " << ㈁ << endl; // print a's value using pointer ptr
    ㈂ = 20;   // change a's value using pointer ptr
    cout << "a's new value : " << a << endl;
    ㈃ ;       // make pointer ptr to point at b
    cout << "b's value : " << *ptr << endl;
    return 0;
}
```

### Condition
1. Fill in the blanks, following the instructions in the comment(s)

### Solution
1. ㈀ = `*ptr{&a}`
2. ㈁ = `*ptr`
3. ㈂ = `*ptr`
4. ㈃ = `ptr = &b`

## DAlloc.cpp
Following program uses a Pointer like an Array.
This is also an example of using Pointer to allocate multiple memory spaces.

### Code
```c++
#include <iostream>
using namespace std;

int main()
{
    int *intPtr;
    ㈀ ; // allocate 4 memory space for intPtr
    *intPtr = 10;
    *(intPtr + 1) = 20;
    intPtr[2] = 30;
    intPtr[3] = 40;
    for (int *p = intPtr, i = 0; i < 4; i++) {
        cout << ㈁ << " ";  // print value where p is pointing, and move p to next
	}
    cout << endl;
    ㈂ ; // release intPtr's allocated spaces
    return 0;
}
```

### Condition
1. Fill in the blanks, following the instructions in the comment(s)

### Solution
1. ㈀ = `intPtr = new int[4]`
2. ㈁ = `*p++`
3. ㈂ = `delete[] intPtr`


## RecTest.cpp
Following program is an example of using a Reference to change another variable's value.

### Code
```c++
#include <iostream>
using  namespace  std;

int main()
{
    int  a{10}, b{20};
    ㈀ ; // Initialize aRef to reference a
    cout << "a's value : " << a << endl;
    cout << "aRef referenced value : " << aRef << endl << endl;
    ㈁ = 100; // change a's value using aRef
    cout << "a's value : " << a << endl;
    ㈂ = b; // change a's value using aRef
    cout << "a's value : " << a << endl;
    return 0;
}
```

### Condition
1. Fill in the blanks, following the instructions in the comment(s)

### Solution
1. ㈀ = `int &aRef = a`
2. ㈁ = `aRef`
3. ㈂ = `aRef`


## GetMax.cpp
Following program uses a function `getMax()` to get the max value from an array.
This is also an example of Overloading.

### Code
```c++
#include <iostream>
㈀ // include climits header file to use INT_MIN
using namespace std;

int getMax(const int arr[], int len)
{
    int max{INT_MIN}; // INT_MIN == -2147483648, integer's lowest limit
    for (int i = 0; i < len; i++) {
        if (  ㈁  ) { // if value at i is bigger than max,
            ㈂ ;      // then set max to that value
        }
    }
    ㈃ ; // output max
}

int main()
{
    int data[10] = { 10, 23, 5, 9, 22, 48, 12, 10, 55, 31 };

    cout << "data : ";
    for (auto d : data) {
        cout << d << " ";
    }
    cout << endl << endl;
    cout << "max value is " << ㈄ << endl; // get max value from data
}
```

### Condition
1. Fill in the blanks, following the instructions in the comment(s)
2. Use Overloading so that `getMax()` can accept float array

### Solution
1. ㈀ = `#include <climits>`
2. ㈁ = `max < arr[i]`
3. ㈂ = `max = arr[i]`
4. ㈃ = `return max`
5. ㈄ = `getMax(data, 10)`

Overloading `getMax()`
```c++
float getMax(const float arr[], int len)
{
    float max{arr[0]}; // no FLOAT_MIN?
    for (int i=1;i<len;i++){
        if (max < arr[i]){
            max = arr[i];
        }
    }
    return max;
}
```

## CallByRef.cpp
Following program takes a user input, radius of a circle, and calculates the circle's area.
This is also an example of a function using a Reference to change the data in struct.

### Code
```c++
#include	<iostream>
using namespace std;

const float PI{3.14159265f};
struct Circle {
    float radius;
};

// Circle data input
 ㈀ inputData(  ㈁  ) // ㈀ = no data type, ㈁ = Reference to Circle
{
    cout << "type a value for radius : ";
    cin >> c.radius;
}

// Circle data print
 ㈀ prData(  ㈂  ) // ㈂ = Reference to Circle, but its attributes cannot be changed
{
    cout << "Circle's radius is " << c.radius << endl;
}

// Circle area calculate
 ㈃ area(  ㈂  )
{
    return PI * c.radius * c.radius;
}

int main()
{
    Circle circle = {1, 2, 3};
    inputData(circle);
    prData(circle);
    cout << "Circle's area is " << area(circle) << endl;
}
```

### Condition
1. Fill in the blanks, following the instructions in the comment(s)

### Solution
1. ㈀ = `void`
2. ㈁ = `Circle& c`
3. ㈂ = `const Circle& c`
4. ㈃ = `float`

## CallByRefOverload.cpp
This is a continuation of problem [CallRyRef.cpp](##CallByRef.cpp).
Code is same.

### Condition
1. Use Overloading on `inputData()`, `prdata()`, and `area()` so that it can handle `Rectangle`.

```c++
struct Rectangle {
    float width, height;
}
```

### Solution
```c++
// ..

void inputData(Rectangle& r)
{
    cout << "type a value for width : ";
    cin >> r.width;
    cout << "type a value for height : ";
    cin >> r.height;
}

void prData(const Rectangle& r)
{
    cout << "Rectangle's width is " << r.width << endl;
    cout << "Rectangle's height is " << r.height << endl;
}

float area(const Rectangle& r)
{
    return r.width * r.height;
}

// ..
```

