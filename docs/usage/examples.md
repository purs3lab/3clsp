---
layout: default
title: Usage Examples
parent: Usage
nav_order: 1
youtubeId: H1LyfBN02Tk
---

# [](#header-1) Usage Details

### [](#header-3) Simple Test Project

To make yourself familiar with the usage of the tool, start with a small project with upto 5 **C** files. Make sure that you have `Bear` and `make` installed on your PC and checkout the pre-requisites for the tool before you start testing and using tool.

[Sample Repository](https://github.com/Vedaant-Rajoo/test3cproject.git){: .btn .btn-purple }

Or just paste the following to get started:

```sh
git clone https://github.com/Vedaant-Rajoo/test3cproject.git
cd test3cproject/simple
bear make
code .
```
- This opens up Visual Studio Code for the `simple` project.
- Navigate to the `program.c` file.
- This starts up the server (`3Cclangd`).
- Press `Ctrl+Shift+P`, this opens up the command palette.
- `Run 3c on the project`

> Take a look at the video below if you come across any problems.
{% include youtube.html id='H2WfbnFl4cQ' %}

### [](#header-3) Second Simple Project

This folder consists of two interrelated `C` files.

- If you already cloned the repo mentioned above.
- Navigate to `simple2` folder and repeat `bear make`.
- Repeat the steps as above.

We also have a video tutorial to help you with the conversion process
{% include youtube.html id='srlvMS5wAgM' %}
### [](#header-3) tiny-bignum-c Project
This folder is widely used `C` library and will serve as an entry point for your project conversion needs.

- Navigate to the `tiny-bignum-c` folder.
- `bear make` to create the compilation database.
- After the diagnostics appear, solve them one by one with the help of code actions.

Beware this is a big library and our tool can't convert the code completely. Even after the root causes are solved, the code won't compile because it needs a little refactoring. Refer to [this link](https://github.com/secure-sw-dev/checkedc-tiny-bignum-c#initial-conversion) for information on the changes to make before it can successfully compile.

## [](#header-2) Post Conversion
{: .text-green-200}
- If you're satisfied with your conversion, save the project (using `Ctrl+S`) so that the changes are permanant (You can skip this step if you have `Auto Save` turned on in VSCode).
- Compile your code using `clang file-name.c` in your terminal.

#### Caution
{: .text-red-200}
The code might not compile because of some minor changes that our tool can't write by it's own. Some conversion requires refactoring that helps compile the file. If you need help with your project conversion, join our [discord server](https://purs3lab.github.io/3clsp/docs/Contact.html#-discord-server) for tips and help from checkedC developers and admins.