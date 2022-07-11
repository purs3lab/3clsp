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


<details>
    <summary>Toggle Switch</summary>
    Foldable Content[enter image description here][1]
</details>

{% include compiler.html %}


Checked C adds checking to C to prevent or detect common low-level programming errors. Checked C provides a way for programmers to check that pointer and array accesses stay in bounds at run time. It also checks for memory accesses via null pointers. 

The Checked C extension adds new checked pointer and array types to C. These types do not have undefined behavior, unlike existing C pointer and array types. Runtime errors such as dereferencing a null pointer or accessing out-of-bounds memory result in signals that stop programs. For some pointer and array types, programmers must declare bounds for variables and members with those types to be able to access memory.

The new types include: 
* Single and multi-dimensional arrays with bounds checking. These are specified by placing the keyword `_Checked` before the dimension of the array. For example, `int x _Checked[10]` declares a 10-element integer array with bounds checking.
* The `_Ptr` type for pointers to single objects. Pointer arithmetic is not allowed on these types. For example, `_Ptr<int> p` declares a pointer to a single object.
* The `_Array_ptr` type for pointers to elements of arrays. Pointer arithmetic is allowed on these types. When `_Array_ptr` pointers are used to access memory, they are bounds checked and checked for non-nullness. Programmers must declare the bounds of `_Array_ptr` variables to be able to use them to access memory. The compiler constructs bounds for `_Array_ptr` typed expressions based on the bounds for variables.
* The `_Nt_array_ptr` type for pointers to elements of null-terminated arrays. These are similar to `_Array_ptr` types, with two differences. The element just beyond the declared bounds can be read or have a zero written to it. If the element is non-null, the bounds for the pointer can be widened by 1 element.

The latter two types are associated with bounds declarations, that define how long the pointed-to array can be. For example, `_Array_ptr<int> x : count(10);` is a declaration of variable `x` which is a pointer to an array of size 10.

Programmers can annotate regions of code as checked; e.g., a code block `{ ... }` can be marked `_Checked { ... }`. Checked regions restrict their contents so as to ensure spatial safety; e.g., checked regions may only use checked pointers. Regions of code deemed to be unchecked may freely intermix checked and legacy pointers. This flexibility permits a partial, incremental conversion of programs.

[More Info on CheckedC](https://github.com/secure-sw-dev/checkedc/wiki){: .btn .btn-purple }