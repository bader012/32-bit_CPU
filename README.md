# 32-bit_CPU
COE 301 - Final Project

In this project, we designed a 32-bit RISC processor with eight 32-bit general-purpose registers: R0 through R7. R0 is a normal register, NOT hardwired to zero. The program counter PC is a special-purpose 20-bit register. All instructions are only 16 bits. There are four instruction formats, R-type, I-type, B-type and J-type.

**R-type format:**
5-bit opcode (Op), 3-bit register numbers (s, t, and d), and 2-bit function field (f). 

**I-type format:**
5-bit opcode (Op), 3-bit register numbers (s and t), and 5-bit Immediate (imm).

**B-type format:** 
5-bit opcode (Op), 3-bit register number s, and 8-bit Immediate (imm).

**J-type format:**
5-bit opcode (Op) and11-bit Immediate (imm).

| Instruction | Meaning                              | Encoding |       |      |      |       | 
|-------------|--------------------------------------|----------|-------|------|------|-------| 
| AND         | Rd = Rs & Rt                         | Op = 0   | s     | t    | d    | f = 0 | 
| CAND        | Rd = ~Rs & Rt (Complement Rs, AND)   | Op = 0   | s     | t    | d    | f = 1 | 
| OR          | Rd = Rs | Rt                         | Op = 0   | s     | t    | d    | f = 2 | 
| XOR         | Rd = Rs ^ Rt                         | Op = 0   | s     | t    | d    | f = 3 | 
| ADD         | Rd = Rs + Rt                         | Op = 1   | s     | t    | d    | f = 0 | 
| NADD        | Rd = –Rs + Rt (Negate Rs, ADD)       | Op = 1   | s     | t    | d    | f = 1 | 
| SLT         | Rd = Rs signed< Rt                   | Op = 1   | s     | t    | d    | f = 2 | 
| SLTU        | Rd = Rs unsigned< Rt                 | Op = 1   | s     | t    | d    | f = 3 | 
| ANDI        | Rt = Rs & sign_extend(Imm5)          | Op = 4   | s     | t    | Imm5 |       | 
| CANDI       | Rt = ~Rs & sign_extend(Imm5)         | Op = 5   | s     | t    | Imm5 |       | 
| ORI         | Rt = Rs OR sign_extend(Imm5)          | Op = 6   | s     | t    | Imm5 |       | 
| XORI        | Rt = Rs ^ sign_extend(Imm5)          | Op = 7   | s     | t    | Imm5 |       | 
| ADDI        | Rt = Rs + sign_extend(Imm5)          | Op = 8   | s     | t    | Imm5 |       | 
| NADDI       | Rt = –Rs + sign_extend(Imm5)         | Op = 9   | s     | t    | Imm5 |       | 
| SLTI        | Rt = Rs signed< sign_extend(Imm5)    | Op = 10  | s     | t    | Imm5 |       | 
| SLTUI       | Rt = Rs unsigned< sign_extend(Imm5)  | Op = 11  | s     | t    | Imm5 |       | 
| SLL         | Rt = Rs << Imm5                      | Op = 12  | s     | t    | Imm5 |       | 
| SRL         | Rt = Rs zero>> Imm5                  | Op = 13  | s     | t    | Imm5 |       | 
| SRA         | Rt = Rs sign>> Imm5                  | Op = 14  | s     | t    | Imm5 |       | 
| ROR         | Rt = Rs rotate>> Imm5                | Op = 15  | s     | t    | Imm5 |       | 
| LW          | Rt  MEM[Rs + Imm5]                  | Op = 16  | s     | t    | Imm5 |       | 
| SW          | MEM[Rs + Imm5]  Rt                  | Op = 17  | s     | t    | Imm5 |       | 
| BEQZ        | Branch if (Rs == 0) (PC = PC + Imm8) | Op = 20  | s     | Imm8 |      |       | 
| BNEZ        | Branch if (Rs != 0) (PC = PC + Imm8) | Op = 21  | s     | Imm8 |      |       | 
| BLTZ        | Branch if (Rs < 0) (PC = PC + Imm8)  | Op = 22  | s     | Imm8 |      |       | 
| BGEZ        | Branch if (Rs >= 0) (PC = PC + Imm8) | Op = 23  | s     | Imm8 |      |       | 
| BGTZ        | Branch if (Rs > 0) (PC = PC + Imm8)  | Op = 24  | s     | Imm8 |      |       | 
| BLEZ        | Branch if (Rs <= 0) (PC = PC + Imm8) | Op = 25  | s     | Imm8 |      |       | 
| JR          | PC = Rs + Imm8                       | Op = 26  | s     | Imm8 |      |       | 
| JALR        | R7 = PC+1; PC = Rs + Imm8            | Op = 27  | s     | Imm8 |      |       |       
| SET         | R0 = sign_extend(Imm11)              | Op = 28  | Imm11 |      |      |       | 
| SSET        | R0 = {R0<<11,  Imm11}                | Op = 29  | Imm11 |      |      |       | 
| J           | PC = PC + Imm11                      | Op = 30  | Imm11 |      |      |       | 
| JAL         | R7 = PC + 1; PC = PC + Imm11         | Op = 31  | Imm11 |      |      |       | 
