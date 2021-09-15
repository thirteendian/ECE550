# ECE 550D Project 1
# By Yuxuan Yang (NetID: yy340)

I apologize that my previous Group partner join another group without notifying me until 2 days before deadline, and I do not have time to find another one.
All contains in project 1 are my own works.

14 Sep 2021

## Carry Lookahead adder (CLA)
In this project, a carry lookahead adder ALU was generated using verilog under Quartus IDE.

This is a 2 Level lookahead adder, by firstly calculating the generator G and propragator P following by a 8-bit Block Carry Lookahead Adder Unit(BCLA), to generate block level G* and P*. Thus the second level Carry Lookahead Adder Unit "CLAU" will use 4 of this BCLA to form 32-bit operation in total.

- `alu.v` (Officially provided): top level files of whole ALU. Contains selection mode depends on 5 bit ctrl_ALUopcode.
- `alu_tb.v`(Officially provided): top level testbench
- `BCLU.v`(8-bit Block Carry Lookahead Adder): Calculate 8-bit G, P, Sum, and carry out, the last bit carry out was merged in G* and P* in order to calculate at second level.
- `CLAU.v`(32-bit Carry Lookahead Adder): formed by 4 8-bit BCLU, parallel calculate 4 remain carry out, and all sum results.
- `add.v`(32-bit Adder): Call CLAU to do simple 32-bit add operation, with c_0=1'b0
- `subtract.v`(32-bit Subtractor): Call CLAU to do simple 32-bit subtract operation. Note that A-B=A+(-B)+1, thus preprocessing each bit of b using not gate, then initial CLAU with c_0=1'b1.

The project passed the testbench provided above.

