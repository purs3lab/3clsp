# LSP3C
Implementing 3C into clangd LSP Server.

## Setup Instructions

For the setup you are going to have to install the 3Cclangd version of `clangd` and to test this LSP server we need a client. We use VSCode as our choice of client. So for setting up the client we install the clangd `extension` on our systems.

### Server Side Installation


[Link to 3Cclangd Repo](https://github.com/Vedaant-Rajoo/checkedc-llvm-project/tree/vrajoo-adventure)

We follow the similar steps as building `clangd` mentioned in the repository. But we include an additional target while installing and replace `clangd` with `3Cclangd`

##### To Build 
```
cmake ../llvm -G Ninja -DLLVM_USE_LINKER=lld -DLLVM_ENABLE_PROJECTS="clang,3c,clang-tools-extra"

```
You can use other cmake flags to optimize the build process further mentioned in the original repo. (Like optimized TableGen, build caches etc.)

##### To install

```
ninja clang 3c 3Cclangd
```

### Client Side Installation

[Link to Extension Repo](https://github.com/Vedaant-Rajoo/vscode-clangd/tree/vrajoo)

##### Requirements

* VS Code
* node.js and npm

##### Steps

1. Make sure you disable the installed `vscode-clangd` extension in VS Code. (As an alternative you can install the insiders version of VSCode to keep separate editors for testing and developing)
2. Make sure you have clangd in `/usr/bin/clangd` or edit `src/clangd-context.ts` to
point to the binary (It's stored in a variable called `clangdPath`. `Ctrl+F` for this variable and change the string and include the path to your 3Cclangd executable, which is usually in `build-path/bin/3Cclangd`).
3. To start a development instance of VS code extended with this, run:

```bash
   $ cd vscode-clangd
   $ npm install
   $ code .
   $ npm run esbuild
   # When VSCode starts, press <F5>.
```
4. Don't forget to build the extension using `npm run esbuild` which creates the scripts for loading in the extension in a developemnt host different than your editor.


## Next Steps
1. Make sure you have a `compile_commands.json`. The server won't work until you have a compile database. You can use [Bear](https://github.com/rizsotto/Bear) to generate compile databases from your makefiles or build instructions.
2. The server part of 3C will overwrite your project files, so make sure to create a copy beforehand to not lose your progress. (We are currently working on a backup function built into VSCode that can automate this process for you).
3. Once done and in the developement Host of VSCode. Open the command pallete(`Ctrl+Shift+P`) and search for `Run 3c` and run the command. This might take a while depending on your project size and the scope of your project depth.
4. This command will run 3c and populate the root cause diagnostics for you. You can use the code actions for each pointer to make it non-wild which would run 3C again automatically and remove root-cause wild pointers with the help of developer(manual) input.

