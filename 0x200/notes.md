# 0x200 - Programming

## 0x210 - What is programming

- Series of statements written in a specific language
- TO instruct a computer to do something it must be written in its language
- Assembler
  - Translantes assembly language into machine readable code
  - Assembly language is less cryptic than machine code, but still not intuitive
- Compiler
  - Converts high level languages into machine code
  - High level languages are more intuitvie, readable, etc. but still must follow strict rules about how instructions are worded

## 0x220 - Pseudo-code

- Normal langague (english for example) arranged with a structure similar to the high level language
- Pseudo code isin't well defined.. most people write it differently

## 0x230 - Control Structures

- Control structures change the flow of the program's execution
- Without control stuctures, programs would run in sequential order

### 0x231 - If, Then, Else

`if (condition) then`
`{`
`Set of isntructions to execute if condition is met;`
`}`
`else`
`{`
`set of instructions to execute if condition is not met;`
`}`

- C like pseudo-code example:
- Every instruction ends in a semicolon
- Instructions are grouped by curly braces and indentation
`Drive down Main Street;`
`If (street is blocked)`
`{`
`    Turn right on 15th Street;`
`    Turn left on Pine Street;`
`    Turn right on 16th Street;`
`}`
`Else`
`{`
`    Turn right on 16th Street;`
`}`

### 0x232 - While/Until loops

- TO execute a set of instuctions more than once, you can use looping
- Looping requires a set of instuctions to telling it when to stop looping
  - Otherwise will loop infinite times
- **while loops**
  - Executes while a condition is `true`
  - Example:  Loop will only execute if `you are hungry` condition is true.
    `While (you are hungry)`
    `{`
        `Find some food;`
        `Eat some food;`
    `}`

- **until loops**
  - Inverted `while` loop
  - Not used in C - used in Perl
  - Example
    `Until (you are not hungry)`
    `{`
        `Find some food;`
        `Eat the food;`
    `}`

### 0x233 - For Loops

- `For` loops let you loop for a specific number of times
- A `For` loop is a `While` loop with a counter
- Example
  `For (5 interations)`
  `Drive straight for one mile;`
- C pseudo-code example
  `For (i=0; i<5; i++);`
    `Drive straight for 1 mile;`

## 0x240 - More fundamental programming concepts

### 0x241 - Variables

- Variables are an object that holds data that can be changed
- Constants are variables who's value can't be changed once set
- All variables are stored in memory and their declarations allow the compiler to organize memory more efficiently
- **Everything is memory**
- Variables are given a type that describes the information meant to be stored in that variable
- Common types include
  - `int` - Integer values
  - `float` - Float values (decimal)
  - `char` - Single character values
- Variables are declared by using these keywords before listing the variables
  - Example
    - `int a,b;`
    - `float k;`
    - `char z;`
- Once variables are declared, they can be used
- Variables can be assigned values when they are declared or anytime aftward using the `=` operator.
  - Example
    `int a = 13, b;`
    `float k;`
    `char z = 'A';`
    `k = 3.14;`
    `z = 'w';`
    `b = a + 5;`

### 0x242 - Arthmetic Operators

- Addition  b = a + 5
- Subtraction   b = a - 5
- Multiplication  b = a * 5
- Division  b = a / 5
- Modulo reduction% b = a % 5
  - Modulo reduction is the remainder after division
    - 13 % 5 = 3

- **Shorthand**
  - i = i + 1
    - i++ or ++i
    - Add 1 to the variable.

- i = i - 1
  - i-- or --i
  - Subtract 1 from the variable.

- You can combine shorthand
    `int a, b;`
    `a = 5;`
    `b = a++ * 6;`
    
- Add some value to the variable.
  - i = i + 12
  - i+=12 
- Subtract some value from the variable.
  - i = i - 12
  - i-=12
- Multiply some value by the variable.
  - i = i * 12
  - i*=12
- Divide some value from the variable.
  - i = i / 12
  - i/=12

### 0x243 - Comparison Operators

- Less than
  - `<`
  - `(a < b)`
- Greater than
  - `>`
  - `(a > b)`
- Less than or equal to
  - `<=`
  - `(a <= b)`
- Greater than or equal to
  - `>=`
  - `(a >= b)`
- Equal to
  - `==`
  - `(a == b)`
- Not equal to
  - `!=`
  - `(a != b)`

