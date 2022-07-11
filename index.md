---
layout: default
title: Home
nav_order: 1
description: "This tool helps you convert your unsafe legacy C code to a more memory safe C code"
permalink: /
---

# A better &  easier way to convert your unsafe C code
{: .fs-9 }

3CLSP gives you the power to convert your **legacy C code** to a memory-safe version of C called **CheckedC**. 
{: .fs-6 .fw-300 }

## Introduction
CheckedC was developed by Microsoft as an extension to the regular **C** we know and love but adds checking to C to detect or prevent common programming errors such as buffer overruns, out-of-bounds memory accesses, and incorrect type casts.

Check Out the Following example for a buffer Overrun example on Legacy C:
```c
#include <string.h>
int main(void) {
    char test[10];
    strcpy(test, "This will overrun the Buffer");
}

```

The checkedC version of the above code would be:
```c
#include <string_checked.h>
int main(void) {
    _Nt_array_ptr<char> test: count(10) = test;
    strcpy(test, "This will overrun the Buffer");
}

```
<details>
    <summary>More Info on Checked Types</summary>
    <ul>
  <li> _Ptr Type : The checked version of the normal star pointer.</li>
  <li> _Array_ptr Type : The checked version of array pointers, these also include using 'count' as a way to define bounds as shown in above example.</li>
  <li>_Nt_array_ptr Type : the checked version of null-terminated array pointer. These are similar to array pointers but include a null character at the end.</li>
</ul>   
</details>


[More Info on CheckedC](https://github.com/secure-sw-dev/checkedc/wiki){: .btn .btn-purple }

<details>
    <summary>Toggle Switch</summary>
    Foldable Content[enter image description here][1]
</details>