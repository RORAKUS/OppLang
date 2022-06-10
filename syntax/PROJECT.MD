# O++ projects

> ## Table of contents
> 1. [Project Types](#project-types)
> 2. [Basic project](#basic-project)
> 3. [Library project](#library-project)
> 4. [Functional project](#functional-project)
> 5. [Project actions](#project-actions)
> 6. [Project.yml](#project-yml)

## Project Types
There are three main project types: basic, library and functional. Basic project are normal projects, uses mainly `.opp` and `.bpp`.
Library project uses only `.lpp` and are not runnable - they compile into `.opplib` library file.
Functional project is project that uses `.lpp` and `main` function in it. It also contains `.opp` and `.bpp` file, but they doesn't contain code.

## Basic project
> ### Structure
> `📁 project-name` <br>
> `└─ 📁 src` <br>
> $\qquad$ `└─ 📄 main.opp` <br>
> $\qquad$ `└─ 📁 bpp` <br>
> $\qquad$ $\qquad$ `└─ 📄 main.bpp` <br>
> $\qquad$ `└─ 📁 lpp` <br>
> `└─ 📁 c` <br>
> `└─ 📁 obj` <br>
> `└─ 📁 bin` <br>
> `└─ 📁 lib` <br>
> `└─ 📄 project.yml` <br>
> `└─ 📄 .oppproject` <br>

Basic project contains five folders. `src` folder contains `main.opp` file, where the main code is in, then `bpp` folder with base files and `lpp` folder with library files.

`c` folder is created only when `compiler.keep-c-files` option in `project.yml` is set to `true`. It contains C files, that are then compiled into object files.

`obj` folder contains `.o` or `.obj` files, that are compiled into binary files.

`bin` folder contains binary files with extension, that is defined in `compiler.extension` option in `project.yml`.

`lib` folder contains external `.lpp` or `.opplib` files, that are used in your project.

`project.yml` file contains project configuration. More information about it can be found in [Project.yml](syntax/PROJECT.MD).

`.oppproject` file is used only for compiler to know that the folder is an O++ projcect.

## Library project
> ### Structure
> `📁 project-name` <br>
> `└─ 📁 src` <br>
> $\qquad$ `└─ 📁 lpp` <br>
> $\qquad$ `└─ 📁 bpp` <br>
> `└─ 📁 fin` <br>
> `└─ 📁 lib` <br>
> `└─ 📄 project.yml` <br>
> `└─ 📄 .oppproject` <br>

Library projects don't contain `.opp` or `.bpp` files - it's just a library. The library is compiled into `.opplib` file, that can be used in other projects.

`src` folder contains `lpp` and `bpp` files.

`fin` folder contains final `.opplib` files.

`lib` folder contains external `.lpp` or `.opplib` files, that are used in your project.

`project.yml` and `.oppproject` is used same way as in basic project.

## Functional project
> ### Structure
> `📁 project-name` <br>
> `└─ 📁 src` <br>
> $\qquad$ `└─ 📁 start` <br>
> $\qquad$ $\qquad$ `└─ 📄 start.opp` <br>
> $\qquad$ $\qquad$ `└─ 📄 start.bpp` <br>
> $\qquad$ `└─ 📁 lpp` <br>
> $\qquad$ $\qquad$ `└─ 📄 main.lpp` <br>
> $\qquad$ `└─ 📁 bpp` <br>
> $\qquad$ $\qquad$ `└─ 📄 main.bpp` <br>
> `└─ 📁 c` <br>
> `└─ 📁 obj` <br>
> `└─ 📁 bin` <br>
> `└─ 📁 lib` <br>
> `└─ 📄 project.yml` <br>
> `└─ 📄 .oppproject` <br>

Functional project is basically the same as basic project. The only difference is that in `src` folder there is `start` folder, where the starter `.opp` and `.bpp` files are located. The main code is in `lpp` and `bpp` folder of the `src` folder.

## Project actions
Projects can be compiled or ran. To compile basic or functional project you need to run `opp compile` command. It will create `.c` file, if `compiler.keep-c-files` option is set to `true` in `project.yml` file. Then it will compile `.c` file into `.o` or `.obj` file, and then it will link `.o` or `.obj` file into binary executable file.

If you run `opp compile` on a library project, it will compile library into `.opplib` file.

To run project you need to run `opp run` command. It will **interpret** these files. <span style='color: red'><strong>LIBRARY FILES CANNOT BE RAN!</strong></span>

## Project yml

