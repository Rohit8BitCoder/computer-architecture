# C.O.A notes

# Index

# **Register Transfer Language (RTL)**

The **Register Transfer Language** is the symbolic representation of notations used to specify the sequence of micro-operations. The term “**Register Transfer**” can perform micro-operations and transfer the result of operation to the same or other register. 

**Micro-operations :**

The operation executed on the data store in registers are called micro-operations. They are detailed low-level instructions used in some designs to implement complex machine instructions.

**Register Transfer :**

The information transformed from one register to another register is represented in symbolic form by replacement operator is called Register Transfer.

**Replacement Operator :**

In the statement, R2 <- R1, acts as a replacement operator. This statement defines the transfer of content of register R1 into register R2.

**There are various methods of RTL –**

1. General way of representing a register is by the name of the register enclosed in a rectangular box as shown in (a). 
2. Register is numbered in a sequence of 0 to (n-1) as shown in (b). 
3. The numbering of bits in a register can be marked on the top of the box as shown in (c). 
4. A 16-bit register PC is divided into 2 parts- Bits (0 to 7) are assigned with lower byte of 16-bit address and bits (8 to 15) are assigned with higher bytes of 16-bit address as shown in (d). 

![https://media.geeksforgeeks.org/wp-content/uploads/20200601145838/1406-5.png](https://media.geeksforgeeks.org/wp-content/uploads/20200601145838/1406-5.png)

**Basic symbols of RTL :**

| Symbol | Description | Example |
| --- | --- | --- |
| Letters and Numbers | Denotes a Register | MAR, R1, R2 |
| ( ) | Denotes a part of register | R1(8-bit)
R1(0-7) |
| <- | Denotes a transfer of information | R2 <- R1 |
| , | Specify two micro-operations of Register Transfer | R1 <- R2
R2 <- R1 |
| : | Denotes conditional operations | P : R2 <- R1
if P=1 |
| Naming Operator (:=) | Denotes another name for an already existing register/alias | Ra := R1 |

**Register Transfer Operations:**

The operation performed on the data stored in the registers are referred to as register transfer operations.

There are different types of register transfer operations:

**1. Simple Transfer – R2 <- R1**

****The content of R1 are copied into R2 without affecting the content of R1. It is an unconditional type of transfer operation.

**2. Conditional Transfer –**

![https://media.geeksforgeeks.org/wp-content/uploads/20200601150023/223-1.png](https://media.geeksforgeeks.org/wp-content/uploads/20200601150023/223-1.png)

It indicates that if P=1, then the content of R1 is transferred to R2. It is a unidirectional operation.

**3. Simultaneous Operations –**

If 2 or more operations are to occur simultaneously then they are separated with comma **(,)**.

![https://media.geeksforgeeks.org/wp-content/uploads/20200601150131/3164-1.png](https://media.geeksforgeeks.org/wp-content/uploads/20200601150131/3164-1.png)

If the control function P=1, then load the content of R1 into R2 and at the same clock load the content of R2 into R1.

# Bus and Memory Transfers

A digital system composed of many registers, and paths must be provided to transfer information from one register to another. The number of wires connecting all of the registers will be excessive if separate lines are used between each register and all other registers in the system.

A bus structure, on the other hand, is more efficient for transferring information between registers in a multi-register configuration system.

A bus consists of a set of common lines, one for each bit of register, through which binary information is transferred one at a time. Control signals determine which register is selected by the bus during a particular register transfer.

The following block diagram shows a Bus system for four registers. It is constructed with the help of four 4 * 1 Multiplexers each having four data inputs (0 through 3) and two selection inputs (S1 and S2).

![https://static.javatpoint.com/tutorial/coa/images/bus-and-memory-transfers.png](https://static.javatpoint.com/tutorial/coa/images/bus-and-memory-transfers.png)

The two selection lines S1 and S2 are connected to the selection inputs of all four multiplexers. The selection lines choose the four bits of one register and transfer them into the four-line common bus.

When both of the select lines are at low logic, i.e. S1S0 = 00, the 0 data inputs of all four multiplexers are selected and applied to the outputs that forms the bus. This, in turn, causes the bus lines to receive the content of register A since the outputs of this register are connected to the 0 data inputs of the multiplexers.

Similarly, when S1S0 = 01, register B is selected, and the bus lines will receive the content provided by register B.

The following function table shows the register that is selected by the bus for each of the four possible binary values of the Selection lines.

![https://static.javatpoint.com/tutorial/coa/images/bus-and-memory-transfers2.png](https://static.javatpoint.com/tutorial/coa/images/bus-and-memory-transfers2.png)

**Note: The number of multiplexers needed to construct the bus is equal to the number of bits in each register. The size of each multiplexer must be 'k * 1' since it multiplexes 'k' data lines. For instance, a common bus for eight registers of 16 bits each requires 16 multiplexers, one for each line in the bus. Each multiplexer must have eight data input lines and three selection lines to multiplex one significant bit in the eight registers.**

A bus system can also be constructed using **three-state gates** instead of multiplexers.

The **three state gates** can be considered as a digital circuit that has three gates, two of which are signals equivalent to logic 1 and 0 as in a conventional gate. However, the third gate exhibits a high-impedance state.

The most commonly used three state gates in case of the bus system is a **buffer gate**.

The graphical symbol of a three-state buffer gate can be represented as:

![https://static.javatpoint.com/tutorial/coa/images/bus-and-memory-transfers3.png](https://static.javatpoint.com/tutorial/coa/images/bus-and-memory-transfers3.png)

The following diagram demonstrates the construction of a bus system with three-state buffers.

![https://static.javatpoint.com/tutorial/coa/images/bus-and-memory-transfers4.png](https://static.javatpoint.com/tutorial/coa/images/bus-and-memory-transfers4.png)

- The outputs generated by the four buffers are connected to form a single bus line.
- Only one buffer can be in active state at a given point of time.
- The control inputs to the buffers determine which of the four normal inputs will communicate with the bus line.
- A 2 * 4 decoder ensures that no more than one control input is active at any given point of time.

# Memory Transfer

Most of the standard notations used for specifying operations on memory transfer are stated below.

- The transfer of information from a memory unit to the user end is called a **Read** operation.
- The transfer of new information to be stored in the memory is called a **Write** operation.
- A memory word is designated by the letter **M**.
- We must specify the address of memory word while writing the memory transfer operations.
- The **address register** is designated by **AR** and the **data register** by **DR**.
- Thus, a read operation can be stated as:
1. **Read: DR ← M [AR]**
- The **Read** statement causes a transfer of information into the data register (DR) from the memory word (M) selected by the address register (AR).
- And the corresponding write operation can be stated as:
1. **Write: M [AR] ← R1**
- The Write statement causes a transfer of information from register R1 into the memory word (M) selected by address register (AR).

![https://static.javatpoint.com/tutorial/coa/images/bus-and-memory-transfers5.png](https://static.javatpoint.com/tutorial/coa/images/bus-and-memory-transfers5.png)

# **Computer Instructions**

Computer instructions are a set of machine language instructions that a particular processor understands and executes. A computer performs tasks on the basis of the instruction provided.

An instruction comprises of groups called fields. These fields include:

- The Operation code (Opcode) field which specifies the operation to be performed.
- The Address field which contains the location of the operand, i.e., register or memory location.
- The Mode field which specifies how the operand will be located.

![https://static.javatpoint.com/tutorial/coa/images/computer-instructions.png](https://static.javatpoint.com/tutorial/coa/images/computer-instructions.png)

A basic computer has three instruction code formats which are:

1. **Memory - reference instruction**
2. **Register - reference instruction**
3. **Input-Output instruction**

**Note: The Operation code (Opcode) of an instruction refers to a group of bits that define arithmetic and logic operations such as add, subtract, multiply, shift, and compliment.**

### Memory - reference instruction

![https://static.javatpoint.com/tutorial/coa/images/computer-instructions2.png](https://static.javatpoint.com/tutorial/coa/images/computer-instructions2.png)

In Memory-reference instruction, 12 bits of memory is used to specify an address and one bit to specify the addressing mode 'I'.

The table(11) lists the seven memory-reference instructions. The decoded output D, for i = 0,1, 2, 3, 4, 5, and 6 from the operation decoder that belongs effective address to each instruction is included in the table. The effective address of the instruction is in the address register AR and was placed there during timing signal T2 when I = 0, or during timing signal T3 when I=1. The symbolic description of each instruction is specified in the table in terms of register transfer notation. The actual execution of the instruction in the bus system will require a sequence of micro-operations.

![bg3.png](C%20O%20A%20notes%20337e6c1c3a6640fd9a4eb887c8385fbc/0f38c529-4b76-42fb-a5d6-cc7043437f8a.png)

### Register - reference instruction

![https://static.javatpoint.com/tutorial/coa/images/computer-instructions3.png](https://static.javatpoint.com/tutorial/coa/images/computer-instructions3.png)

The Register-reference instructions are represented by the Opcode 111 with a 0 in the leftmost bit (bit 15) of the instruction.

A Register-reference instruction specifies an operation on or a test of the AC (Accumulator) register.

### Input-Output instruction

![https://static.javatpoint.com/tutorial/coa/images/computer-instructions4.png](https://static.javatpoint.com/tutorial/coa/images/computer-instructions4.png)

Just like the Register-reference instruction, an Input-Output instruction does not need a reference to memory and is recognised by the operation code 111 with a 1 in the leftmost bit of the instruction. The remaining 12 bits are used to specify the type of the input-output operation or test performed.

### Note

- The three operation code bits in positions 12 through 14 should be equal to 111. Otherwise, the instruction is a memory-reference type, and the bit in position 15 is taken as the addressing mode I.
- When the three operation code bits are equal to 111, control unit inspects the bit in position 15. If the bit is 0, the instruction is a register-reference type. Otherwise, the instruction is an input-output type having bit 1 at position 15.

# **Timing and Control**

The timing for all registers in the basic computer is controlled by a master clock generator. The clock pulses are applied to all flip-flops and registers in the system, including the flip-flops and registers in the control unit. The control signals are generated in the control unit and provide control inputs for the multiplexers in the common bus, control inputs in processor registers, and micro-operations for the accumulator.

**There are two major types of control organisation:  
1- hardwired control** : the control logic is implemented with gates, flip-flops, decoders, and other digital circuits. It has the advantage that it can be optimized to produce a fast mode of operation. 
**2- microprogrammed control:** the control information is stored in a control memory. The control memory is programmed to initiate the required sequence of micro-operations. 

![Untitled](C%20O%20A%20notes%20337e6c1c3a6640fd9a4eb887c8385fbc/Untitled.png)

SC is incremented with every positive clock transition, unless its CLR input is active. This produces the sequence of timing signals T0, T1, T2, T3, T4, and so on, as shown in the diagram. (**Note the relationship between the timing signal and its corresponding positive clock transition.**) If SC is not cleared, the timing signals will continue with T5, T6, up to T15 and back to T0. As an example, consider the case where SC is incremented to provide timing signals T0, T1 T2, T3, and T4 in sequence. At time T4, SC is cleared to 0 if decoder output D3 is active. This is expressed symbolically by the statement

                                              **𝐷3𝑇4:𝑆𝐶  ← 0**

![Untitled](C%20O%20A%20notes%20337e6c1c3a6640fd9a4eb887c8385fbc/a2986d1d-1f86-447c-b326-b1a13fddc53a.png)

# **Instruction Cycle**

A program residing in the memory unit of the computer consists of a sequence of instructions. The program is executed in the computer by going through a cycle for each instruction. In the basic computer each instruction cycle consists of the following phases: 

**1. Fetch an instruction from memory.  
2. Decode the instruction.  
3. Read the effective address from memory if the instruction has an indirect address.  
4. Execute the instruction.**  

This process continues indefinitely unless a HALT instruction is encountered. Initially, the program counter PC is loaded with the address of the first instruction in the program. The sequence counter SC is cleared to 0, providing a decoded timing signal T0. After each clock pulse, SC is incremented by one, so that the timing signals go through a sequence T0, T1, T2, and  so  on.  The  microoperations  for  the  fetch  and  decode  phases  can  be  specified  by  the 
following register transfer statements. 
                                                  𝑇0:𝐴𝑅 ←𝑃𝐶 
                                    𝑇1:𝐼𝑅  ← 𝑀[𝐴𝑅],𝑃𝐶 =𝑃𝐶 + 1 
𝑇2: 𝐷0, , , , 𝐷7← 𝐷𝑒𝑐𝑜𝑑𝑒 𝐼𝑅(12 −14),𝐴𝑅 ←𝐼𝑅(0 − 11), 𝐼 ← 𝐼𝑅(15)

1. It is necessary to use timing signal T1 to provide the following connections in the bus system.  
1. Enable the read input of memory.  
2. Place the content of memory onto the bus by making S2S1S0=111.  
3. Transfer the content of the bus to IR by enabling the LD input of IR.  
4. Increment PC by enabling the INR input of PC.

# Addressing Modes

Computers use addressing mode techniques for the purpose of accommodating one or both of the following provisions: 1. To give programming versatility to the user by providing such facilities as pointers to memory, counters for loop control, indexing of data, and program relocation. 2. To reduce the number of bits in the addressing field of the instruction. PC holds the address of the instruction to be executed next and is incremented each time an instruction is fetched from memory. An example of an instruction format with a distinct addressing mode field is shown in Fig(27)

![Untitled](C%20O%20A%20notes%20337e6c1c3a6640fd9a4eb887c8385fbc/f96c72f5-345f-4720-89e4-351eaabc2aa5.png)

**Immediate  Mode:** In  this  mode  the  operand  is  specified  in  the  instruction  itself.  In  other words, an immediate-mode instruction has an operand field rather than an address field. 
**Register  Mode:** In  this mode  the operands  are  in  registers  that  reside within  the  CPU. The particular register is selected from a register field in the instruction. 
**Register Indirect Mode:** In this mode the instruction specifies a register in the CPU whose contents give the address of the operand in memory. 
**Auto-increment  or  Auto-decrement  Mode:**  This  is  similar  to  the  register  indirect  mode except  that  the  register  is  incremented  or  decremented  after  (or  before)  its  value  is  used  to 
access memory. The  effective  address  is  defined  to  be  the  memory  address  obtained  from  the  computation dictated by the given addressing mode.  
**Direct  Address Mode:** In this mode the effective address is equal to the address part of the instruction. 
**Indirect  Address  Mode:**  In  this  mode the address field  of  the instruction gives  the  address where the effective address is stored in memory. The effective address in these modes is obtained from the following computation: 
****effective address = address part of instruction + content of CPU register 
**Relative  Address  Mode:** In  this  mode  the  content  of  the  program  counter  is  added  to  the 
address part of the instruction in order to obtain the effective address. 
**Indexed  Addressing  Mode:**  In  this  mode  the  content  of  an  index  register  is  added  to  the address part of the instruction to obtain the effective address. 
**Base Register Addressing Mode: I**n this mode the content of a base register is added to the address part of the instruction to obtain the effective address.

# Instruction Cycle

A program residing in the memory unit of a computer consists of a sequence of instructions. These instructions are executed by the processor by going through a cycle for each instruction.

In a basic computer, each instruction cycle consists of the following phases:

1. **Fetch instruction from memory.**
2. **Decode the instruction.**
3. **Read the effective address from memory.**
4. **Execute the instruction.**

![Untitled](C%20O%20A%20notes%20337e6c1c3a6640fd9a4eb887c8385fbc/Untitled%201.png)

After the following four procedures are done, the control switches back to the first step and repeats the similar process for the next instruction. Therefore, the cycle continues until a **Halt** condition is met. The figure shows the phases contained in the instruction cycle.

![https://www.tutorialspoint.com/assets/questions/media/54565/fetch_instruction.jpg](https://www.tutorialspoint.com/assets/questions/media/54565/fetch_instruction.jpg)

As display in the figure, the halt condition appears when the device receive turned off, on the circumstance of unrecoverable errors, etc.

## **Fetch Cycle**

The address instruction to be implemented is held at the program counter. The processor fetches the instruction from the memory that is pointed by the PC.

Next, the PC is incremented to display the address of the next instruction. This instruction is loaded onto the instruction register. The processor reads the instruction and executes the important procedures.

## **Execute Cycle**

The data transfer for implementation takes place in two methods are as follows −

- **Processor-memory** − The data sent from the processor to memory or from memory to processor.
- **Processor-Input/Output** − The data can be transferred to or from a peripheral device by the transfer between a processor and an I/O device.

In the execute cycle, the processor implements the important operations on the information, and consistently the control calls for the modification in the sequence of data implementation. These two methods associate and complete the execute cycle.

# **Stack Organization**

**[Stack](https://www.tutorialspoint.com/data_structures_algorithms/stack_algorithm.htm)** is also known as the Last In First Out (LIFO) list. It is the most important feature in the **[CPU](https://www.tutorialspoint.com/computer_fundamentals/computer_cpu.htm)**. It saves data such that the element stored last is retrieved first. A stack is a memory unit with an address register. This register influence the address for the stack, which is known as Stack Pointer (SP). The stack pointer continually influences the address of the element that is located at the top of the stack.

It can insert an element into or delete an element from the stack. The insertion operation is known as push operation and the deletion operation is known as pop operation. In a computer stack, these operations are simulated by incrementing or decrementing the SP register.

## **Register Stack**

The stack can be arranged as a set of memory words or registers. Consider a 64-word register stack arranged as displayed in the figure. The stack pointer register includes a binary number, which is the address of the element present at the top of the stack. The three-element A, B, and C are located in the stack.

The element C is at the top of the stack and the stack pointer holds the address of C that is 3. The top element is popped from the stack through reading memory word at address 3 and decrementing the stack pointer by 1. Then, B is at the top of the stack and the SP holds the address of B that is 2. It can insert a new word, the stack is pushed by incrementing the stack pointer by 1 and inserting a word in that incremented location.

![https://www.tutorialspoint.com/assets/questions/media/54603/register_stack.jpg](https://www.tutorialspoint.com/assets/questions/media/54603/register_stack.jpg)

The stack pointer includes 6 bits, because 26 = 64, and the SP cannot exceed 63 (111111 in binary). After all, if 63 is incremented by 1, therefore the result is 0(111111 + 1 = 1000000). SP holds only the six least significant bits. If 000000 is decremented by 1 thus the result is 111111.

Therefore, when the stack is full, the one-bit register ‘FULL’ is set to 1. If the stack is null, then the one-bit register ‘EMTY’ is set to 1. The data register DR holds the binary information which is composed into or readout of the stack.

First, the SP is set to 0, EMTY is set to 1, and FULL is set to 0. Now, as the stack is not full (FULL = 0), a new element is inserted using the push operation.

The push operation is executed as follows −

| SP←SP + 1 | It can increment stack pointer |
| --- | --- |
| K[SP] ← DR | It can write element on top of the stack |
| If (SP = 0) then (FULL ← 1) | Check if stack is full |
| EMTY ← 0 | Mark the stack not empty |

The stack pointer is incremented by 1 and the address of the next higher word is saved in the SP. The word from DR is inserted into the stack using the memory write operation. The first element is saved at address 1 and the final element is saved at address 0. If the stack pointer is at 0, then the stack is full and ‘FULL’ is set to 1. This is the condition when the SP was in location 63 and after incrementing SP, the final element is saved at address 0. During an element is saved at address 0, there are no more empty registers in the stack. The stack is full and the ‘EMTY’ is set to 0.

A new element is deleted from the stack if the stack is not empty (if EMTY = 0). The pop operation includes the following sequence of micro-operations −

| DR←K[SP] | It can read an element from the top of the stack |
| --- | --- |
| SP ← SP – 1 | It can decrement the stack pointer |
| If (SP = 0) then (EMTY ← 1) | Check if stack is empty |
| FULL ← 0 | Mark the stack not full |

The top element from the stack is read and transfer to DR and thus the stack pointer is decremented. If the stack pointer reaches 0, then the stack is empty and ‘EMTY’ is set to 1. This is the condition when the element in location 1 is read out and the SP is decremented by 1.

# **Memory Stack**

A stack can be executed in the CPU by analyzing an area of the computer memory to a stack operation and utilizing a processor register as a stack pointer. In this method, it is performed in a random access memory connected to the CPU.

An area of the computer memory is broken into three segments such as program, data, and stack. The address of the next instruction in the program is saved in the pointer Program Counter (PC). The Address Register (AR) points to an array of the information. SP continually influences the address of the element present at the top of the stack.

The three registers that are linked to the common bus are PC, AR, and SP. PC can read the instruction during the fetch stage. An operand is read during execute stage using the address register. An element is pushed into or popped from the stack using a stack pointer.

![https://www.tutorialspoint.com/assets/questions/media/54605/memory_stack.jpg](https://www.tutorialspoint.com/assets/questions/media/54605/memory_stack.jpg)

In the figure, the SP points to a beginning value ‘2001’. Therefore, the stack increase with decreasing addresses. The first element is saved at address 2000, the next element is saved at address 1999 and the last element is saved at address 1000.

The data register can read an element into or from the stack. It can use push operation to insert a new element into the stack.

SP ← SP – 1

K ← SP [DR]

It can insert another element into the stack, the stack pointer is decremented by 1. It can point to the address of the next location/word. A word from DR is inserted into the top of the stack using memory write operation.

It can delete an element from the stack. It can use the pop operation which is as follows −

DR ← K [SP]

SP ← SP + 1

The top element is read into the DR and then the stack pointer is decremented to point to the next element in the stack.

Two processor registers can check the stack limits. One processor register influence the upper limit (1000) and the other influence the lower limit (2001). During push operation, the SP is compared with the upper limit to check if the stack is full. During pop operation, the SP is compared with the lower limit to check if the stack is empty.

# **General Register Organization**

A set of **[flip-flops](https://www.tutorialspoint.com/digital_circuits/digital_circuits_flip_flops.htm)** forms a register. A register is a unique high-speed storage area in the **[CPU](https://www.tutorialspoint.com/computer_fundamentals/computer_cpu.htm)**. They include combinational circuits that implement data processing. The information is always defined in a register before processing. The registers speed up the implementation of programs.

Registers implement two important functions in the CPU operation are as follows −

- It can support a temporary storage location for data. This supports the directly implementing programs to have fast access to the data if required.
- It can save the status of the CPU and data about the directly implementing program.

**Example** − Address of the next program instruction, signals get from the external devices and error messages, and including different data is saved in the registers.

If a CPU includes some registers, therefore a common bus can link these registers. A general organization of seven CPU registers is displayed in the figure.

![https://www.tutorialspoint.com/assets/questions/media/54601/some_registers.jpg](https://www.tutorialspoint.com/assets/questions/media/54601/some_registers.jpg)

The CPU bus system is managed by the control unit. The control unit explicit the data flow through the **[ALU](https://www.tutorialspoint.com/arithmetic-logic-unit-alu)** by choosing the function of the ALU and components of the system.

Consider R1 ← R2 + R3, the following are the functions implemented within the CPU −

**MUX A Selector (SELA)** − It can place R2 into bus A.

**MUX B Selector (SELB)** − It can place R3 into bus B.

**ALU Operation Selector (OPR)** − It can select the arithmetic addition (ADD).

**Decoder Destination Selector (SELD)** − It can transfers the result into R1.

The multiplexers of 3-state gates are performed with the buses. The state of 14 binary selection inputs determines the control word. The 14-bit control word defines a micro-operation.

The encoding of register selection fields is specified in the table.

**Encoding of Register Selection Field**

| Binary Code | SELA | SELB | SELD |
| --- | --- | --- | --- |
| 000 | Input | Input | None |
| 001 | R1 | R1 | R1 |
| 010 | R2 | R2 | R2 |
| 011 | R3 | R3 | R3 |
| 100 | R4 | R4 | R4 |
| 101 | R5 | R5 | R5 |
| 110 | R6 | R6 | R6 |
| 111 | R7 | R7 | R7 |

There are several micro-operations are implemented by the ALU. Few of the operations implemented by the ALU are displayed in the table.

**Encoding of ALU Operations**

| OPR Select | Operation | Symbol |
| --- | --- | --- |
| 00000 | Transfer A | TSFA |
| 00001 | Increment A | INCA |
| 00010 | Add A + B | ADD |
| 00101 | Subtract A - B | SUB |
| 00110 | Decrement A | DECA |
| 01000 | ADD A and B | AND |
| 01010 | OR A and B | OR |
| 01100 | XOR A and B | XOR |
| 01110 | Complement A | COMA |
| 10000 | Shift right A | SHRA |
| 11000 | Shift left A | SHLA |

There are some ALU micro-operations are shown in the table.

**ALU Micro-Operations**

| Micro-operation | SELA | SELB | SELD | OPR | Control Word |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| R1 ← R2 – R3 | R2 | R3 | R1 | SUB | 010 | 011 | 001 | 00101 |
| R4 ← R4 ∨ R5 | R4 | R5 | R4 | OR | 100 | 101 | 100 | 01010 |
| R6 ← R6 + R1 | - | R6 | R1 | INCA | 110 | 000 | 110 | 00001 |
| R7 ← R1 | R1 | - | R7 | TSFA | 001 | 000 | 111 | 00000 |
| Output ← R2 | R2 | – | None | TSFA | 010 | 000 | 000 | 00000 |
| Output ← Input | Input | - | None | TSFA | 000 | 000 | 000 | 00000 |
| R4 ← shl R4 | R4 | - | R4 | SHLA | 100 | 000 | 100 | 11000 |
| R5 ← 0 | R5 | R5 | R5 | XOR | 101 | 101 | 101 | 01100 |

# **Difference Between RISC and CISC**

RISC and CISC are two different types of computer architectures that are used to design the microprocessors that are found in computers. The fundamental difference between RISC and CISC is that **RISC (Reduced Instruction Set Computer)** includes simple instructions and takes one cycle, while the **CISC (Complex Instruction Set Computer)** includes complex instructions and takes multiple cycles.

## **What is RISC?**

In the **[RISC architecture](https://www.tutorialspoint.com/what-is-risc-processor)**, the instruction set of the computer system is simplified to reduce the execution time. RISC architecture has a small set of instructions that generally includes register-to-register operations.

The RISC architecture uses comparatively a simple instruction format that is easy to decode. The instruction length can be fixed and aligned to word boundaries. RISC processors can execute only one instruction per clock cycle.

The following are some important **characteristics** of a RISC Processor −

- A RISC processor has a few instructions.
- RISC processor has a few addressing modes.
- In the RISC processor, all operations are performed within the registers of the CPU.
- RISC processor can be of fixed-length.
- RISC can be hardwired rather than micro-programmed control.
- RISC is used for single-cycle instruction execution.
- RISC processor has easily decodable instruction format.

RISC architectures are characterized by a small, simple instruction set and a highly efficient execution pipeline. This allows RISC processors to execute instructions quickly, but it also means that they can only perform a limited number of tasks.

## **What is CISC?**

The **[CISC architecture](https://www.tutorialspoint.com/what-is-cisc-processor)** comprises a complex instruction set. A CISC processor has a variable-length instruction format. In this processor architecture, the instructions that require register operands can take only two bytes.

In a CISC processor architecture, the instructions which require two memory addresses can take five bytes to comprise the complete instruction code. Therefore, in a CISC processor, the execution of instructions may take a varying number of clock cycles. The CISC processor also provides direct manipulation of operands that are stored in the memory.

The primary objective of the CISC processor architecture is to support a single machine instruction for each statement that is written in a high-level programming language.

The following are the important **characteristics** of a CISC processor architecture −

- CISC can have variable-length instruction formats.
- It supports a set of a large number of instructions, typically from 100 to 250 instructions.
- It has a large variety of addressing modes, typically from 5 to 20 different modes.
- CISC has some instructions which perform specialized tasks and are used infrequently.

CISC architectures have a large, complex instruction set and a less efficient execution pipeline. This allows CISC processors to perform a wider range of tasks, but they are not as fast as RISC processors when executing instructions.

## **Difference between RISC and CISC**

The following table highlights all the important differences between RISC and CISC architectures −

| S.No. | RISC | CISC |
| --- | --- | --- |
| 1. | It stands for Reduced Instruction Set Computer. | It stands for Complex Instruction Set Computer. |
| 2. | It is a microprocessor architecture that uses small instruction set of uniform length. | This offers hundreds of instructions of different sizes to the users. |
| 3. | These simple instructions are executed in one clock cycle. | This architecture has a set of special purpose circuits which help execute the instructions at a high speed. |
| 4. | These chips are relatively simple to design. | These chips are complex to design. |
| 5. | They are inexpensive. | They are relatively expensive. |
| 6. | Examples of RISC chips include SPARC, POWER PC. | Examples of CISC include Intel architecture, AMD. |
| 7. | It has less number of instructions. | It has more number of instructions. |
| 8. | It has fixed-length encodings for instructions. | It has variable-length encodings of instructions. |
| 9. | Simple addressing formats are supported. | The instructions interact with memory using complex addressing modes. |
| 10. | It doesn't support arrays. | It has a large number of instructions. It supports arrays. |
| 11. | It doesn't use condition codes. | Condition codes are used. |
| 12. | Registers are used for procedure arguments and return addresses. | The stack is used for procedure arguments and return addresses. |

# **Address Sequencing**

Microinstructions are saved in control memory in groups. These groups describe routines. Each computer instruction has its microprogram routine that can create micro-operations. These micro-operations can execute instructions. The hardware consists of controls for the address sequencing of the microinstructions of a similar routine. They also branch the microinstructions.

There are the following phases that the control has while implementing a computer instruction −

- When power is turned on, and address is initially loaded into the control address register. (This is the address of the first microinstruction).
- The control address register is incremented resulting in sequencing the fetch routine.
- After the fetch routine, the instruction is present in the IR of the computer.
- Next, the control memory retrieves the effective address of the operand from the routine.
- Thus, the mapping process appears from the instruction bits to a control memory address.
- It depends on the opcodes of instruction the microinstructions of the processor registers are generated. Each of these microinstructions has a separate microprogram routine stored.
- The instruction code bits are changed into the address where the routine is placed and is known as the mapping process. A mapping process transforms the microinstruction into a control memory address.
- Next, subroutines are called and processes are returned.
- After the completion of the routine, the control address register is incremented to sequence the instruction is implemented. It can also be based on the values of status bits in processor registers. External registers are needed through microprograms to save return addresses that use subroutines. After the instruction is performed, the control returns to the fetch routine. This is done by branching the microinstruction to the first address in the fetch routine.

The diagram shows the block diagram of a control memory and its associated hardware to support in choosing the next microinstruction. The microinstruction present in the control memory has a set of bits that facilitate to start off the micro-operations in registers.

There are four different directions are showed in the figure from where the control address register recovers its address. The CAR is incremented by the incrementer and selects the next instruction. In multiple fields of microinstruction, the branching address can be determined to result in branching.

It can specify the condition of the status bits of microinstruction, conditional branching can be applied. A mapping logic circuit can share an external address. A special register can save the return address so that when the microprogram needs to return from the subroutine, it can need the value from the unique register.

![https://www.tutorialspoint.com/assets/questions/media/54577/address_sequencing.jpg](https://www.tutorialspoint.com/assets/questions/media/54577/address_sequencing.jpg)

# Mode of Transfer:

The binary information that is received from an external device is usually stored in the memory unit. The information that is transferred from the CPU to the external device is originated from the memory unit. CPU merely processes the information but the source and target is always the memory unit. Data transfer between CPU and the I/O devices may be done in different modes. Data transfer to and from the peripherals may be done in any of the three possible ways

1. **Programmed I/O.**
2. **Interrupt- initiated I/O.**
3. **Direct memory access( DMA).**
4. **Programmed I/O:** It is due to the result of the I/O instructions that are written in the computer program. Each data item transfer is initiated by an instruction in the program. Usually the transfer is from a CPU register and memory. In this case it requires constant monitoring by the CPU of the peripheral devices.**Example of Programmed I/O:** In this case, the I/O device does not have direct access to the memory unit. A transfer from I/O device to memory requires the execution of several instructions by the CPU, including an input instruction to transfer the data from device to the CPU and store instruction to transfer the data from CPU to memory. In programmed I/O, the CPU stays in the program loop until the I/O unit indicates that it is ready for data transfer. This is a time consuming process since it needlessly keeps the CPU busy. This situation can be avoided by using an interrupt facility. This is discussed below.
5. **Interrupt- initiated I/O:** Since in the above case we saw the CPU is kept busy unnecessarily. This situation can very well be avoided by using an interrupt driven method for data transfer. By using interrupt facility and special commands to inform the interface to issue an interrupt request signal whenever data is available from any device. In the meantime the CPU can proceed for any other program execution. The interface meanwhile keeps monitoring the device. Whenever it is determined that the device is ready for data transfer it initiates an interrupt request signal to the computer. Upon detection of an external interrupt signal the CPU stops momentarily the task that it was already performing, branches to the service program to process the I/O transfer, and then return to the task it was originally performing.
    - The I/O transfer rate is limited by the speed with which the processor can test and service a device.
    - The processor is tied up in managing an I/O transfer; a number of instructions must be executed for each I/O transfer.
    - Terms:
        - Hardware Interrupts: Interrupts present in the hardware pins.
        - Software Interrupts: These are the instructions used in the program whenever the required functionality is needed.
        - Vectored interrupts: These interrupts are associated with the static vector address.
        - Non-vectored interrupts: These interrupts are associated with the dynamic vector address.
        - Maskable Interrupts: These interrupts can be enabled or disabled explicitly.
        - Non-maskable interrupts: These are always in the enabled state. we cannot disable them.
        - External interrupts: Generated by external devices such as I/O.
        - Internal interrupts: These devices are generated by the internal components of the processor such as power failure, error instruction, temperature sensor, etc.
        - Synchronous interrupts: These interrupts are controlled by the fixed time interval. All the interval interrupts are called as synchronous interrupts.
        - Asynchronous interrupts: These are initiated based on the feedback of previous instructions. All the external interrupts are called as asynchronous interrupts.
6. **Direct Memory Access**: The data transfer between a fast storage media such as magnetic disk and memory unit is limited by the speed of the CPU. Thus we can allow the peripherals directly communicate with each other using the memory buses, removing the intervention of the CPU. This type of data transfer technique is known as DMA or direct memory access. During DMA the CPU is idle and it has no control over the memory buses. The DMA controller takes over the buses to manage the transfer directly between the I/O devices and the memory unit.
    1. Bus grant request time.
    2. Transfer the entire block of data at transfer rate of device because the device is usually slow than the speed at which the data can be transferred to CPU.
    3. Release the control of the bus back to CPU So, total time taken to transfer the N bytes = Bus grant request time + (N) * (memory transfer rate) + Bus release control time.
7. Buffer the byte into the buffer
8. Inform the CPU that the device has 1 byte to transfer (i.e. bus grant request)
9. Transfer the byte (at system bus speed)
10. Release the control of the bus back to CPU.

### Advantages:

**Standardization:** I/O interfaces provide a standard way of communicating with external devices. This means that different devices can be connected to a computer using the same interface, which makes it easier to swap out devices and reduces the need for specialized hardware.

**Modularity:** With I/O interfaces, different devices can be added or removed from a computer without affecting the other components. This makes it easier to upgrade or replace a faulty device without affecting the rest of the system.

**Efficiency:** I/O interfaces can transfer data between the computer and the external devices at high speeds, which allows for faster data transfer and processing times.

**Compatibility:** I/O interfaces are designed to be compatible with a wide range of devices, which means that users can choose from a variety of devices that are compatible with their computer’s I/O interface.

### Disadvantages:

**Cost:** I/O interfaces can be expensive, especially if specialized hardware is required to connect a particular device to a computer system.

**Complexity:** Some I/O interfaces can be complex to configure and require specialized knowledge to set up and maintain. This can be a disadvantage for users who are not familiar with the technical aspects of computer hardware.

**Compatibility issues:** While I/O interfaces are designed to be compatible with a wide range of devices, there can still be compatibility issues with certain devices. In some cases, device drivers may need to be installed to ensure proper functionality.

**Security risks:** I/O interfaces can be a security risk if they are not properly configured or secured. Hackers can exploit vulnerabilities in I/O interfaces to gain unauthorised access to a computer system or steal data.

# **Direct Memory Access (DMA)**

For the execution of a computer program, it requires the synchronous working of more than one component of a computer. For example, Processors – providing necessary control information, address etc. buses – to transfer information and data to and from memory to I/O
device etc. 

The interesting factor of the system would be the way it handles the transfer of information among processor, memory and I/O devices. Usually, processors control all the process of transferring data, right from initiating the transfer to the storage of data at the destination. This adds load on the processor and most of the time it stays in the ideal state, thus decreasing the efficiency of the system. 

To speed up the transfer of data between I/O devices and memory, DMA controller acts as station master. DMA controller transfers data with minimal intervention of the processor.

## What is a DMA Controller?

The term DMA stands for direct memory access. The hardware device used for direct memory access is called the DMA controller. DMA controller is a control unit, part of I/O device’s interface circuit, which can transfer blocks of data between I/O devices and main memory with minimal intervention from the processor.

![Untitled](C%20O%20A%20notes%20337e6c1c3a6640fd9a4eb887c8385fbc/Untitled%202.png)

### **Working of DMA Controller**

DMA controller has to share the bus with the processor to make the data transfer. The device that holds the bus at a given time is called bus master. When a transfer from I/O device to the memory or vice verse has to be made, the processor stops the execution of the current program, increments [the program](https://www.elprocus.com/8086-assembly-language-programs-explanation/) counter, moves data over stack then sends a DMA select signal to DMA controller over the address bus.

If the DMA controller is free, it requests the control of bus from the processor by raising the bus request signal. Processor grants the bus to the controller by raising the bus grant signal, now DMA controller is the bus master. The processor initiates the DMA controller by sending the memory addresses, number of blocks of data to be transferred and direction of data transfer. After assigning the data transfer task to the DMA controller, instead of waiting ideally till completion of data transfer, the processor resumes the execution of the program after retrieving instructions from the stack.

![transfer-of-data-by-DMA-in-computer-by-DMA.jpg](C%20O%20A%20notes%20337e6c1c3a6640fd9a4eb887c8385fbc/transfer-of-data-by-DMA-in-computer-by-DMA.jpg)

DMA controller now has the full control of buses and can interact directly with memory and I/O devices independent of CPU. It makes the data transfer according to the control instructions received by the processor. After completion of data transfer, it disables the bus request signal and CPU disables the bus grant signal thereby moving control of buses to the CPU.

When an I/O device wants to initiate the transfer then it sends a DMA request signal to the DMA controller, for which the controller acknowledges if it is free. Then the controller requests the processor for the bus, raising the bus request signal. After receiving the bus grant signal it transfers the data from the device. For n channeled DMA controller n number of external devices can be connected.

**The DMA transfers the data in three modes which include the following:-**

a) **Burst Mode**: In this mode DMA handover the buses to CPU only after completion of whole data transfer. Meanwhile, if the CPU requires the bus it has to stay ideal and wait for data transfer.

b) **Cycle Stealing Mode**: In this mode, DMA gives control of buses to CPU after transfer of every byte. It continuously issues a request for bus control, makes the transfer of one byte and returns the bus. By this CPU doesn’t have to wait for a long time if it needs a bus for higher priority task.

c) **Transparent Mode:** Here, DMA transfers data only when CPU is executing the instruction which does not require the use of buses.

# Booth's Multiplication Algorithm

The booth algorithm is a multiplication algorithm that allows us to multiply the two signed binary integers in 2's complement, respectively. It is also used to speed up the performance of the multiplication process. It is very efficient too. It works on the string bits 0's in the multiplier that requires no additional bit only shift the right-most string bits and a string of 1's in a multiplier bit weight 2k to weight 2m that can be considered as **2k+ 1 - 2m**.

Following is the pictorial representation of the Booth's Algorithm:

![https://static.javatpoint.com/tutorial/coa/images/booths-multiplication-algorithm-in-coa.png](https://static.javatpoint.com/tutorial/coa/images/booths-multiplication-algorithm-in-coa.png)

In the above flowchart, initially, **AC** and **Qn + 1** bits are set to 0, and the **SC** is a sequence counter that represents the total bits set **n,** which is equal to the number of bits in the multiplier. There are **BR** that represent the **multiplicand bits,** and QR represents the **multiplier bits**. After that, we encountered two bits of the multiplier as Qn and Qn + 1, where Qn represents the last bit of QR, and Qn + 1 represents the incremented bit of Qn by 1. Suppose two bits of the multiplier is equal to 10; it means that we have to subtract the multiplier from the partial product in the accumulator AC and then perform the arithmetic shift operation (ashr). If the two of the multipliers equal to 01, it means we need to perform the addition of the multiplicand to the partial product in accumulator AC and then perform the arithmetic shift operation (**ashr**), including **Qn + 1**. The arithmetic shift operation is used in Booth's algorithm to shift AC and QR bits to the right by one and remains the sign bit in AC unchanged. And the sequence counter is continuously decremented till the computational loop is repeated, equal to the number of bits (n).

### Working on the Booth Algorithm

1. Set the Multiplicand and Multiplier binary bits as M and Q, respectively.
2. Initially, we set the AC and Q registers value to 0.
    
    n + 1
    
3. SC represents the number of Multiplier bits (Q), and it is a sequence counter that is continuously decremented till equal to the number of bits (n) or reached to 0.
4. A Qn represents the last bit of the Q, and the Q shows the incremented bit of Qn by 1.
    
    n+1
    
5. On each cycle of the booth algorithm, Q and Q bits will be checked on the following parameters as follows:
    
    n
    
    n + 1
    
    1. When two bits Q and Q are 00 or 11, we simply perform the arithmetic shift right operation (ashr) to the partial product AC. And the bits of Qn and Q is incremented by 1 bit.
        
        n
        
        n + 1
        
        n + 1
        
    2. If the bits of Q and Q is shows to 01, the multiplicand bits (M) will be added to the AC (Accumulator register). After that, we perform the right shift operation to the AC and QR bits by 1.
        
        n
        
        n + 1
        
    3. If the bits of Q and Q is shows to 10, the multiplicand bits (M) will be subtracted from the AC (Accumulator register). After that, we perform the right shift operation to the AC and QR bits by 1.
        
        n
        
        n + 1
        
6. The operation continuously works till we reached n - 1 bit in the booth algorithm.
7. Results of the Multiplication binary bits will be stored in the AC and QR registers.

There are two methods used in Booth's Algorithm:

### 1. RSC (Right Shift Circular)

It shifts the right-most bit of the binary number, and then it is added to the beginning of the binary bits.

![https://static.javatpoint.com/tutorial/coa/images/booths-multiplication-algorithm-in-coa2.png](https://static.javatpoint.com/tutorial/coa/images/booths-multiplication-algorithm-in-coa2.png)

### 2. RSA (Right Shift Arithmetic)

It adds the two binary bits and then shift the result to the right by 1-bit position.

**Example**: 0100 + 0110 => 1010, after adding the binary number shift each bit by 1 to the right and put the first bit of resultant to the beginning of the new bit.

**Example: Multiply the two numbers 7 and 3 by using the Booth's multiplication algorithm.**

**Ans**. Here we have two numbers, 7 and 3. First of all, we need to convert 7 and 3 into binary numbers like 7 = (0111) and 3 = (0011). Now set 7 (in binary 0111) as multiplicand (M) and 3 (in binary 0011) as a multiplier (Q). And SC (Sequence Count) represents the number of bits, and here we have 4 bits, so set the SC = 4. Also, it shows the number of iteration cycles of the booth's algorithms and then cycles run SC = SC - 1 time.

| Qn | Qn + 1 | M = (0111)M' + 1 = (1001) & Operation | AC | Q | Qn + 1 | SC |
| --- | --- | --- | --- | --- | --- | --- |
| 1 | 0 | Initial | 0000 | 0011 | 0 | 4 |
|  |  | Subtract (M' + 1) | 1001 |  |  |  |
|  |  |  | 1001 |  |  |  |
|  |  | Perform Arithmetic Right Shift operations (ashr) | 1100 | 1001 | 1 | 3 |
| 1 | 1 | Perform Arithmetic Right Shift operations (ashr) | 1110 | 0100 | 1 | 2 |
| 0 | 1 | Addition (A + M) | 0111 |  |  |  |
|  |  |  | 0101 | 0100 |  |  |
|  |  | Perform Arithmetic right shift operation | 0010 | 1010 | 0 | 1 |
| 0 | 0 | Perform Arithmetic right shift operation | 0001 | 0101 | 0 | 0 |

The numerical example of the Booth's Multiplication Algorithm is 7 x 3 = 21 and the binary representation of 21 is 10101. Here, we get the resultant in binary 00010101. Now we convert it into decimal, as (000010101)10 = 2*4 + 2*3 + 2*2 + 2*1 + 2*0 => 21.

**Example: Multiply the two numbers 23 and -9 by using the Booth's multiplication algorithm.**

Here, M = 23 = (010111) and Q = -9 = (110111)

| Qn             Qn + 1 | M = 0 1 0 1 1 1M' + 1 = 1 0 1 0 0 1 | AC | Q | Qn + 1             SC |
| --- | --- | --- | --- | --- |
|  | Initially | 000000 | 110111 | 0             6 |
| 1             0 | Subtract M | 101001 |  |  |
|  |  | 101001 |  |  |
|  | Perform Arithmetic right shift operation | 110100 | 111011 | 1             5 |
| 1             1 | Perform Arithmetic right shift operation | 111010 | 011101 | 1             4 |
| 1             1 | Perform Arithmetic right shift operation | 111101 | 001110 | 1             3 |
| 0              1 | Addition (A + M) | 010111 |  |  |
|  |  | 010100 |  |  |
|  | Perform Arithmetic right shift operation | 001010 | 000111 | 0             2 |
| 1             0 | Subtract M | 101001 |  |  |
|  |  | 110011 |  |  |
|  | Perform Arithmetic right shift operation | 111001 | 100011 | 1             1 |
| 1             1 | Perform Arithmetic right shift operation | 111100 | 110001 | 1             0 |

**Qn + 1** = 1, it means the output is negative.

Hence, 23 * -9 = 2's complement of 111100110001 => **(00001100111)**

# **What Is Parallel Processing?**

**Parallel processing is a computing technique when multiple streams of calculations or data processing tasks co-occur through numerous central processing units (CPUs) working concurrently.**

![https://images.spiceworks.com/wp-content/uploads/2022/08/26120008/Parallel-Processing.png](https://images.spiceworks.com/wp-content/uploads/2022/08/26120008/Parallel-Processing.png)

**Pictorial Representation of Parallel Processing and its Inner Workings**

Parallel processing uses two or more processors or CPUs simultaneously to handle various components of a single activity. Systems can slash a program’s execution time by dividing a task’s many parts among several processors. Multi-core processors, frequently found in modern computers, and any system with more than one CPU are capable of performing parallel processing.

For improved speed, lower power consumption, and more effective handling of several activities, multi-core processors are integrated circuit (IC) chips with two or more CPUs. Most computers can have two to four cores, while others can have up to twelve. Complex operations and computations are frequently completed in parallel processing.

At the most fundamental level, the way registers are used distinguishes between parallel and serial operations. Shift registers operate serially, processing each bit one at a time, whereas registers with parallel loading process each bit of the word simultaneously. It is possible to manage parallel processing at a higher level of complexity by using a variety of functional units that perform the same or different activities simultaneously.

# **How Does Parallel Processing Work?**

In general, parallel processing refers to dividing a task between at least two microprocessors. The idea is very straightforward: a computer scientist uses specialized software created for the task to break down a complex problem into its component elements. Then, they designate a specific processor for each part. To complete the entire computing problem, each processor completes its portion. The software reassembles the data to solve the complex initial challenge.

When processing is done in parallel, a big job is broken down into several smaller jobs better suited to the number, size, and type of available processing units. After the task is divided, each processor starts working on its part without talking to the others. Instead, they use software to stay in touch with each other and find out how their tasks are going.

After all the program parts have been processed, the result is a fully processed program segment. This is true whether the number of processors and tasks and processors were equal and they all finished simultaneously or one after the other.

There are two types of parallel processes: fine-grained and coarse-grained. Tasks communicate with one another numerous times per second in fine-grained parallelism to deliver results in real-time or very close to real-time. The slower speed of coarse-grained parallel processes results from their infrequent communication.

A parallel processing system can process data simultaneously to complete tasks more quickly. For instance, the system could receive the next instruction from memory as the current instruction is processed by the CPU’s arithmetic-logic unit (ALU). The main goal of parallel processing is to boost a computer’s processing power and increase throughput, or the volume of work one can do in a given time. One can use many functional units to create a parallel processing system by carrying out similar or dissimilar activities concurrently.

This is a more sophisticated way of saying that dividing the work makes things easier. You could still split the load between different processors in the same computer, or it could be split between different computers connected by a [computer network](https://www.spiceworks.com/tech/networking/articles/what-is-a-computer-network/). Users can accomplish the same objective in several ways.

A computer scientist typically uses a software tool to break a complex task into smaller parts and assign each portion to a processor. Each processor will then solve its part, and the data will be put back together by a software tool to read the answer or carry out the operation.

Each CPU will normally function and carry out parallel tasks as directed while reading data from the computer’s memory. Processors will also use the software to communicate and keep track of changes in data values. After a task, the software will fit all the data fragments together, assuming that all the processors stay in sync. If computers are networked to form a cluster, one can use those without multiple processors for parallel computing.

# **Types of Parallel Processing**

There are various varieties of parallel processing, such as MMP, SIMD, MISD, SISD, and MIMD, of which SIMD is probably the most popular. Single instruction multiple data, or SIMD, is a parallel processing type where a computer has two or more processors that all follow the same instruction set but handle distinct data types. Let us now take a look at the various kinds of parallel processing and how they work:

![https://images.spiceworks.com/wp-content/uploads/2022/08/26122504/Types-of-Parallel-Processing.png](https://images.spiceworks.com/wp-content/uploads/2022/08/26122504/Types-of-Parallel-Processing.png)

**Types of Parallel Processing**

# **1. Single Instruction, Single Data (SISD)**

In the type of computing called Single Instruction, Single Data (SISD), a single processor is responsible for simultaneously managing a single algorithm as a single data source. A computer organization having a control unit, a processing unit, and a memory unit is represented by SISD. It is similar to the current serial computer. Instructions are carried out sequentially by SISD, which may or may not be capable of parallel processing, depending on its configuration.

Sequentially carried-out instructions may cross over throughout their execution phases. There may be more than one functional unit inside a SISD computer. However, one control unit is in charge of all functional units. Such systems allow for pipeline processing or using numerous functional units to achieve parallel processing.

# **2. Multiple Instruction, Single Data (MISD)**

Multiple processors are standard in computers that use the Multiple Instruction, Single Data (MISD) instruction set. While using several algorithms, all processors share the same input data. MISD computers can simultaneously perform many operations on the same batch of data. As expected, the number of operations is impacted by the number of processors available.

The MISD structure consists of many processing units, each operating under its instructions and over a comparable data flow. One processor’s output becomes the input for the following processor. This organization’s debut garnered little notice and wasn’t used in architecture.

# **3. Single Instruction, Multiple Data (SIMD)**

Computers that use the Single Instruction, Multiple Data (SIMD) architecture have multiple processors that carry out identical instructions. However, each processor supplies the instructions with its unique collection of data. SIMD computers apply the same algorithm to several data sets. The SIMD architecture has numerous processing components.

All of these components fall under the supervision of a single control unit. While processing numerous pieces of data, each processor receives the same instruction from the control unit. Multiple modules included in the shared subsystem aid in simultaneous communication with every CPU. This is further separated into organizations that use bit-slice and word-slice modes.

# **4. Multiple Instruction, Multiple Data (MIMD)**

Multiple Instruction, Multiple Data, or MIMD, computers are characterized by the presence of multiple processors, each capable of independently accepting its instruction stream. These kinds of computers have many processors. Additionally, each CPU draws data from a different data stream. A MIMD computer is capable of running many tasks simultaneously.

Although MIMD computers are more adaptable than SIMD or MIMD computers, developing the sophisticated algorithms that power these machines is more challenging. Since all memory flows are changed from the shared data area transmitted by all processors, a MIMD computer organization incorporates interactions between the multiprocessors.

The multiple SISD operation is equivalent to a collection of separate SISD systems if the many data streams come from various shared memories.

# **5. Single Program, Multiple Data (SPMD)**

SPMD systems, which stand for Single Program, Multiple Data, are a subset of MIMD. Although an SPMD computer is constructed similarly to a MIMD, each of its processors is responsible for carrying out the same instructions. SPMD is a message passing programming used in distributed memory computer systems. A group of separate computers, collectively called nodes, make up a distributed memory computer.

Each node launches its application and uses send/receive routines to send and receive messages when interacting with other nodes. Systems can also use messages to provide barrier synchronization. It is possible to transfer the messages via a wide range of communication techniques, such as [transmission control protocol (TCP/IP)](https://www.spiceworks.com/tech/networking/articles/what-is-tcp/) over Ethernet and specialized high-speed interconnects, such as Supercomputer Interconnect and Myrinet.

# **6. Massively Parallel Processing (MPP)**

A storage structure called Massively Parallel Processing (MPP) is made to manage the coordinated execution of program operations by numerous processors. With each CPU using its operating system and memory, this coordinated processing can be applied to different program sections.

As a result, MPP databases can handle enormous amounts of data and deliver analyses based on large datasets considerably faster. MPP processors typically communicate through a messaging interface and can have up to 200 or more processors working on an application. It functions by enabling the transmission of messages between processes via a set of corresponding data links.

The most common types of computers used in parallel processing systems are SIMD and MIMD. Although SISD computers can’t run in parallel on their own, a cluster can be created by connecting many of them. In a more extensive parallel system, the CPU of each computer can function as a processor. The computers work as a single supercomputer when used collectively. [Grid computing](https://www.spiceworks.com/tech/cloud/articles/what-is-grid-computing/) is the name of this method.

# **Vector Processing**

Vector processing is a **[central processing unit](https://www.tutorialspoint.com/computer_fundamentals/computer_cpu.htm)** that can perform the complete vector input in individual instruction. It is a complete unit of hardware resources that implements a sequential set of similar data elements in the memory using individual instruction.

The scientific and research computations involve many computations which require extensive and high-power computers. These computations when run in a conventional computer may take days or weeks to complete. The science and engineering problems can be specified in methods of vectors and matrices using vector processing.

## **Features of Vector Processing**

There are various features of Vector Processing which are as follows −

- A vector is a structured set of elements. The elements in a vector are scalar quantities. A vector operand includes an ordered set of n elements, where n is known as the length of the vector.
- Each clock period processes two successive pairs of elements. During one single clock period, the dual vector pipes and the dual sets of vector functional units allow the processing of two pairs of elements.
    
    As the completion of each pair of operations takes place, the results are delivered to appropriate elements of the result register. The operation continues just before the various elements processed are similar to the count particularized by the vector length register.
    
- In parallel vector processing, more than two results are generated per clock cycle. The parallel vector operations are automatically started under the following two circumstances −
    - When successive vector instructions facilitate different functional units and multiple vector registers.
    - When successive vector instructions use the resulting flow from one vector register as the operand of another operation utilizing a different functional unit. This phase is known as chaining.
- A vector processor implements better with higher vectors because of the foundation delay in a pipeline.
- Vector processing decrease the overhead related to maintenance of the loop-control variables which creates it more efficient than scalar processing.

# What is Interrupt?

The interrupt is a signal emitted by hardware or software when a process or an event needs immediate attention. It alerts the processor to a high-priority process requiring interruption of the current working process. In I/O devices one of the bus control lines is dedicated for this purpose and is called the **[*Interrupt Service Routine (ISR)*.](https://www.geeksforgeeks.org/difference-between-isr-and-function-call/)**

When a device raises an interrupt at let’s say process i, the processor first completes the execution of instruction i. Then it loads the **[Program Counter (PC)](https://www.geeksforgeeks.org/what-is-program-counter/)** with the address of the first instruction of the ISR. Before loading the Program Counter with the address, the address of the interrupted instruction is moved to a temporary location. Therefore, after handling the interrupt the processor can continue with process i+1.

While the processor is handling the interrupts, it must inform the device that its request has been recognized so that it stops sending the interrupt request signal. Also, saving the registers so that the interrupted process can be restored in the future, increases the delay between the time an interrupt is received and the start of the execution of the ISR. This is called Interrupt Latency.

# Types of Interrupt

Event-related software or hardware can trigger the issuance of interrupt signals. These fall into one of two categories: software interrupts or hardware interrupts.

### 1. Software Interrupts

A sort of interrupt called a software interrupt is one that is produced by software or a system as opposed to hardware. Traps and exceptions are other names for software interruptions. They serve as a signal for the operating system or a system service to carry out a certain function or respond to an error condition. Generally, software interrupts occur as a result of specific instructions being used or exceptions in the operation. In our system, software interrupts often occur when system calls are made. In contrast to the **[fork() system call](https://www.geeksforgeeks.org/fork-system-call-in-operating-system/)**, which also generates a software interrupt, division by zero throws an exception that results in the software interrupt.

A particular instruction known as an “interrupt instruction” is used to create software interrupts. When the interrupt instruction is used, the processor stops what it is doing and switches over to a particular interrupt handler code. The interrupt handler routine completes the required work or handles any errors before handing back control to the interrupted application.

### 2. Hardware Interrupts

In a hardware interrupt, all the devices are connected to the Interrupt Request Line. A single request line is used for all the n devices. To request an interrupt, a device closes its associated switch. When a device requests an interrupt, the value of INTR is the logical OR of the requests from individual devices.

Hardware interrupts are further divided into two types of interrupt

- **Maskable Interrupt:** Hardware interrupts can be selectively enabled and disabled thanks to an inbuilt interrupt mask register that is commonly found in processors. A bit in the mask register corresponds to each interrupt signal; on some systems, the interrupt is enabled when the bit is set and disabled when the bit is clear, but on other systems, the interrupt is deactivated when the bit is set.
- **Spurious Interrupt:** A hardware interrupt for which there is no source is known as a spurious interrupt. This phenomenon might also be referred to as phantom or ghost interrupts. When a wired-OR interrupt circuit is connected to a level-sensitive processor input, spurious interruptions are typically an issue. When a system performs badly, it could be challenging to locate these interruptions.

# **Handshaking**

Handshaking is an I/O control approach to synchronize I/O devices with the **[microprocessor](https://www.tutorialspoint.com/microprocessor/index.htm)**. As several I/O devices accept or release data at a much lower cost than the microprocessor, this technique is used to control the microprocessor to operate with an I/O device at the I/O devices data transfer rate.

The drawback of the strobe approach is that the source unit that starts the transfer has no method of knowing whether the destination unit has received the data element that was located in the bus. A destination unit that initiates the transfer has no method of knowing whether the source unit has located the information on the bus.

The handshake approach solves this issue by introducing a second control signal that supports a response to the unit that initiates the transfer. The basic feature of the two-wire handshaking approach of data transfer is as follows. One control line is in an equal direction as the data flow in the bus from the source to the destination.

It is used by the source unit to update the destination unit whether there are true data in the bus. The other control line is in the other direction from the destination to the source. It is used by the destination unit to update the source whether it can accept information. The sequence of control during the transfer is based on the unit that initiates the transfer.

The diagram shows the data transfer process when initiated by the source. The two handshaking lines are data valid, which is created by the source unit, and data accepted, created by the destination unit. The timing diagram displays the exchange of signals between the two units.

![https://www.tutorialspoint.com/assets/questions/media/54524/handshaking.jpg](https://www.tutorialspoint.com/assets/questions/media/54524/handshaking.jpg)

The sequence of events showed in part (c) shows the four possible states that the system can be at any given time. The source unit initiates the transfer by locating the information on the bus and enabling its data valid signal. The data accepted signal is activated by the destination unit after it obtains the data from the bus.

The destination-initiated transfer using handshaking lines is shown in the figure. The name of the signal created by the destination unit has been modified to ready for data to reflect its new definition. The source unit in this case does not locate data on the bus until after it takes the ready-for-data signal from the destination unit.

The sequence of events in both cases would be equal if it can consider the ready-for-data signal as the complement of data accepted. The only difference between the source-initiated and the destination-initiated transfer is in their choice of the initial state.

# **Priority Interrupts | (S/W Polling and Daisy Chaining)**

In **[I/O Interface (Interrupt and DMA Mode)](https://www.geeksforgeeks.org/io-interface-interrupt-dma-mode/)**, we have discussed the concept behind the Interrupt-initiated I/O. To summarize, when I/O devices are ready for I/O transfer, they generate an interrupt request signal to the computer. The CPU receives this signal, suspends the current instructions it is executing, and then moves forward to service that transfer request. But what if multiple devices generate interrupts simultaneously. In that case, we have a way to decide which interrupt is to be serviced first. In other words, we have to set a priority among all the devices for systemic interrupt servicing. The concept of defining the priority among devices so as to know which one is to be serviced first in case of simultaneous requests is called a priority interrupt system. This could be done with either software or hardware methods.

**SOFTWARE METHOD – POLLING**

In this method, all interrupts are serviced by branching to the same service program. This program then checks with each device if it is the one generating the interrupt. The order of checking is determined by the priority that has to be set. The device having the highest priority is checked first and then devices are checked in descending order of priority. If the device is checked to be generating the interrupt, another service program is called which works specifically for that particular device. The structure will look something like this-

```
if (device[0].flag)
    device[0].service();
else if (device[1].flag)
    device[1].service();
.
.
.
.
.
.
else
    //raise error
```

The major disadvantage of this method is that it is quite slow. To overcome this, we can use hardware solution, one of which involves connecting the devices in series. This is called Daisy-chaining method.

HARDWARE METHOD – DAISY CHAINING

The daisy-chaining method involves connecting all the devices that can request an interrupt in a serial manner. This configuration is governed by the priority of the devices. The device with the highest priority is placed first followed by the second highest priority device and so on. The given figure depicts this arrangement.

![https://media.geeksforgeeks.org/wp-content/uploads/dasiychaining.png](https://media.geeksforgeeks.org/wp-content/uploads/dasiychaining.png)

**WORKING:**

There is an interrupt request line which is common to all the devices and goes into the CPU.

- When no interrupts are pending, the line is in HIGH state. But if any of the devices raises an interrupt, it places the interrupt request line in the LOW state.
- The CPU acknowledges this interrupt request from the line and then enables the interrupt acknowledge line in response to the request.
- This signal is received at the PI(Priority in) input of device 1.
- If the device has not requested the interrupt, it passes this signal to the next device through its PO(priority out) output. (PI = 1 & PO = 1)
- However, if the device had requested the interrupt, (PI =1 & PO = 0)
    - The device consumes the acknowledge signal and block its further use by placing 0 at its PO(priority out) output.
    - The device then proceeds to place its interrupt vector address(VAD) into the data bus of CPU.
    - The device puts its interrupt request signal in HIGH state to indicate its interrupt has been taken care of.
- If a device gets 0 at its PI input, it generates 0 at the PO output to tell other devices that acknowledge signal has been blocked. (PI = 0 & PO = 0)

Hence, the device having PI = 1 and PO = 0 is the highest priority device that is requesting an interrupt. Therefore, by daisy chain arrangement we have ensured that the highest priority interrupt gets serviced first and have established a hierarchy. The farther a device is from the first device, the lower its priority.

# **Difference Between Machine Language and Assembly Language**

**Machine language** is the low level programming language. ***Machine language can only be represented by 0s and 1s*. I**n earlier when we have to create a picture or show data on the screen of the computer then it is very difficult to draw using only binary digits(0s and 1s). For example: To write 120 in the computer system its representation is 1111000. So it is very difficult to learn. To overcome this problem the assembly language is invented.

**Assembly language is the more than low level and less than high-level language so it is intermediary language**. Assembly languages use numbers, symbols, and abbreviations instead of 0s and 1s.For example: For addition, subtraction and multiplications it uses symbols likes Add, sub and Mul, etc.

![Untitled](C%20O%20A%20notes%20337e6c1c3a6640fd9a4eb887c8385fbc/Untitled%203.png)

| Machine Language | Assembly Language |
| --- | --- |
| Machine language is only understand by the computers. | Assembly language is only understand by human beings not by the computers. |
| In machine language data only represented with the help of binary format(0s and 1s), hexadecimal and octadecimal. | In assembly language data can be represented with the help of mnemonics such as Mov, Add, Sub, End etc. |
| Machine language is very difficult to understand by the human beings. | Assembly language is easy to understand by the human being as compare to machine language. |
| Modifications and error fixing cannot be done in machine language. | Modifications and error fixing can be done in assembly language. |
| Machine language is very difficult to memorize so it is not possible to learn the machine language. | Easy to memorize the assembly language because some alphabets and mnemonics are used. |
| Execution is fast in machine language because all data is already present in binary format. | Execution is slow as compared to machine language. |
| There is no need of translator.The machine understandable form is the machine language. | Assembler is used as translator to convert mnemonics into machine understandable form. |
| Machine language is hardware dependent. | Assembly language is the machine dependent and it is not portable. |

# Asynchronous Data Transfer

Asynchronous data transfer enables computers to send and receive data without having to wait for a real-time response. With this technique, data is conveyed in discrete units known as packets that may be handled separately. This article will explain what asynchronous data transfer is, its primary terminologies, advantages and disadvantages, and some frequently asked questions.

# Terminologies used in Asynchronous Data Transfer

- **Sender**: The machine or gadget that transfers the data.
- **Receiver**: A device or computer that receives data.
- **Packet**: A discrete unit of transmitted and received data.
- **Buffer**: A short-term location for storing incoming or departing data.

# Classification of Asynchronous Data Transfer

- **Strobe Control Method**
- **Handshaking Method**

![https://media.geeksforgeeks.org/wp-content/uploads/20230503170345/GFG-Asynchronus.png](https://media.geeksforgeeks.org/wp-content/uploads/20230503170345/GFG-Asynchronus.png)

### Strobe Control Method For Data Transfer

Strobe control is a method used in **[asynchronous](https://www.geeksforgeeks.org/difference-between-synchronous-and-asynchronous-transmission/)** data transfer that synchronizes data flow between two devices. Bits are transmitted one at a time, independently of one another, and without the aid of a clock signal in asynchronous communication. To properly receive the data, the receiving equipment needs to be able to synchronize with the transmitting device.

Strobe control involves sending data along with a different signal known as the strobe signal. The strobe signal alerts the receiving device that the data is valid and ready to be read. The receiving device waits for the strobe signal before reading the data to ensure sure it is synchronized with its clock.

The strobe signal is usually generated by the transmitting device and is sent either before or after the data. If the strobe signal is sent before the data, it is called a leading strobe. If it is sent after the data, it is called a trailing strobe.

![https://media.geeksforgeeks.org/wp-content/uploads/20230503174347/GFG-STROBE-METHOD.png](https://media.geeksforgeeks.org/wp-content/uploads/20230503174347/GFG-STROBE-METHOD.png)

*Types of Strobes*

It is advantageous to utilize strobe control because it enables asynchronous data transfer, which is helpful when the participating devices have dissimilar clock rates or are not synchronized. The time of data transfer is also made more flexible by strobe control since the receiving device doesn’t have to synchronize with the transmitting device’s clock; instead, it can wait for the strobe signal before reading the data.

Overall, strobe control, which is frequently employed in a range of electronic devices and systems, is a helpful technique for assuring dependable data flow in asynchronous communication.

### Handshaking Method For Data Transfer

During an asynchronous data transfer, two devices manage their communication using **handshaking**. It is guaranteed that the transmitting and receiving devices are prepared to send and receive data. Handshakes are essential in asynchronous communication since there is no clock signal to synchronize the data transfer.

During handshaking, we use two types of signals mostly they are request-to-send (RTS) and clear-to-send (CTS). The receiving device is notified by an RTS signal when the transmitting equipment is ready to provide data. The receiving device responds with a CTS signal when it is ready to accept data.

once data is transmitted to the receiver end. the receiver generates a signal that it has done by sending an acknowledgment (ACK) signal. If the data is not successfully received, the receiving device will notify that a new transmission is necessary via a **[negative acknowledgment](https://www.geeksforgeeks.org/sliding-window-protocol-set-3-selective-repeat/)** (NAK) signal.

The handshaking procedure guarantees synchronized and dependable data delivery. Additionally, it allows for flow management, preventing the transmitting device from sending the receiving device an excessive amount of data all at once. In order to offer flow control, handshaking signals are utilized to regulate the rate at which data is sent.

The Handshaking Method in asynchronous data transfer is used in different devices for the transfer of data to ensure reliable communication.