# 0x251 - The bigger picture

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
- Hexadecimal bytes in the middle of the listing above are machine language instructions for the x86 processor. 
- Machine code isn't useful to anything but the processer, so the machine code is displayed as hexidecimal bytes
- Each instruction is on it's own line similar to splitting it into sentances
- The instuctions on the far right are assembly language insructions
- Assembly language instructions have a direct one-to-one relationship with their corresponding machine language instructions
- Every processor architecutre has a differnt form of machine language instructions
- Two main types of assembly language syntax
  - AT&T
  - Intel
- THe above example is AT&T. below is Intel:
    objdump -M intel -D a.out | grep -A20 main.:
    0000000000001149 <main>:
    1149:       f3 0f 1e fa             endbr64
    114d:       55                      push   rbp
    114e:       48 89 e5                mov    rbp,rsp
    1151:       48 83 ec 10             sub    rsp,0x10
    1155:       c7 45 fc 00 00 00 00    mov    DWORD PTR [rbp-0x4],0x0
    115c:       eb 13                   jmp    1171 <main+0x28>
    115e:       48 8d 05 9f 0e 00 00    lea    rax,[rip+0xe9f]        # 2004 <_IO_stdin_used+0x4>
    1165:       48 89 c7                mov    rdi,rax
    1168:       e8 e3 fe ff ff          call   1050 <puts@plt>
    116d:       83 45 fc 01             add    DWORD PTR [rbp-0x4],0x1
    1171:       83 7d fc 13             cmp    DWORD PTR [rbp-0x4],0x13
    1175:       7e e7                   jle    115e <main+0x15>
    1177:       b8 00 00 00 00          mov    eax,0x0
    117c:       c9                      leave
    117d:       c3                      ret

Disassembly of section .fini:

0000000000001180 <_fini>:
    1180:       f3 0f 1e fa             endbr64

- These instructions consist of an operation and sometimes additional arguments that describe the destination and/or the source for the operation. 
- These operations move memory around, perform some sort of basic math, or interrupt the processor to get it to do something else.
- Processors also have their own set of special variables called registers. 
- Most instructions use these registers to read or write data, so understanding the registers of a processor is essential to understanding the instructions.
