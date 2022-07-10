---
layout: default
title: CheckedC Compiler & 3C
parent: Installation
nav_order: 1
---

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
cmake ../llvm -G Ninja -DLLVM_ENABLE_PROJECTS="clang,3c,clang-tools-extra"
ninja clang 3c 3Cclangd
```

### [](#header-3)Build Options

Because all of LLVM and clang are built as dependencies, this may
consume up to ~50 GB of disk space, take several hours (depending on
the speed of your computer), and require ~10 GB of RAM. Incremental
builds will usually be faster. Here are some things you can do that
may reduce the build time and/or peak memory use:

- The above instructions already assume the use of the
  [Ninja](https://ninja-build.org/) build tool; you may have to
  install it. You can alternatively use `make` (remove `-G Ninja` from
  the `cmake` command and replace `ninja` with `make`), but Ninja is
  much faster in our experience.

- Pass `-DLLVM_TARGETS_TO_BUILD=X86` (or whatever your machine's
  architecture is, e.g., `ARM`) to `cmake` to build only the parts of
  `clang` needed to compile programs for your machine.

- Pass `-DLLVM_USE_LINKER=lld`. This requires a sufficiently recent
  version of `lld` to be installed on your system.

- Pass `-DLLVM_USE_SPLIT_DWARF=ON`. We have tested the build with this
  option, but it may affect some debugging tools.

- Pass `-DLLVM_OPTIMIZED_TABLEGEN=ON`.

- Pass `-DLLVM_APPEND_VC_REV=OFF` to turn off embedding of your Git
  head commit ID in the executables and thus avoid the need to re-link
  all of them every time the commit ID changes.

(The reference for improving build performance is [this LLVM
page](https://www.llvm.org/docs/GettingStarted.html#common-problems),
but we have attempted to describe the most promising options here.)

You might want to use `-DCMAKE_BUILD_TYPE=RelWithDebInfo` if you are
running 3C enough between builds that the faster running time
outweighs the slower build time or you simply want to test a release
build of 3C, assuming that's what end users will eventually be
encouraged to use.


