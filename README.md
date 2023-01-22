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
```
Step 1: Module Declaration. module is a keywords defined in Verilog . 
Step 2: Input-Output Delecaration. Clock and reset are the inputs. 
Step 3: Declare the always keyword. 
Step 4: Use if loop for the functionality. 
Step 5: Assign the counter_up & _down. 
Step 6: End the module
```
### PROGRAM 

Program for flipflops  and verify its truth table in quartus using Verilog programming.
Developed by: M.Chandru
RegisterNumber: 22008631

```
UP COUNTER:

module uc(input clk,input reset,output[0:3]counter);
reg[0:3] counter_up;
always@(posedge clk or posedge reset)
begin
if(reset)
counter_up<=4'd0;
else
counter_up<=counter_up+4'd1;
end
assign counter=counter_up;
endmodule
```
```
DOWN COUNTER:

module dc(input clk,input reset,output[0:3]counter);
reg[0:3] counter_down;
always@(posedge clk or posedge reset)
begin
if(reset)
counter_down<=4'd0;
else
counter_down<=counter_down-4'd1;
end
assign counter=counter_down;
endmodule
```

### RTL LOGIC UP COUNTER AND DOWN COUNTER  

UP COUNTER

![image](https://user-images.githubusercontent.com/119393023/213902290-f7b34ca5-7db1-4f00-9bdf-db26f5be17ee.png)

DOWN COUNTER

![image](https://user-images.githubusercontent.com/119393023/213902300-4cd45e04-c5ce-4833-b283-29b490d183b7.png)

### TIMING DIGRAMS FOR COUNTER  

UP COUNTER:

![image](https://user-images.githubusercontent.com/119393023/213902320-7b3b69b9-4770-461e-8188-f7b6de54a34a.png)

DOWN COUNTER:

![image](https://user-images.githubusercontent.com/119393023/213902334-c0e2be3b-8d3d-4603-9e2a-52bf58890a47.png)

### TRUTH TABLE 

UP COUNTER

![image](https://user-images.githubusercontent.com/119393023/213902350-b5ea0741-4906-472c-ad9a-801a6c55c0de.png)

DOWN COUNTER

![image](https://user-images.githubusercontent.com/119393023/213902364-fff6023b-fc07-4d2c-bf83-5aefc8a5fccc.png)

### RESULTS 
4 bit up and down counters are implemented and its functionality is validated successfully.
