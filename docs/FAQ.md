---
layout: default
title: FAQs
nav_order: 6
---

## My `clangd` server won't start up?
{: .text-purple-000}
The tool is still in development and may crash from time to time. Although them ain reason for a crash maybe the absence of a compile database. Make sure that your folder has a `compile_commands.json`. 

## My Code won't compile after conversion?
{: .text-purple-000}
The tool tries it's best to convert as much code as possible. It fails to convert code that requires major refactoring. If you're converting `tiny-bignum-c`, visit [this link for more info.](https://github.com/secure-sw-dev/checkedc-tiny-bignum-c#initial-conversion). Also make sure that you have the correct `clang` in your `PATH`. 

## Clang: Command not found.
{: .text-purple-000}
This error states that the `clang` compiler executable was not found. Make sure you followed the [PATH instructions](https://purs3lab.github.io/3clsp/docs/installation/checkedC.html#path-instructions), as they are vital to your clang working in your terminal window.

## I get Compilation Errors while using the tool to convert.
{: .text-purple-000}
If you are trying to convert libraries, they have build instructions that are strict and allow no errors or warnings. This is done because of the safe usage of the library. But our tool, which extensively works on a compilation database doesn't need these strict instructions. Take a look at the steps we took [here](https://github.com/purs3lab/oopsla22-3c-artifact/blob/main/3c-actions-old-fork/.github/workflows/exhaustivestats.yml#L3231) to make sure **icecast** was safe to convert without compilation errors. If you still need help, join our discord server and ping our admins.