- Inverting a comparison operator
  - `!(a < b)` is equivalent to `(a >= b)`

- OR
  - `||`
  - `((a < b) || (a < c))`
- AND
  - `&&`
  - `((a < b) && !(a < c))`

### 0x244 - Functions

- Instructions that need to be used several times can be grouped into reusable functions
- Arguments (variables) can be passed into functions

  `Function Turn(variable_direction)`
  `{`
    `Activate the variable_direction blinker;`
    `Slow down;`
    `Check for oncoming traffic;`
    `while(there is oncoming traffic)`
    `{`
        `Stop;`
        `Watch for oncoming traffic;`
    `}`
    `Turn the steering wheel to the variable_direction;`
    `while(turn is not complete)`
    `{`
        `if(speed < 5 mph)`
            `Accelerate;`
    `}`
    `Turn the steering wheel back to the original position;`
    `Turn off the variable_direction blinker;`
`}`


- By default, functions return a value to the caller
- In C keywords are declared by the data type of the variable they are returning
- This function returns an integer
  `int factorial(int x)`
  `{`
    `int i;`
    `for(i=1; i < x; i++)`
        `x *= i;`
    `return x;`
   `}`
  
  - In C, the complier needs to know about functions before it can use them
    - This can be done by 
      - Writing the function before you use it
      - Using a function prototype
        - Function prototypes tell the compiler to expect a function with a specific name
        - Function prototypes are typically located at the beginning of the program
        - The complier only cares about the function name, return data type, and the data type of any arguments
        - Example
          - `int factorial(int);`

## 0x250 - Getting your hands dirty

### 0x251 - The bigger picture

- C code must be compiled for it to work
- Each architecture has a different machine language
- The GNU development tools include a program called `objdump`, which can be used to examine compiled binaries
  - `objdump -D a.out | grep -A20 main.:`
- The objdump program will spit out far too many lines of output to review so the output is piped into grep with the command-line option to only display 20 lines after the regular expression `main.:`. 
- Here is the output from `firstprog.c`:

  0000000000001149 <main>:
    1149:       f3 0f 1e fa             endbr64
    114d:       55                      push   %rbp
    114e:       48 89 e5                mov    %rsp,%rbp
    1151:       48 83 ec 10             sub    $0x10,%rsp
    1155:       c7 45 fc 00 00 00 00    movl   $0x0,-0x4(%rbp)
    115c:       eb 13                   jmp    1171 <main+0x28>
    115e:       48 8d 05 9f 0e 00 00    lea    0xe9f(%rip),%rax        # 2004 <_IO_stdin_used+0x4>
    1165:       48 89 c7                mov    %rax,%rdi
    1168:       e8 e3 fe ff ff          call   1050 <puts@plt>
    116d:       83 45 fc 01             addl   $0x1,-0x4(%rbp)
    1171:       83 7d fc 13             cmpl   $0x13,-0x4(%rbp)
    1175:       7e e7                   jle    115e <main+0x15>
    1177:       b8 00 00 00 00          mov    $0x0,%eax
    117c:       c9                      leave
    117d:       c3                      ret

Disassembly of section .fini:

0000000000001180 <_fini>:
    1180:       f3 0f 1e fa             endbr64

- Each byte is represented in hexadecimal notation, which is a base-16 numbering system.
- Hexadecimal uses 0 through 9 to represent 0 through 9, but it also uses A through F to represent the values 10 through 15. 
- This is a convenient notation since a byte contains 8 bits, each of which can be either true or false. This means a byte has 256 (28) possible values, so each byte can be described with 2 hexadecimal digits.
- The hexadecimal numbers—starting with 0000000000001149 on the far left—are memory addresses. 
- The bits of the machine language instructions must be put somewhere, and this somewhere is called memory. 
- Memory is a collection of bytes of temporary storage space that are numbered with addresses.
- Like a row of houses on a street, each with its own address, memory can be thought of as a row of bytes, each with its own memory address. 
- Each byte of memory can be accessed by its address, and in this case the CPU accesses this part of memory to retrieve the machine language instructions that make up the compiled program. 
- 32-bit processors have 232 (or 4,294,967,296) possible addresses.
- 64-bit processors have a 48-bit address space, allowing for 248 addresses. 
- 64-bit processors can run in 32-bit compatibility mode, which allows them to run 32-bit code more performantly.