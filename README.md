# Lisp Interpreter Project Documentation

## Overview

This project is an implementation of a Lisp interpreter written in C. The interpreter supports basic Lisp operations, expressions, and error handling. The goal of this project is to build a functional Lisp-like language with features such as symbolic expressions, mathematical operations, and list manipulation.

Following [Build Your Own Lisp](https://buildyourownlisp.com/contents) guide. I decided to create this project as I wanted to learn C programming and was interested in the idea of building a language.

## Features (Current Progress)

- Basic numeric operations (`+`, `-`, `*`, `/`, `%`)
- Symbolic expressions (S-Expressions) and quoted expressions (Q-Expressions)
- Error handling for invalid operations
- List operations such as `head`, `tail`, `join`, and `eval`
- Memory management to prevent leaks
- Cross-platform compatibility (Windows and UNIX-based systems)

## Dependencies

- **MPC (Micro Parser Combinator)** for parsing Lisp expressions
- **Standard C libraries** for memory allocation, I/O, and error handling
- **editline library** for command-line interaction (on UNIX-based systems)

## Compilation and Setup

### Prerequisites

Ensure you have a C compiler installed (e.g., GCC or Clang). On Windows, you may need MinGW or an equivalent compiler.

### Compilation Steps

```sh
# Clone the repository
git clone <repository-url>
cd <repository-folder>

# Compile using GCC
gcc -std=c99 -Wall -o lisp_interpreter main.c mpc.c -ledit -lm

# Run the interpreter
./lisp_interpreter
```
On Windows, use:
```sh
gcc -std=c99 -Wall -o lisp_interpreter main.c mpc.c -lm
```

## Usage

Once the interpreter is running, you can enter lisp expressions in the command line:
```lisp
> (+ 1 2 3)
6
> (list 1 2 3)
{1 2 3}
> (head {1 2 3})
1
> (tail {1 2 3})
{2 3}
> (/ 10 0)
Error: Division by zero!
```

## Code Structure

### `lval` Structure
The `lval` struct represents a Lisp value and supports different types:

- `LVAL_NUM` (Numeric values)
- `LVAL_ERR` (Error messages)
- `LVAL_SYM` (Symbols)
- `LVAL_SEXPR` (S-expressions)
- `LVAL_QEXPR` (Q-expressions)

### Core Functions

- `lval_num(long x)`: Creates a numeric Lisp value.
- `lval_err(char* m)`: Creates an error message.
- `lval_sym(char* s)`: Creates a symbolic expression.
- `lval_sexpr()`: Creates an empty S-expression.
- `lval_qexpr()`: Creates an empty Q-expression.
- `lval_add(lval* v, lval* x)`: Adds an element to an expression.
- `lval_pop(lval* v, int i)`: Removes and returns an element from an expression.
- `lval_take(lval* v, int i)`: Removes an element and deletes the rest.
- `lval_eval(lval* v)`: Evaluates an expression recursively.
- `builtin_op(lval* a, char* op)`: Performs mathematical operations.

## Planned Features

- Implement variable definition and environment handling
- Add lambda functions for user-defined operations
- Add conditionals
- Add string handling

