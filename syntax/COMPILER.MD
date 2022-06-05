# Info about O++ compiler `opp`

> ## Table of contents
> 1. [Overview](#overview)
> 2. [Interpreting mode](#opp-run)
> 3. [Compiling mode](#opp-compile)
> 4. [Creating a project](#opp-new)
> 5. [Inicializing a project](#opp-init)
> 6. [Module path](#opp-path)

## Overview
`opp` is a compiler for O++ language. Besides compiling, it provides an eazy way to manage your code in **projects**.
The compiler has six modes:
- Interpreting mode - runs your code (slow)
- Compiling mode - compiles your code to C and then to binary (fast)
- Creating a project - creates a new O++ project and basic structure
- Inicializing a project - inicializes an existing O++ project for example from github (if not created by `opp new`)
- Show or manage module path - shows or changes module path, where O++ compiler searches for libraries
- Help - shows help (`opp help` or `opp --help`)

## opp run
> ### Arguments
> `opp run <code-file> -b <base-file> -l [lib-file]:[lib-base-file] ...` </br>
> Where: </br>
> $\qquad$ `<code-file>` == the `.opp` file with your main code </br>
> $\qquad$ `-b <base-file>` == the `.bpp` file with your base code </br>
> $\qquad$ `-l [lib-file]:[lib-base-file] ...` == the `.lpp` files with your libraries and base files matching to them </br>
> </br>
> `opp run` when current folder is O++ project.

This runs your code in console. It's interpreted and the compiler is written in C#, so it's slow. Use it only for testing!

## opp compile
> ### Arguments
> `opp compile [-C] [-O] -o [output-file] <code-file> -b <base-file> -l [lib-file]:[lib-base-file] ...` </br>
> Where: </br>
> $\qquad$ `-C` == keep C files from compiling </br>
> $\qquad$ `-O` == keep object files from compiling </br>
> $\qquad$ `-o [output-file]` == the name of the output file </br>
> $\qquad$ `<code-file>` == the `.opp` file with your main code </br>
> $\qquad$ `-b <base-file>` == the `.bpp` file with your base code </br>
> $\qquad$ `-l [lib-file]:[lib-base-file] ...` == the `.lpp` files with your libraries and base files matching to them </br>
> </br>
> `opp compile` when current folder is O++ project.

This compiles your code to C and then to binary. It's fast. Use it for production!

## opp new
> ### Arguments
> `opp new -d [directory='.'] [-l] [-f] <project-name>` </br>
> Where: </br>
> $\qquad$ `-d [directory='.']` == the directory where the project folder will be created </br>
> $\qquad$ `<project-name>` == the name of the project </br>
> $\qquad$ `-l` == creates a library project </br>
> $\qquad$ `-f` == if it's not library, make the project functional </br>

Creates a new O++ project with basic structure in `directory`. If `-l` is provided, it will be a library project.

> ### Basic project structure
> `📁 project-name` </br>
> `└─ 📁 src` </br>
> $\qquad$ `└─ 📄 main.opp` </br>
> $\qquad$ `└─ 📁 bpp` </br>
> $\qquad$ $\qquad$ `└─ 📄 main.bpp` </br>
> $\qquad$ `└─ 📁 lpp` </br>
> `└─ 📁 c` </br>
> `└─ 📁 obj` </br>
> `└─ 📁 bin` </br>
> `└─ 📁 lib` </br>
> `└─ 📄 project.yml` </br>
> `└─ 📄 .oppproject` </br>
> </br>
> ### Functional project structure
> `📁 project-name` </br>
> `└─ 📁 src` </br>
> $\qquad$ `└─ 📁 start` </br>
> $\qquad$ $\qquad$ `└─ 📄 start.opp` </br>
> $\qquad$ $\qquad$ `└─ 📄 start.bpp` </br>
> $\qquad$ `└─ 📁 lpp` </br>
> $\qquad$ $\qquad$ `└─ 📄 main.lpp` </br>
> $\qquad$ `└─ 📁 bpp` </br>
> $\qquad$ $\qquad$ `└─ 📄 main.bpp` </br>
> `└─ 📁 c` </br>
> `└─ 📁 obj` </br>
> `└─ 📁 bin` </br>
> `└─ 📁 lib` </br>
> `└─ 📄 project.yml` </br>
> `└─ 📄 .oppproject` </br>
> </br>
> ### Library project structure
> `📁 project-name` </br>
> `└─ 📁 src` </br>
> $\qquad$ `└─ 📁 lpp` </br>
> $\qquad$ `└─ 📁 bpp` </br>
> `└─ 📁 lib` </br>
> `└─ 📄 project.yml` </br>
> `└─ 📄 .oppproject` </br>

<!--
TODO move to another file
-->

## opp init

## opp path