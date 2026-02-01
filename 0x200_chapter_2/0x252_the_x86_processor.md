# 0x252 - The x86 Processor

- The x86 processor has several registers, which are like internal variables for the processor.
- The GNU development tools also include a debugger called GDB. 
- Debuggers are used to setep through programs, examine program memory, and view processpr registers
- GDB is used to show the state of the processor registers right before the program starts.
  Breakpoint 1, main () at firstprog.c:6
    6           for(i=0; i<20; i++)
    (gdb) info registers
    rax            0x555555555149      93824992235849
    rbx            0x7fffffffd728      140737488344872
    rcx            0x555555557dc0      93824992247232
    rdx            0x7fffffffd738      140737488344888
    rsi            0x7fffffffd728      140737488344872
    rdi            0x1                 1
    rbp            0x7fffffffd600      0x7fffffffd600
    rsp            0x7fffffffd5f0      0x7fffffffd5f0
    r8             0x0                 0
    r9             0x7ffff7fca380      140737353917312
    r10            0x7fffffffd320      140737488343840
    r11            0x203               515
    r12            0x1                 1
    r13            0x0                 0
    r14            0x555555557dc0      93824992247232
    r15            0x7ffff7ffd000      140737354125312
    rip            0x555555555155      0x555555555155 <main+12>
    eflags         0x206               [ PF IF ]
    cs             0x33                51
    --Type <RET> for more, q to quit, c to continue without paging--
    ss             0x2b                43
    ds             0x0                 0
    es             0x0                 0
    fs             0x0                 0
    gs             0x0                 0
    k0             0x10001             65537
    k1             0x880               2176
    k2             0x0                 0
    k3             0x4000208           67109384
    k4             0x0                 0
    k5             0x0                 0
    k6             0x0                 0
    k7             0x0                 0
    fs_base        0x7ffff7faa740      140737353787200
    gs_base        0x0                 0
    (gdb) 

- A breakpoint is set on the main() function so execution will stop right before the code is executed
- GDB runs the program, stops at the breakpoint, and is told to display all the processor registers and their current states.
- The first four registers RAX(EAX), RCX(ECX), RDX(EDX), and RBX(EBX) are known as general purpose registers 
- These are called the 
  - Accumulator Registere
  - Counter Register
  - Data Register
  - Base Register
- They are used for a variety of purposes, but they mainly act as temporary variables for the CPU when it is executing machine instructions.
- The second four registers RSP(ESP), RBP(EBP), RSI(ESI), and RDI(EDI) are also general purpose registers, but they are sometimes known as pointers and indexes.
- They are called:
  - Stack Pointer
  - Base Pointer
  - Source Index
  - Destination Index,
- The first two registers are called pointers because they store 32-bit addresses which point to a location in memory
- The last two registers are also technically pointers that point to the source and destination when data needs to bread from or written to.
- There are load and store insturctions that use these registers, but are simple general purpose registers
- The RIP (EIP) register is the Instruction Pointer register, which points to the current instruction the process is reading
  - The processer reads each instuction using the RIP (EIP) register
  - This register is important and will be used a lot when debugging
