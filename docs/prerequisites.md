---
layout: default
title: Pre-Requisites
nav_order: 2
---

# Pre-Requisites
{: .no_toc }

Before you start converting your code, you need to follow some simple steps to get your system ready for this tool.
{: .fs-6 .fw-300 }

#### [](#header-4) OS Supported

> Due to the restrictions by Microsoft the tool only works on Linux and Windows based operating systems.
> Basic installation of Linux and Windows OS makes sure that a C compiler and other basic build tools are pre-installed.

## [](#header-2) Basic Tools

Make sure your system has basic tools like **python,git,curl etc** and the following libraries and tools installed before you proceed.

### [](#header-3)VSCode
Visual Studio Code is a code editor developed by Microsoft and works best when using this tool, but any other code editor that supports **LSP** would work. For the sake of easeness and it's popularity we have just published our extension on the Visual Studio Marketplace. But in the next few releases we might release it to other platforms.

[VSCode](https://code.visualstudio.com/download){: .btn .btn-purple }

### [](#header-3)CMake

For Linux, install CMake 3.8 or later. For Windows, CMake is bundled as part of your Visual Studio install.

### [](#header-3)Ninja

This tool will build the compiler and all other supporting tools on your system.

[Ninja](https://github.com/ninja-build/ninja/releases){: .btn .btn-purple }

**Ninja** is also packaged by major packaged mangaers on UNIX OSes. For example on Ubuntu, you can :

```sh
sudo apt install ninja-build
```
### [](#header-3)Bear
3clsp needs a compilation databse to work. Bear uses your build command to automatically create CompDBs.

```sh
sudo apt install bear
```
[Bear Repo](https://github.com/rizsotto/Bear){: .btn .btn-purple }

Bear is [packaged](https://repology.org/project/bear/versions) for many distributions. Check out your package manager.


<details>
    <summary><p id="#header-3">CCache(Optional)</p></summary>
    Foldable Content[enter image description here][1]
</details>
### [](#header-3)Ccache (OPTIONAL)
Install `ccache` to speed up the compiler build on Linux and
MacOS. [ ccache](https://ccache.samba.org) is a smart cache for GCC or Clang. It
works as a shim, and uses the hash of source files and their included headers
and build options to decide if an output needs recompiling, instead of file
modification time (which CMake uses). In some circumstances, this can cut
second-build (i.e. `ninja` where some of the files are already built) time down
from 5 minutes to 30 seconds. This still depends on how your header files and
includes are organized. Moreover, there are ways to share and control the size
of the cache directory, which is where `ccache` stores a copy of any object
files it has compiled.

```sh
sudo apt install ccache
```

### [](#header-3)lld (OPTIONAL)
LLD is a new, high-performance linker. It is built as a set of reusable components which highly leverage existing libraries in the larger LLVM Project. 


```sh
sudo apt update
sudo apt install lld
```