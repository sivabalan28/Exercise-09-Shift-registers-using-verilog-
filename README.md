
# Experiment--09-Implementation-of Shift-registers-using-verilog-
### AIM: To implement PISO , PIPO,PISO  using verilog and validating their functionality using their functional tables
### HARDWARE REQUIRED:  – PC, Cyclone II , USB flasher
### SOFTWARE REQUIRED:   Quartus prime
### THEORY 
Shift registers are basically of 4 types. These are:

Serial In Serial Out shift register
Serial In parallel Out shift register
Parallel In Serial Out shift register
Parallel In parallel Out shift register
Serial-In Serial-Out Shift Register (SISO) –
The shift register, which allows serial input (one bit after the other through a single data line) and produces a serial output is known as Serial-In Serial-Out shift register. Since there is only one output, the data leaves the shift register one bit at a time in a serial pattern, thus the name Serial-In Serial-Out Shift Register.

The logic circuit given below shows a serial-in serial-out shift register. The circuit consists of four D flip-flops which are connected in a serial manner. All these flip-flops are synchronous with each other since the same clock signal is applied to each flip flop.

![image](https://user-images.githubusercontent.com/36288975/172337366-540cc45e-11fe-4cce-9503-560dc704bc7d.png)
FIGURE -01 
erial-In Parallel-Out shift Register (SIPO) –
The shift register, which allows serial input (one bit after the other through a single data line) and produces a parallel output is known as Serial-In Parallel-Out shift register.

The logic circuit given below shows a serial-in-parallel-out shift register. The circuit consists of four D flip-flops which are connected. The clear (CLR) signal is connected in addition to the clock signal to all the 4 flip flops in order to RESET them. The output of the first flip flop is connected to the input of the next flip flop and so on. All these flip-flops are synchronous with each other since the same clock signal is applied to each flip flop.

![image](https://user-images.githubusercontent.com/36288975/172337438-03416c7e-7c9d-4939-ba34-c355b9fc79c5.png)
FIGURE-02
The above circuit is an example of shift right register, taking the serial data input from the left side of the flip flop and producing a parallel output. They are used in communication lines where demultiplexing of a data line into several parallel lines is required because the main use of the SIPO register is to convert serial data into parallel data.
Parallel-In Serial-Out Shift Register (PISO) –
The shift register, which allows parallel input (data is given separately to each flip flop and in a simultaneous manner) and produces a serial output is known as Parallel-In Serial-Out shift register.

The logic circuit given below shows a parallel-in-serial-out shift register. The circuit consists of four D flip-flops which are connected. The clock input is directly connected to all the flip flops but the input data is connected individually to each flip flop through a multiplexer at the input of every flip flop. The output of the previous flip flop and parallel data input are connected to the input of the MUX and the output of MUX is connected to the next flip flop. All these flip-flops are synchronous with each other since the same clock signal is applied to each flip flop.
![image](https://user-images.githubusercontent.com/36288975/172337544-1632407f-1743-4b17-b480-00663d01e59f.png)
FIGURE-03
A Parallel in Serial out (PISO) shift register us used to convert parallel data to serial data.

Parallel-In Parallel-Out Shift Register (PIPO) –
The shift register, which allows parallel input (data is given separately to each flip flop and in a simultaneous manner) and also produces a parallel output is known as Parallel-In parallel-Out shift register.

The logic circuit given below shows a parallel-in-parallel-out shift register. The circuit consists of four D flip-flops which are connected. The clear (CLR) signal and clock signals are connected to all the 4 flip flops. In this type of register, there are no interconnections between the individual flip-flops since no serial shifting of the data is required. Data is given as input separately for each flip flop and in the same way, output also collected individually from each flip flop![image](https://user-images.githubusercontent.com/36288975/172337661-babb1f90-6286-4d14-8cbd-26a380ee085e.png)
FIGURE-04
A Parallel in Parallel out (PIPO) shift register is used as a temporary storage device and like SISO Shift register it acts as a delay element.

### Procedure
1.Use quartus software and import required modules. 

2.Assign inputs and outputs for shift registers. 

3.Assign logic for input to give output at positive edge. 

4.Perform opertaions and produce rtl circuit. 

5.End module

### PROGRAM  
```
/*
Program for  Implementation-of Shift-registers-using-verilog-
Developed by: SIVABALAN S
RegisterNumber:  212222240100
*/

module SIPO(c,si,po);
input c,si;
output [7:0] po;
reg [7:0] temp;
always @ (posedge c)
begin
temp = {temp[6:0],si};
end
assign po = temp;
endmodule 
```

### RTL LOGIC  REGISTERS   
![243533973-4d09af2e-4dfd-4cdb-980a-a770465d50c3](https://github.com/sivabalan28/Exercise-09-Shift-registers-using-verilog-/assets/113497347/dd023a46-b524-4982-b88f-3b9249eaafbe)

### TIMING DIGRAMS FOR SHIFT REGISTERS
![243533996-3ad920b6-53ef-4728-ac5b-fe48b8844dc5](https://github.com/sivabalan28/Exercise-09-Shift-registers-using-verilog-/assets/113497347/3c0107a6-580b-4c39-9a0d-f2ceb9ea459b)

## PROGRAM 2:
```
mmodule PISO(Clk,Pin,load,so);
input load,Clk;
input [3:0] Pin;
output reg so;
reg [3:0] temp;
always @ (posedge Clk)
begin 
if(load)
temp <= Pin;
else
begin
so<=temp[3];
temp <={temp[2:0],1'b0};
end
end
endmodule
```

### RTL LOGIC  REGISTERS   
![243534144-e8e0334c-03e6-4ad6-97cd-59d01a135ad2](https://github.com/sivabalan28/Exercise-09-Shift-registers-using-verilog-/assets/113497347/46b6abd2-f1c9-40e7-a9c2-27dca99e3b95)

### TIMING DIGRAMS FOR SHIFT REGISTERS
![243534186-f2646094-da78-4b64-af5e-490d5cedcf63](https://github.com/sivabalan28/Exercise-09-Shift-registers-using-verilog-/assets/113497347/a367fd50-4378-42bc-8a9f-bc4b052a20fb)

## PROGRAM 3:
 ```
 module PIPO (Po,Pi,clk);
input clk;
input[3:0] Pi;
output reg[3:0] Po;
always@(posedge clk)
begin
Po=Pi;
end 
endmodule
```

### RTL LOGIC  REGISTERS   
![243534343-c46a988d-8ce5-438c-81fa-682a7e442d56](https://github.com/sivabalan28/Exercise-09-Shift-registers-using-verilog-/assets/113497347/399404e4-bba1-4a2e-8e55-d7dba5e9c788)

### TIMING DIGRAMS FOR SHIFT REGISTERS
![243534502-f1bb08f0-24cd-4355-bbb1-ea2a04a95675](https://github.com/sivabalan28/Exercise-09-Shift-registers-using-verilog-/assets/113497347/84df2030-9691-4f6c-b4ea-a00bfa8f951b)

### RESULTS 
Thus the program to implement shift registers is done successful.
