# Code part syntax

> ## Table of contents
> 1. [How it works](#basic-info)
> 2. [`.` instruction](#dot-instruction)
> 3. [`;` instruction](#semicolon-instruction)
> 4. [`,` instruction](#comma-instruction)
> 5. [`!` instruction](#bang-instruction)
> 6. [`~` instruction](#tilde-instruction)
> 7. [`$` instruction](#dollar-instruction)
> 8. [`%` instruction](#percent-instruction)
> 9. [`@` instruction](#at-instruction)
> 10. [`#` instruction](#hash-instruction)
> 11. [`§` instruction](#paragraph-instruction)
> 12. [`+`, `-`, `*`, `/` instructions](#arithmetic-instructions)
> 13. [`&`, `|`, `^` instructions](#bitwise-instructions)
> 14. [`=`, `>`, `<` instructions](#comparison-instructions)
> 15. [`[`, `]` instructions](#loop-instructions)
> 16. [`(`, `)` instructions](#command-group-instructions)
> 17. [`'` instruction](#quote-instruction)
> 18. [`:` instruction](#colon-instruction)
> 19. [Quantity modifiers](#quantity-modifiers)
> 20. [Base address modifiers](#base-address-modifiers)
> 21. [Blocks with base section](#blocks-with-base-section)

## Basic info
O++ program is mainly divided into 2 sections, every section in one file. Firstly the **code** section (`.opp` file) and secondly the **base** section (`.bpp` file). This file is about the code section. It contains instruction - one character = one instructions (exception - modifiers). Every instruction need some operands, for example print instruction need two operands - what to print and where to print. These operands are set in the base section. You give control to the base section with special base instruction. When any instruction from the code section is executed operand values are taken from the base section and used.

## Dot instruction
The dot instruction is used to pass the control to the base section, until a special base instruction is executed. When that happens, control is passed back to the code section.

## Semicolon instruction
> ### Uses
> `%in` (`"@`) - from where it reads the input <br>
> **Returns** `%r` (`"@`) - what it read <br>

The semicolon instruction is used to read line from console, file etc...

## Comma instruction
> ### Uses
> `%out` (`"@`) - where it writes the output <br>
> `%1` (`"@`) - what it writes <br>

The comma instruction is used to write line to console, file etc...

## Bang instruction
> ### Uses
> `%err` (`"@`) - where it writes the exception <br>
> `%1` (`"@`) - the exception message <br>

The bang instruction sets `%e[0]` to 1, `%e[1]` to the exception message. If `%a` is 1, program ends and the exception message is written to the console, file etc...

## Tilde instruction
> ### Uses
> `%n` (`"@`) - the name of the function to call <br>
> `%1, %2, %3 ...` (`$@`) - the arguments passed to the function <br>
> **Returns** `%r` (`$@`) - the return value of the function <br>

The tilde instruction is used to call a function from external `.lpp` library. If the function is in function group, separate the group name and function name with `/`.

## Dollar instruction
> ### Uses
> `%n` (`"@`) - the name of the variable to create <br>
> `%t` (`@@`) - the type of the variable to create <br>

The dollar instruction is used to create a variable. The variable is stored **on the stack**, so it can be used only in the current block (`[` `]`, `(` `)` or `{` `}` in `.lpp`).

## Percent instruction
> ### Uses
> `%n` (`"@`) - the name of the variable to create <br>
> `%t` (`@@`) - the type of the variable to create <br>

The percent instruction is used to create a variable. The variable is stored **in the memory**, so it can be used **from anywhere** in the program.

## At instruction
> ### Uses
> `%n` (`"@`) - the name of the variable to set <br>
> `%1` (`$@`) - the value to set (**the value of `%1` is copied to the variable**) <br>

The at instruction is used to set the value of a variable. The value is copied from a register and stored in the variable.

## Hash instruction
> ### Uses
> `%n` (`"@`) - the name of the variable to return <br>
> **Returns** `%r` (`$@`) - the **address** of the variable <br>

The hash instruction is used to retrieve an address of a variable.

## Paragraph instruction
> ### Uses
> `%n` (`"@`) - the name of the variable to cast <br>
> `%t` (`@@`) - a new type the variable should have <br>

The paragraph instruction is used to cast a variable to other type.

## Arithmetic instructions
> ### Uses
> `%1` (`$@`) - the first operand <br>
> `%2` (`$@`) - the second operand <br>
> **Returns** `%r` (`$@`) - the result of the operation <br>

Arithmetic instructions (`+`, `-`, `*`, `/`) are used to perform arithmetic operations on two operands.
<!-- TODO add possible cases -->
