# Info about O++ language
> ## Table of contents
> 1. [What is O++?](#what-is-o++?)
> 2. [O++ parts](#parts)
>    - [Code part](#code)
>    - [Base part](#base)
>    - [Library part](#library)
> 3. [O++ features](#features)
> 4. [Why use O++?](#why-use-o++?)
> 5. [Compiling](#compiling)


## What is O++?
O++ is an **esoteric** programming language, that was made by RORAK in 2022.
It provides an eazy unreadable way to write code, but it is also a powerful tool.
Just give it a try.

## O++ parts
O++ program is dived into two part, and optional one. These parts are [Code](#code-part), [Base](#base-part), and [Library](#library-part).

The most basic program has **two** files: code file with extension `.opp` and base file with extension `.bpp`.
You can also create a library file with extension `.lpp` and with base file with extension `.bpp` and use it in your code.

### Code part
The code part is the most important part of O++. It is the part that you write your code in.
It has extension `.opp` and it contains **instructions** of your code.
This part is the main entry point of every program.

### Base part
As you know, almost every instruction has some **parameters** wich are used to tell what exactly should the instruction do.
The base part sets **registers**, that are used as parameters for instructions. If you use `.` instruction in your code part, control will be passed to the base part. In base part you use `out()` to switch back to the code part.

### Library part
The library part has extension `.lpp`. It's the same as code part, uses same instruction, but **functions** can be defined here.
Also, this isn't executable code, so code can be written only in functions. You can attach library to your code using compiler.
Every library has a base with the same name as the library. In code, used libraries are in `%lib` register.

## O++ features
1. Basic programming language - console input, output, flow control, functions
2. GUI library
3. Working with files
4. Multiplatform
5. Big speed

## Why use O++?
1. Easy to learn
2. Fast
3. Multiplatform
4. Small programs

## Compiling
O++ language provides a program called `opp` (`opp.exe` on windows), that besides compiles your code.

A **run** mode runs your code. It's slow and interpreted. You use `opp run <main.opp> -b <main.bpp> -l [lib.lpp]:[lib.bpp] ...` to run your code.

A **compile** mode compiles your code to C and then to binary. You use `opp compile [-C] [-O output] <main.opp> -b <main.bpp> -l [lib.lpp]:[lib.bpp] ...` to compile your code.
More [here](COMPILER.MD)