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

