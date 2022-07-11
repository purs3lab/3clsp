---
layout: default
title: Examples
parent: Usage
nav_order: 2
---
## [](#header-2) Code Examples

### [](#header-3) Simple Test Project

To make yourself familiar with the usage of the tool, start with a small project with upto 5 **C** files. If you don't have one checkout the following repo for testing purposes. Make sure that you have Bear and make installed on your PC and checkout the pre-requisites for the tool before you start testing and using tool.

[Sample Repository](https://github.com/Vedaant-Rajoo/test3cproject.git){: .btn .btn-purple }

Or just paste the following to get started:

```sh
git clone https://github.com/Vedaant-Rajoo/test3cproject.git
cd test3cproject
bear make
```

After you load in the project in VSCode open up `program1.c` or `program2.c` and run the steps we mentioned earlier in Extension Usage. After the conversion has taken place you can see that the code was successfully converted and that `program2.c` had a root cause that was the result of an unsafe casting. If you proceed and make this pointer non-WILD by choosing the appropriate code action. You can see that an unsafe `z` pointer was now converted into a `checked pointer`.