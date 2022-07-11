---
layout: default
title: Usage
nav_order: 4
has_children: true
---
# [](#header-1) Usage Details

## [](#header-2) Compilation Databases
A compilation database is a **JSON file**, which consist of an array of “command objects”, where each command object specifies one way a translation unit is compiled in the project. Each command object contains the translation unit's main file, the working directory of the compile run and the actual compile command.

3clsp needs a compilation databse to work. A compilation database specifies which files in your project 3c needs to work on. 

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