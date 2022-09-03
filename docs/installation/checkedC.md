---
layout: default
title: CheckedC Compiler & 3C
parent: Installation
nav_order: 1
---

# [](#header-1)CheckedC Compiler & 3C

## [](#header-2)Building


### [](#header-3)Basics

You first have to clone the CheckedC clang repo from https://github.com/Vedaant-Rajoo/checkedc-llvm-project.git.

```sh
git clone https://github.com/Vedaant-Rajoo/checkedc-llvm-project.git
cd checkedc-llvm-project

# Get a copy of the Checked C system headers. Use Microsoft's
# "checkedc" repository regardless of which "checkedc-clang"
# repository you use.
git clone https://github.com/microsoft/checkedc llvm/projects/checkedc-wrapper/checkedc
mkdir build && cd build
cmake ../llvm -G Ninja -DLLVM_ENABLE_PROJECTS="clang;clang-tools-extra" -DLLVM_TARGETS_TO_BUILD=X86 -DLLVM_USE_SPLIT_DWARF=ON -DLLVM_OPTIMIZED_TABLEGEN=ON
ninja clang 3c 3Cclangd
```

### [](#header-3)PATH Instructions
{: .text-purple-200}
If you want to use any of the tools you built above to work on your terminal window, you will need to add them to your `PATH` environment variable.
- After sucessfully building do the following:
```sh
cd bin
pwd
```
- This will return the `PATH`(something like `checkedc-llvm-project/build/bin` at the end) of your build files (If you didn't change the directory after building).
- And then set the variable using the command:
```sh
export PATH=$PATH:the/path/you/got
```
#### Caution
{: .text-red-200}
If you already have the normal legacy version of `clang` compiler installed on your system, the new checked version might interfere with its operation. This new version of `clang` is **backward-compatible**, i.e it works with checked and unchecked C code. So remove the old `clang` from your system and set the PATH to your new `clang` compiler using the steps above.

#### TARGETS 
{: .text-blue-100}

- `clang` : This is the checkedC version of clang compiler. You need this to compile and run your converted code.
- `3c` : This is the conversion library our tool is build on top of.
- `3Cclangd` : The LSP server that works with your editor to leverage automated feedback supported conversion. 

<details>
    <summary>Extra Build Options</summary>
    <ul>
  <li>The above instructions already assume the use of the [Ninja](https://ninja-build.org/) build tool; you may have to install it. You can alternatively use `make` (remove `-G Ninja` from the `cmake` command and replace `ninja` with `make`), but Ninja is
  much faster in our experience.</li>
  <li>Pass `-DLLVM_USE_LINKER=lld`. This requires a sufficiently recent
  version of `lld` to be installed on your system.</li>
  <li>Pass `-DLLVM_APPEND_VC_REV=OFF` to turn off embedding of your Git
  head commit ID in the executables and thus avoid the need to re-link
  all of them every time the commit ID changes.</li>
  <li>You might want to use `-DCMAKE_BUILD_TYPE=RelWithDebInfo` if you are running 3C enough between builds</li>
</ul> 
</details>

[See ccache Installation Steps](https://purs3lab.github.io/3clsp/docs/prerequisites.html#ccacheoptional)


[See lld Installation Steps](https://purs3lab.github.io/3clsp/docs/prerequisites.html#lldoptional)



