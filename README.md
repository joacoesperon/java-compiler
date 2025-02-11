***

🛠️ **Compiler - Custom Language**
====================================

This project implements a **complete compiler** for a programming language specifically designed for this practice. The compiler covers **all phases of the compilation process**, from lexical analysis to assembly code generation for **Motorola 68000**.

***

📌 **Index**
-------------

*   [Description](#description)
*   [Authors](#authors)
*   [Language Features](#language-features)
*   [Compiler Phases](#compiler-phases)
    *   [Lexical Analysis](#lexical-analysis)
    *   [Syntax Analysis](#syntax-analysis)
    *   [Symbol Table](#symbol-table)
    *   [Semantic Analysis](#semantic-analysis)
    *   [Intermediate Code Generation](#intermediate-code-generation)
    *   [Code Optimization](#code-optimization)
    *   [Assembly Code Generation](#assembly-code-generation)
*   [Installation and Execution](#installation-and-execution)
*   [Code Example](#code-example)
*   [Contact](#contact)

***

📖 **Description**
------------------

This project consists of implementing a **complete compiler**, capable of translating source code written in a **custom programming language** into **Motorola 68000** assembly code.

The compiler is divided into several stages:

*   **Lexical analysis:** Tokenization of the source code.
*   **Syntax analysis:** Construction of the Abstract Syntax Tree (AST).
*   **Semantic analysis:** Type validation and semantic rule checking.
*   **Intermediate code generation:** Production of three-address code (TAC).
*   **Code optimization:** Elimination of redundancies and efficiency improvements.
*   **Translation to assembly:** Conversion into **Motorola 68000** processor instructions.

***

👥 **Authors**
--------------

*   **Joaquín Esperon Solari**
*   **Marc Nadal Sastre Gondar**

***

🚀 **Language Features**
-----------------------------------

The language designed in this project supports:  
✅ **Primitive data types:** `int`, `boolean`  
✅ **Control structures:** `if`, `else`, `while`, `for`  
✅ **Functions with parameters and return values**  
✅ **Functions without return values**  
✅ **Constant declaration (`const`)**  
✅ **Input (`read`) and output (`write`)**  
✅ **Arithmetic operators:** `+`, `-`, `*`  
✅ **Relational operators:** `==`, `!=`, `<`, `>`  
✅ **Logical operators:** `&&`, `||`, `!`  
✅ **Tuple handling (`tuple.get(index)`)**

***

🏗️ **Compiler Phases**
----------------------------

### 🔹 **Lexical Analysis**

Lexical analysis identifies **tokens** in the source code. It is implemented in **scanner.flex**, where **keywords**, **operators**, and **delimiters** are defined using **regular expressions**.

✔️ **Token generation:** `main`, `if`, `else`, `while`, `for`, `read`, `write`, `int`, `boolean`, etc.  
✔️ **Handling of lexical errors:** Unrecognized tokens are reported.  
✔️ **Elimination of comments and whitespace.**

***

### 🔹 **Syntax Analysis**

Syntax analysis uses **Java CUP** to construct the **Abstract Syntax Tree (AST)**.  
✔️ A **LALR grammar** is defined to recognize language structures.  
✔️ **Operator precedence handling.**  
✔️ **Syntax error recovery** using the `error` production.

***

### 🔹 **Symbol Table**

✔️ Implemented as a **hierarchical structure** to handle nested scopes.  
✔️ **Checks for duplicate variables, functions, and constants.**  
✔️ **Allows efficient lookup** of identifiers at different scope levels.

***

### 🔹 **Semantic Analysis**

✔️ **Type checking** in assignments and operations.  
✔️ **Return check in functions** (prohibiting empty `return;`).  
✔️ **Scope restrictions** (`for`, `if`, `while` cannot redeclare parent variables).  
✔️ **Validation of tuple access** (`tuple.get(index)`).

***

### 🔹 **Intermediate Code Generation (TAC)**

✔️ **Translation from AST to three-address code.**  
✔️ **Handling of temporaries** (`t1`, `t2`, ...) to store intermediate calculations.  
✔️ **Label generation** (`e1: skip`) for conditional and unconditional jumps.  
✔️ **Translation of control structures** into efficient code using `goto`.

***

### 🔹 **Code Optimization**

Several techniques were implemented to improve intermediate code efficiency:

✅ **Elimination of unreachable code** (`goto` followed by unnecessary code).  
✅ **Branch reduction** (`if` + `goto` simplifications).  
✅ **Elimination of redundant labels** (labels without references).  
✅ **Copy propagation** (`t1 = 5; x = t1;` → `x = 5;`).  
✅ **Constant folding** (`t1 = 2 + 3;` → `t1 = 5;`).

***

### 🔹 **Assembly Code Generation**

✔️ **Translation to Motorola 68000 assembly.**  
✔️ **Stack and register management (`D0`, `D1`, `A0`)** for operations.  
✔️ **Subroutine generation** (`write_int`, `read_int`).  
✔️ **Organized structure** with `.DATA` for variables and `.TEXT` for instructions.

***

🛠️ **Installation and Execution**
-------------------------------

### 📌 **Instructions**

1️⃣ **Open the project in NetBeans**

*   Clone or download the repository and open it in **NetBeans**.
*   Ensure that the **JDK** is properly configured.

2️⃣ **Compile the project**

*   NetBeans will automatically compile the code upon execution.
*   If necessary, clean and build the project with:  
    **`Run > Clean and Build Project`**

3️⃣ **Run the compiler**

*   In **NetBeans**, locate the class **`Yio.java`**.
*   Right-click and select **"Run File"** (`Shift + F6`).
*   This will start the compiler, allowing analysis and assembly code generation.

3️⃣ **Run assembly code in Easy68K**

***

📝 **Code Example**
------------------------

```cpp
main() {
    int x = 5;
    boolean y = true;

    if (y == true) {
        write(x);
    } else {
        write(0);
    }

    def int add(int a, int b) {
        int ret = a + b;
        return ret;
    }

    int g = 3;
    int h = 5;
    h = add(g, h);
    write(h);

    tuple t = (5, true);
    write(t.get(0));
    write(t.get(1));

    const int con = 2;
    write(con);

    for (int i = 0; i < x; i = i + 1) {
        write(i);
    }
}
```

✔️ **Executes mathematical and boolean operations.**  
✔️ **Includes functions, conditionals, loops, and tuples.**  
✔️ **Generates optimized assembly code for Motorola 68000.**

***

📩 **Contact**
---------------

If you have any questions or suggestions, you can contact the authors:  
📧 **Joaquín Esperon Solari** - joacoesperon1@gmail.com  
📧 **Marc Nadal Sastre Gondar** - parasitohumanitario@gmail.com

***

