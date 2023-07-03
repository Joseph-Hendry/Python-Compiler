# Compiler Readme

## Introduction
This is a compiler template for the later defined language compiler. The compiler supports lexical analysis, syntax analysis, semantic analysis, and code generation.

## Language
This is the language accepted by the compiler:
```
Program = Statements

Statements = Statement (; Statement)*

Statement = If | While | Assignment

If = if Comparison then Statements end

While = while Comparison do Statements end

Assignment = identifier := Expression

Comparison = Expression Relation Expression

Relation = = | != | < | <= | > | >=

Expression = Term ((+ | -) Term)*

Term = Factor ((* | /) Factor)*

Factor = (Expression) | number | identifier
```

## Features
- Lexical analysis: The compiler tokenizes the source code into meaningful tokens.
- Syntax analysis: It parses the tokens according to the grammar rules of the source language.
- Code generation: It generates the corresponding target code based on the analyzed source code.
- Error handling: It detects and reports syntax erros with error messages.

## Requirements
To use the compiler template, you should have the following:
- Python 3 installed
- Jasmin assembler (available at http://jasmin.sourceforge.net/) for translating Java assembly to Java bytecode

## Usage
To use the compiler, follow the provided procedure:
1. Run the compiler using Python 3, passing the program via standard input. The Java assembly should be outputted via standard output. Use the command:
   ```
   python3 compiler.py < program > Program.j
   ```

2. Translate the Java assembly to a Java class file using the Jasmin assembler (available at http://jasmin.sourceforge.net/). Use the command:
   ```
   java -Xmx100m -jar jasmin.jar Program.j
   ```
   This will generate the class file `Program.class`.

3. Run the Java class file using Java, passing the test input via standard input. The result should be outputted via standard output. Use the command:
   ```
   java -Xmx100m Program < test_input > test_output
   ```

## Examples
Here's an example program:

```
read n;
sum := 0;
while n > 0 do
  sum := sum + n;
  n := n - 1
end;
write sum
```
