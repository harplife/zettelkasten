---
aliases: [Why Use Pointers]
tags: [computer_science, c++, WHY]
status: ongoing
edited: 2021-11-03
---

FYI, this is Copy&Paste from [cppbyexample.com](https://cppbyexample.com/why_pointer.html) by Rob Cusimano. I do not claim ownership for any of the content below.

# Why Use Pointers
By default, variables in C++ are copied when they are passed to functions. The same is true for structs, classes, and objects of all sizes. For example, while you might expect the function below to remove 2 of Johnny’s bones and change his name, it does not.

```c++
#include <iostream>
#include <string>

struct Skeleton {
  std::string name;
  int bones;
};

void remove_two_bones(Skeleton s) {
  s.name += " the Lesser";
  s.bones -= 2;
}

int main() {
  Skeleton johnny{"Johnny", 206};
  remove_two_bones(johnny);
  std::cout << johnny.name << " has "
            << johnny.bones << " bones.\n";
}
```
`>>> Johnny has 206 bones.`

When our `Skeleton jonny` from `main` was passed to the function `remove_two_bones`, _all_ of the values of Johnny were _copied_ into the function’s parameter `s`.

This is one of the primary uses of pointers in C++, to _avoid copying data_. We can pass a pointer to something instead of the thing itself. In so doing it’s the value of the pointer that’s being copied, _not_ the value of `Johnny`.

```c++
#include <iostream>
#include <string>

struct Skeleton {
  std::string name;
  int bones;
};

void remove_two_bones(Skeleton* s) {
  if (s) {
    s->name += " the Lesser";
    s->bones -= 2;
  }
}

int main() {
  Skeleton johnny{"Johnny", 206};
  remove_two_bones(&johnny);
  std::cout << johnny.name << " has "
            << johnny.bones << " bones.\n";
}
```
`>>> Johnny the Lesser has 204 bones.`

You may have noticed the syntax has changed when using pointers. C++ uses the ampersand(`&`) for taking the address of variables. When a variable’s value is the address of some other variable, that’s called a pointer. There’s even special syntax for saying when a `type` is a pointer, the asterisk(`*`). When an asterisk directly follows a `type`, it becomes a pointer, such as when we use `Skeleton*` above.

There’s also two pieces of syntax for the reverse of taking an address, turning an address (a pointer) into a value, the asterisk(`*`), and the arrow(`->`).