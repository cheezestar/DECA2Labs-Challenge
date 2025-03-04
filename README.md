# DECA2Labs-Challenge
Here is my attempt at the DECA labs 2 challenge

**Hardware implementation**

I deccided to use a normal 8x8 multiplier and create software to make it work for 16x16 signed and unsigned.

<img width="916" alt="Image" src="https://github.com/user-attachments/assets/3581ddd8-cc45-4cde-847d-bd6d60c9b20d" />

*here is the multiplier*

due to us using the inherent MOV instruction format to add to EE1 IS I can take advantage of the structure of the ALU block as ALUOPC will already select the path i can just use

<img width="654" alt="Image" src="https://github.com/user-attachments/assets/0d8f04fc-e311-46f3-b7ec-2df55a438b0b" />

*here is that path in ALU block- you can also see me adding another MUX and a MULTI select input which i will get from the DPECODE block*
