# DECA2Labs-Challenge
Here is my attempt at the DECA labs 2 challenge

**Hardware implementation**

I deccided to use a normal 8x8 multiplier and create software to make it work for 16x16 signed and unsigned.

<img width="916" alt="Image" src="https://github.com/user-attachments/assets/3581ddd8-cc45-4cde-847d-bd6d60c9b20d" />

*here is the multiplier*

due to us using the inherent MOV instruction format to add to EE1 IS I can take advantage of the structure of the ALU block as ALUOPC will already select the path i can just use

<img width="654" alt="Image" src="https://github.com/user-attachments/assets/0d8f04fc-e311-46f3-b7ec-2df55a438b0b" />

*here is that path in ALU block- you can also see me adding another MUX and a MULTI select input which i will get from the DPECODE block*

-its worth noting i am using the first 8 bits of each input block-



*here is my implementation of the dpecode*

I have made multiselkect by checking address 'c' for MOV is not equal to 0 and make sure that the ALU instruction select is MOV in the right format (<ins>i do not need to worry if MOV is selected here as it will already happen in the ALU thanks to the way i added the muxs</ins>).

I also wanted my address structure to be MOVc Ra , Rb , Rc to compute Rb := Ra * Rc so ive added multis select into the AD1selc to get this format for the register file.

<img width="711" alt="Image" src="https://github.com/user-attachments/assets/2b085b74-3e38-4333-98df-eaf2aba5e042" />

This is all the hardware I added, in order too implement the 16bit by 16bit and signed multiplication i have made some software.

Here is the 8bit by 8bit test just to show that my new instruction works
<img width="359" alt="image" src="https://github.com/user-attachments/assets/30e7bd06-21f6-4882-9793-8b6fa43b5728" />
<img width="994" alt="image" src="https://github.com/user-attachments/assets/c03d4375-7202-4f4e-91fb-3c9c6a38b250" />
Here we see the result and see the 63 * 127 = 8001 which is correct

16bit by 16bit is much more confusing as i have to perform the neccessary multiplies on the various blocks of 8 bits a bit like expanding double brackets.
I used shifts to get these in the necessary positions to be multiplied and again shifting in order to deal with the results

<img width="272" alt="Image" src="https://github.com/user-attachments/assets/6db26c2a-2544-453f-acd2-03a4018ab94f" />
<img width="817" alt="Image" src="https://github.com/user-attachments/assets/90a59a54-008a-4b32-8383-840d21cbc6cc" />


And so 0x10A52A10 = 279259664 and equal to 13457 * 20752 showing this program works again significantly reducing the amount of cycles required.
