---
layout: default
title: Home
nav_order: 1
description: "This tool helps you convert your unsafe legacy C code to a more memory safe C code"
permalink: /
---

# Enabling conversion of C to Checked C
{: .fs-9 }

3CLSP is a language server protocol plugin that assists you to convert **C** to a memory-safe version called **Checked C**.
{: .fs-5 .fw-300 }

## What is Checked C?
As we all know C is memory unsafe language and can contain serious vulnerabilities such as spatial and temporal memory issues. Checked C is a **safe dialect of C** developed by Microsoft, which prevents spatial memory issues (e.g., buffer overruns, out-of-bounds accesses). Checked C provides **3 pointer annotations**, which developer can use to annotate pointers that will help in preventing spatial issues.

For instance, consider the following example (`foo.c`) that has a out-of-bounds access:
```c
#include <stdlib.h>
int main(void) {
    unsigned s, i;
    char *test;
    scanf("%u %u", &s, &i);
    test = (char*)malloc(s);
    // potential out of bounds access (if i > s)
    if (test) test[i] = 0;
    return 0;
}

```

This bug can be triggered as below:

```
$ gcc foo.c
$ ./a.out 
2 79799979
Segmentation fault (core dumped) // arbitrary memory access
```

The checkedC version of the above code (`foo.checked.c`) would be:
```c
#include <stdlib_checked.h>
int main(void) {
    unsigned s, i;
    // here we are saying that test is an array pointer
    // whose size is present in s.
    _Array_ptr<char> test : count(s) = NULL;
    scanf("%u %u", &s, &i);
    test = (char*)malloc(s);
    // The following issue will be prevented.
    if (test) test[i] = 0;
    return 0;
}

```

Now, if we try to trigger the bug, the program exits **without allowing arbitrary memory access.**

```
$ clang foo.checked.c
$ ./a.out 
2 79799979
Illegal instruction (core dumped) // program exited.
```
<details>
    <summary>More Info on Checked Types</summary>
    There are 3 additional pointer types supported by Checked C.
    <ul>
  <li> _Ptr Type (`_Ptr<int>`) : Regular pointer, i.e., pointer to a single element of the corresponding type.</li>
  <li> _Array_ptr Type (`_Array_ptr<int>`) : The checked version of array pointer, which indicates that the pointer is pointing to an array of elements of corresponding type. This type also includes **count** annotation which says the expression that defines the size (i.e., number of elements) of the corresponding array.</li>
  <li>_Nt_array_ptr Type (`_Nt_array_ptr<char>`) : the checked version of null-terminated array pointer. These are similar to array pointers but include a null character at the end.</li>
</ul>   
</details>


[More Info on CheckedC](https://github.com/secure-sw-dev/checkedc/wiki){: .btn .btn-purple }
