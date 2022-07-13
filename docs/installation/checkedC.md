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
cmake ../llvm -G Ninja -DLLVM_ENABLE_PROJECTS="clang,3c,clang-tools-extra" -DLLVM_TARGETS_TO_BUILD=X86 -DLLVM_USE_SPLIT_DWARF=ON -DLLVM_OPTIMIZED_TABLEGEN=ON
ninja clang 3c 3Cclangd
```

<details>
    <summary>Extra Build Options</summary>

- The above instructions already assume the use of the [Ninja](https://ninja-build.org/) build tool; you may have to install it. You can alternatively use `make` (remove `-G Ninja` from the `cmake` command and replace `ninja` with `make`), but Ninja is
  much faster in our experience.

- Pass `-DLLVM_USE_LINKER=lld`. This requires a sufficiently recent
  version of `lld` to be installed on your system.


- Pass `-DLLVM_APPEND_VC_REV=OFF` to turn off embedding of your Git
  head commit ID in the executables and thus avoid the need to re-link
  all of them every time the commit ID changes.

- You might want to use `-DCMAKE_BUILD_TYPE=RelWithDebInfo` if you are running 3C enough between builds
</details>

[See lld Installation Steps]({{ site.baseurl }}{% link docs/prerequisites.md#lldoptional %})



