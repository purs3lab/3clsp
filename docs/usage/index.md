---
layout: default
title: Usage
nav_order: 4
has_children: true
---
# [](#header-1) Usage Details

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





### [](#header-3)Creating Compile DBs
Compile databses can be lengthy to write and can become complicated at times. If your project uses build systems like **make, boost, SCons etc.** You can leverage the use of a tool called **Bear** that generates a compilation database for clang tooling. Some build system natively supports the generation of JSON compilation database. For projects which does not use such build tool, Bear generates the JSON file during the build process.

[Bear](https://github.com/rizsotto/Bear){: .btn .btn-purple }

Bear is [packaged](https://repology.org/project/bear/versions) for many
distributions. Check out your package manager.

For example on Ubuntu/Debian based OS: 
```sh
sudo apt install bear
```
should do the trick.

* * *
#### [](#header-4)How to Use Bear

After installation the usage is like this:
```sh
 bear -- <your-build-command>
```

The output file called `compile_commands.json` is saved in the current directory.

For more options you can check the man page or pass `--help` parameter. Note
that if you want to pass parameter to Bear, pass those _before_ the `--` sign,
everything after that will be the build command. 