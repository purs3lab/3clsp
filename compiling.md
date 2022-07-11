---
layout: default
title: Compiling CheckedC Code
nav_order: 5
---

# [](#header-1) Compiling CheckedC

After your conversion step is over. You might need some help with compiling this new code. CheckedC code does require a special compiler but if you followed all the steps before using the tool you installed our CheckedC version of `clang` using `NINJA`. So just use the Checked C version of clang like you would use clang. If you had a source file myfile.c, you can compile it using:
```sh
clang myfile.c
```

This assumes that the Checked C version of `clang` is on your path.

### [](#header-3) Hello World

Here is the source code for "hello, world" in Checked C:
```C
#include <stdio_checked.h>
#include <stdchecked.h>

// Make the top-level scope a checked scope.  This allows only the use of checked
// pointer and array types or declarations with bounds-safe interfaces.
#pragma CHECKED_SCOPE ON

int main(int argc, nt_array_ptr<char> argv checked[] : count(argc)) {
  puts("hello, world");
  return 0;
}
```

If you have a copy of the Checked C repo and clang is on your path, just go to the sample directory and run `clang hello-world.c` to compile the program.

### [](#header-3) RunTime Checking Failures

If bounds checking or other Checked C runtime checks fail, your program will execute an illegal instruction. You can use C signal handling to catch the illegal instruction signal and have your program exit gracefully. For example:
```c
#include <stdlib_checked.h>
#include <signal_checked.h>

void handle_error(int err) {
  _Exit(1);
}

int main(int argc, _Array_ptr<_Nt_array_ptr<char>> argv : count(argc)) {
  // Set up the handler for a failing runtime check.   A SIGILL is raised when a Checked C
  // runtime check fails.
  signal(SIGILL, handle_error);
  ...
```

### [](#header-3) Warnings for Checking of Bounds Declaration

The compiler always checks whether declared bounds are valid. This is important because bounds checking is not meaningful if the declared bounds are wrong. Declared bounds are valid if they are implied by existing declared bounds and other information in the program. For example, given

```C
void f(array_ptr<int> p : count(len), int len) {
  array_ptr<int> r : count(len) = p;
  ...
}
```

The declared bounds for `r` of `count(len)` are valid because `p` has inferred bounds of `count(len)` The bounds of the left-hand side of the initializer (`count(len)`) imply that the bounds for the right-hand side are valid.