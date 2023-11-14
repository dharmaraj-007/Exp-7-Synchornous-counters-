# Exp-6-Synchornous-counters - up counter and down counter 
### AIM: To implement 4 bit up and down counters and validate  functionality.
### HARDWARE REQUIRED:  – PC, Cyclone II , USB flasher
### SOFTWARE REQUIRED:   Quartus prime
### THEORY 

## UP COUNTER 
The counter is a digital sequential circuit and here it is a 4 bit counter, which simply means it can count from 0 to 15 and vice versa based upon the direction of counting (up/down). 

The counter (“count“) value will be evaluated at every positive (rising) edge of the clock (“clk“) cycle.
The Counter will be set to Zero when “reset” input is at logic high.
The counter will be loaded with “data” input when the “load” signal is at logic high. Otherwise, it will count up or down.
The counter will count up when the “up_down” signal is logic high, otherwise count down

Since we know that binary count sequences follow a pattern of octave (factor of 2) frequency division, and that J-K flip-flop multivibrators set up for the “toggle” mode are capable of performing this type of frequency division, we can envision a circuit made up of several J-K flip-flops, cascaded to produce four bits of output.
The main problem facing us is to determine how to connect these flip-flops together so that they toggle at the right times to produce the proper binary sequence.
Examine the following binary count sequence, paying attention to patterns preceding the “toggling” of a bit between 0 and 1:
Binary count sequence, paying attention to patterns preceding the “toggling” of a bit between 0 and 1.

Note that each bit in this four-bit sequence toggles when the bit before it (the bit having a lesser significance, or place-weight), toggles in a particular direction: from 1 to 0.



 
 

Starting with four J-K flip-flops connected in such a way to always be in the “toggle” mode, we need to determine how to connect the clock inputs in such a way so that each succeeding bit toggles when the bit before it transitions from 1 to 0.

The Q outputs of each flip-flop will serve as the respective binary bits of the final, four-bit count:

 
 

Four-bit “Up” Counter
![image](https://user-images.githubusercontent.com/36288975/169644758-b2f4339d-9532-40c5-af40-8f4f8c942e2c.png)



## DOWN COUNTER 

As well as counting “up” from zero and increasing or incrementing to some preset value, it is sometimes necessary to count “down” from a predetermined value to zero allowing us to produce an output that activates when the zero count or some other pre-set value is reached.

This type of counter is normally referred to as a Down Counter, (CTD). In a binary or BCD down counter, the count decreases by one for each external clock pulse from some preset value. Special dual purpose IC’s such as the TTL 74LS193 or CMOS CD4510 are 4-bit binary Up or Down counters which have an additional input pin to select either the up or down count mode.
![image](https://user-images.githubusercontent.com/36288975/169644844-1a14e123-7228-4ed8-81a9-eb937dff4ac8.png)


4-bit Count Down Counter
### Procedure
/* write all the steps invloved */



### PROGRAM 
Program for flipflops  and verify its truth table in quartus using Verilog programming.

Developed by: Dharmaraj S

RegisterNumber: 212222240025

### UPCOUNTER:
```
module upcounter(A,clk);
output reg [3:0]A;
input clk;
always@(posedge clk)
begin
	A[3]=(A[2]&A[1]&A[0])^A[3];
	A[2]=(A[1]&A[0])^A[2];
	A[1]=(A[0]^A[1]);
	A[0]=1^A[0];
end
endmodule
```
### DOWN COUNTER:
```
module down(clk,A);
input clk;
output reg [3:0]A;
always @(posedge clk)
begin
A[3]=((~A[2])&(~A[1])&(~A[0]))^A[3];
A[2]=((~A[1])&(~A[0]))^A[2];
A[1]=(~A[0])^A[1];
A[0]=1^A[0];
end
endmodule
```
### RTL LOGIC UP COUNTER:
![Screenshot 2023-10-20 091905](https://github.com/Sabariakash22009103/Exp-7-Synchornous-counters-/assets/119390227/74d2d94d-b1aa-43ee-88ee-1b8dd244acc8)

### RTL LOGIC DOWN COUNTER:  
![279404680-dcd218c1-36be-4b55-99c0-c1e00efbe82f](https://github.com/Sabariakash22009103/Exp-7-Synchornous-counters-/assets/119390227/0161199c-acdc-41e4-91c2-57ea18a764be)

### Waveform Output for UP COUNTER :
![Screenshot 2023-10-20 091841](https://github.com/Sabariakash22009103/Exp-7-Synchornous-counters-/assets/119390227/74b15ad8-252f-475f-8211-8199b25d48f3)
### Waveform Output for UP COUNTER
![279404993-a847070e-1490-4341-8a2a-90cfaaf83d7d](https://github.com/Sabariakash22009103/Exp-7-Synchornous-counters-/assets/119390227/f3d2c0f8-dae4-43c2-9336-1d376dee2a8d)

### TRUTH TABLE For UPCOUNTER:
![image](https://github.com/Sabariakash22009103/Exp-7-Synchornous-counters-/assets/119390227/2fe67778-3cf1-4586-be32-fb59f3179daa)
### TRUTH TABLE For DOWN COUNTER:
![image](https://github.com/Sabariakash22009103/Exp-7-Synchornous-counters-/assets/119390227/6bf959e4-6983-4c9d-984e-7addc66a9fc7)

### RESULTS 
Thus the program has been executed successfully.
