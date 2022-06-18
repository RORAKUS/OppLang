# Info about O++ compiler `opp`

> ## Table of contents
> 1. [Overview](#overview)
> 2. [Interpreting mode](#opp-run)
> 3. [Compiling mode](#opp-compile)
> 4. [Creating a project](#opp-new)
> 5. [Inicializing a project](#opp-init)
> 6. [Module path](#opp-path)
> 7. [Options](#opp-option)

## Overview
`opp` is a compiler for O++ language. Besides compiling, it provides an eazy way to manage your code in **projects**.
The compiler has six modes:
- Interpreting mode - runs your code (slow)
- Compiling mode - compiles your code to C and then to binary (fast)
- Creating a project - creates a new O++ project and basic structure
- Inicializing a project - inicializes an existing O++ project for example from github (if not created by `opp new`)
- Show or manage module path - shows or changes module path, where O++ compiler searches for libraries
- Help - shows help (`opp help` or `opp --help`)

<span style="color:red;font-size:20px"><strong>Needs gcc to work!</strong></span>

## opp run
> ### Arguments
> `opp run <code-file> -b <base-file> -l [lib-file]:[lib-base-file] ...` <br>
> Where: <br>
> $\qquad$ `<code-file>` == the `.opp` file with your main code <br>
> $\qquad$ `-b <base-file>` == the `.bpp` file with your base code <br>
> $\qquad$ `-l [lib-file]:[lib-base-file] ...` == the `.lpp` files with your libraries and base files matching to them <br>
> <br>
> `opp run` when current folder is nonlibrary O++ project.

This runs your code in console. It's interpreted and the compiler is written in C#, so it's slow. Use it only for testing!

## opp compile
> ### Arguments
> `opp compile [-C] [-O] -o [output-file] <code-file> -b <base-file> -l [lib-file]:[lib-base-file] ...` <br>
> Where: <br>
> $\qquad$ `-C` == keep C files from compiling <br>
> $\qquad$ `-O` == keep object files from compiling <br>
> $\qquad$ `-o [output-file]` == the name of the output file <br>
> $\qquad$ `<code-file>` == the `.opp` file with your main code <br>
> $\qquad$ `-b <base-file>` == the `.bpp` file with your base code <br>
> $\qquad$ `-l [lib-file]:[lib-base-file] ...` == the `.lpp` files with your libraries and base files matching to them <br>
> <br>
> `opp compile` when current folder is O++ project.

This compiles your code to C and then to binary. It's fast. Use it for production!

If this on a library project, it will create a `.opplib` file with all your `.lpp` library paths.

## opp new
> ### Arguments
> `opp new -d [directory='.'] [-l] [-f] <project-name>` <br>
> Where: <br>
> $\qquad$ `-d [directory='.']` == the directory where the project folder will be created <br>
> $\qquad$ `<project-name>` == the name of the project <br>
> $\qquad$ `-l` == creates a library project <br>
> $\qquad$ `-f` == if it's not library, make the project functional <br>

Creates a new O++ project with basic structure in `directory`. If `-l` is provided, it will be a library project. If it's not a library project and `-f` is provided, it will be a functional project. More about projects [here](PROJECT.MD).

## opp init
> ### Arguments
> `opp init -p` <br>
> Use when folder is already a project, but it's not labeled as project.<br>
> <br>
> `opp init [-l] [-f] [directory='.']` <br>
> Where: <br>
> $\qquad$ `-l` == initializes a library project <br>
> $\qquad$ `-f` == if it's not library, make the project functional <br>
> $\qquad$ `[directory]` == what folder will be the project (folder name = project name) <br>

Initializes a new project in `directory`. If the `-p` is used, it only adds`.oppproject` file into that directory.
Otherwise, it adds not only `.oppproject` but also `project.yml` file to that directory.

## opp path
> ### Arguments
> `opp path list` <br>
> Returns a list of all paths where O++ compiler searches for libraries in stdout. <br>
> `opp path add <path>` <br>
> Adds a folder, where O++ compiler searches for libraries. <br>
> `opp path remove <path>` <br>
> Removes a folder from path, where O++ compiler searches for libraries. <br>
> `opp path clear` <br>
> Clears all paths where O++ compiler searches for libraries except of system path. <br>

Compiler stores paths in file. Unremovable default path is `/lib/opp`. This command modifies the path.

## opp option
> ### Arguments
> `opp option compiler <command>` <br>
> Sets C compiler to `command`.