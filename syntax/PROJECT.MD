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

`.oppproject` file is used only for compiler to know that the folder is an O++ project.

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
> ### Basic project.yml
> ```yml
> name: <project-name>
> author: <username>
> version: 0.0.1-SNAPSHOT
> library: false
> compiler:
>   extension: null
>   keep-c-files: false
>   delete-object-files: false
>   wipe-binaries: false
> files:
>   source:
>       main: src/main.opp
>       main-base: src/bpp/main.bpp
>       base: src/bpp
>       libs: src/lpp
>   c: c
>   objects: obj
>   binary: bin
>   external-libraries: lib
> additional-libraries: null # + all in opp path
> ```
> Where `<project-name>` is the name of the project and `<username>` is `$USERNAME` or `%USERNAME%`.
> You can add additional libraries to your project or specify an extension for the executable.
> 
> ### Library project.yml
> ```yml
> name: <project-name>
> author: <username>
> version: 0.0.1-SNAPSHOT
> library: true
> compiler:
>   extension: .opplib
>   wipe-binaries: false
> files:
>   libraries: src/lpp
>   bases: src/bpp
>   final-lib: fin
>   external-libraries: lib
> additional-libraries: null # + all in opp path
> ```
> Where `<project-name>` is the name of the project and `<username>` is `$USERNAME` or `%USERNAME%`.
> You can add additional libraries to your project. **THIS KIND OF PROJECT CANNOT BE RAN.**
> 
> ### Functional project.yml
> ```yml
> name: <project-name>
> author: <username>
> version: 0.0.1-SNAPSHOT
> library: false
> compiler:
>   extension: null
>   keep-c-files: false
>   delete-object-files: false
>   wipe-binaries: false
> files:
>   source:
>       main: src/start/start.opp
>       main-base: src/start/start.bpp
>       base: src/bpp
>       libs: src/lpp
>   c: c
>   objects: obj
>   binary: bin
>   external-libraries: lib
> additional-libraries: null # + all in opp path
> ```
> The same as basic project, only some values changed.

Project.yml is a configuration file. Every O++ project must have it. Here are the values explained: <br>
+ `name` is the name of the project and the first part of the name of the executable - **use lowercase letters and avoid blanks**
+ `author` is an author of the project. It's not required.
+ `version` is the version of the project. Version rules:
  - There are three numbers, that can be from 0 to 255. 
  - The **first number** is the main version of the program. Prerelease uses 0, first release 1. Bigger numbers only with solid changes to the program.
  - The **second number** is the feature/update version. With new bigger features or updates it increases.
  - The **third number** is basically the bugfix or slight change version. Every time you change code but not the first two numbers, change it.
  - The word following after `-` can be **SNAPSHOT** or **RELEASE**. It speaks for itself.
+ `library` says if it's a library project or not
+ `compiler.extension` is the extension of final executable, or `.opplib` for libraries.
+ `compiler.keep-c-files` *(only for non-library projects)* says if compiler keeps `.c` files (in `[files.c]`)
+ `compiler.delete-object-files` *(only for non-library projects)* says if compiler delets object files in `[files.c]`. If set to true, `obj` folder is deleted
+ `compiler.wipe-binaries` says if the compiler firstly wipe `[files.binary]` or `[files.final-lib]` before creating one
+ `files.source.main` *(only for non-library projects)* is the name of main `.opp` file.
+ `files.source.main-base` *(only for non-library projects)* is the name of base for `[files.source.main]`.
+ `files.source.base` *(only for non-library projects)* is the name of the folder with base files (for libraries)
+ `files.source.libs` *(only for non-library projects)* is the name of the folder with `.lpp` files
+ `files.c` *(only for non-library projects)* is the name of the folder where C files are stored
+ `files.objects` *(only for non-library projects)* is the name of the folder where object files are stored
+ `files.binary` *(only for non-library projects)* is the name of the folder where executable binaries are stored
+ `files.libraries` *(only for library projects)* is the name of the folder where the source libraries are stored
+ `files.bases` *(only for library projects)* is the name of the folder where source bases for libraries are stored
+ `files.final-lib` *(only for library projects)* is the name of the folder where final `.opplib` files are stored
+ `files.external-libraries` is the name of the folder where external library `.lpp:.bpp` or `.opplib` files are stored
+ `additional-libraries` is an array of libraries, that are added to your project. Example of elements: `/lib/lo.lpp:/lib/lo.bpp`, `/lib/lo.opplib`