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

## FirstStep.cpp
Following program prints a line of characters.

Code:
```c++
#include	<iostream>

int main()
{
    std::cout << "one small step" << std::endl;
    return 0;
}
```

Condition:
1. Change the code so that line 5 becomes
`cout << "one small step" << endl;`

Solution:
add below line 1 following code
```c++
using namespace std; // c++ standard library
```

## FindMaxInArr.cpp
Following program computes the max value from a data array.

Code:
```c++
#include	<iostream>
using namespace std;

int main()
{
    int data[10] = { 10, 23, 5, 9, 22, 48, 12, 10, 55, 31 };
    int  ㈀;  // set 1st value from data as max

    cout << "Data : " << ㈁ ;  // print 1st value from data
    for (          ㈂           ) {    // iterate the rest 9 from data
        cout << "  " << ㈃  ;     // print data at i
        if (max < ㈃ )    // if data at i is bigger than max,
            max = ㈃;     // then set data at i as new max
    }
    cout << endl << endl;
    cout << "The max value is : " << max << endl;
    return 0;
}
```

Condition:
1. Fill in the blanks, following the instructions in the comment(s)

Solution:
1. ㈀ = `max{data[0]}`
2. ㈁ = `data[0]`
3. ㈂ = `int i=1; i<10; i++`
4. ㈃ = `data[i]`

## IntPtr.cpp
Following program uses a Pointer to change the value of another variable.

Code:
```c++
#include <iostream>
using namespace std;

int main()
{
  int  a = 10, b = 100;
  int  ㈀ ; 	 // pointer ptr holds memory address of a

  cout << "a's value : " << ㈁  << endl; // print a's value using pointer ptr
   ㈂ = 20;   // change a's value using pointer ptr
  cout << "a's new value : " << a << endl;
  ㈃      ;         // make pointer ptr to point at b
  cout << "b's value : " << *ptr << endl;
  return 0;
}
```

Condition:
1. Fill in the blanks, following the instructions in the comment(s)

Solution:
1. ㈀ = `*ptr{&a}`
2. ㈁ = `*ptr*`
3. ㈂ = `*ptr`
4. ㈃ = `ptr = &b`

## DAlloc.cpp
Following program uses a Pointer like an Array.
This is also an example of using Pointer to allocate multiple memory spaces.

Code:
```c++
#include	<iostream>
using namespace std;

int main()
{
    int *intPtr;
     ㈀ // allocate 4 memory space for intPtr
    *intPtr = 10;
    *(intPtr + 1) = 20;
    intPtr[2] = 30;
    intPtr[3] = 40;
    for (int *p = intPtr, i = 0; i < 4; i++)
        cout << ㈁ << " ";  // print value where p is pointing, and move p to next
    cout << endl;
    ㈂　// release intPtr's allocated spaces
    return 0;
}
```

Condition:
1. Fill in the blanks, following the instructions in the comment(s)