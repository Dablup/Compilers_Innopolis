# Compiler Construction S22 course.
Compiler implementation for the Functional Language.
> Semester 6, 3rd study-year, Innopolis University.

This is a project assignment about creating a compiler for the toy funcitional language (similar to Lisp).

*Haskell team* members
- Roman Soldatov 
- Daniil Livitin	
- Timur Nugaev	
- Mikhail Martovitsky


## General usage
The program can run with provided command line arguments. You can specify the path to the source program and compiler compiles it. Alternatively, in [Main.java](/src/main/java/Main.java) you can specify the path in `defaultPath` variable: `String defaultPath = <path to the source program>`

## Lexical analysis
In [lexical_analysis](/src/main/java/lexical_analysis) folder you can find a **Lexer** which tokenizes an input from the source program file. The lexer was automatically created with a use of [JFlex](https://jflex.de) scanner. Tokens are defined in a [lexer.flex](/src/main/java/lexical_analysis/lexer.flex) file. Their class representation is stored in the [tokens](/src/main/java/lexical_analysis/tokens) folder.

Run `jflex lexer.flex` command in your terminal to generate [Lexer.java](/src/main/java/lexical_analysis/Lexer.java) java file. We are using `lexer.tokenize()` and `lexer.getTokens`. To parse and get a list of all found tokens.

## Syntax analysis
In [syntax_analysis](/src/main/java/syntax_analysis) folder you can fina a **Parser** which creates AST via `Parser.makeAST(<sourceProgramPath>)` method. This parser was generated by [Bison](https://www.gnu.org/software/bison/). The grammar is described in [Parser.y](/src/main/java/syntax_analysis/Parser.y) file. AST contians of nodes which represent particular syntax subtrees. You can find them in [node](/src/main/java/syntax_analysis/node) folder.

We use [LexerAdapter.java](/src/main/java/syntax_analysis/LexerAdapter.java) class which connects our [Lexer.java](/src/main/java/lexical_analysis/Lexer.java) and implements necessary methods from `Parser.Lexer` [interface](https://www.gnu.org/software/bison/manual/bison.html#Java-Parser-Interface).

Run `bison Parser.y -L java` to create [Parser.java](/src/main/java/syntax_analysis/Parser.java) parser.
