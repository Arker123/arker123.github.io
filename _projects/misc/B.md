---
title: B-- Compiler
subtitle: Toy programming Language
contributors: Arnav Kharbanda* & Yashasav Prajapati*
date: 2019-11-17
image: ../images/bmm.jpg
carousels: 
  - images: 
    - image: '../images/bmm.jpg'
      desc: B-- Compiler
    # - image: '../images/pp_2.png'
    #   desc: The insides of the pointer
    # - image: '../images/arch.png'
    #   desc: Architecture of the pointer.
order: -70
---

<!-- <iframe width="420" height="315" src="http://www.youtube.com/embed/GQc7L0EPPWk" frameborder="0" allowfullscreen></iframe> -->

### B-- Programming Language Compiler

The **B-- programming language** is a toy language inspired by **BASIC**. I developed a **compiler** for B-- using **Flex** and **Bison** tools, defining the language’s grammar and generating both a **lexical analyzer (scanner)** and a **syntax analyzer (parser)**.

#### Compiler Workflow:
- **Lexical Analyzer**: The lexical analyzer tokenizes the source code by identifying and categorizing keywords, identifiers, operators, and other elements of the code.
  
- **Syntax Analyzer**: The syntax analyzer parses the tokenized source code, generating an **abstract syntax tree (AST)** that represents the structure of the program.

- **Code Generation**: The AST is then used to generate executable code based on the structure and logic of the B-- program.

- **Error Handling**: The compiler also provides meaningful **error messages** to help identify syntax issues in the provided B-- source code.

#### Features of the B-- Compiler:
- **Variables**: Supports scalar numeric variables (Integer, Single Precision, Double Precision) and scalar string variables.
  
- **Operators**: Includes arithmetic operators (`+, -, *, /`) and comparison operators (`=, <>, <, >, <=, >=`).

- **Control Structures**: Supports conditional **IF-THEN** statements and **FOR-NEXT** loops.

- **Input and Output**: Implements **INPUT** for reading data and **PRINT** for outputting values.

- **Arrays**: Allows for arrays with non-default sizes using the **DIM** statement.

- **DATA Statement**: Stores values in memory for later use with the **READ** statement.

- **DEF Statement**: Defines user-defined functions for a numeric variable or pseudo-constants.

- **GOSUB Statement**: Enables subroutine calls with the **GOSUB** statement for modular programming.

### Conclusion:
The development of the B-- compiler was an exciting project, allowing me to dive deep into compiler construction using tools like Flex and Bison. The features of the B-- language, such as its support for variables, control structures, and arrays, make it a simple yet powerful tool for learning and experimenting with basic programming concepts.


