# SIMULATION AND IMPLEMENTATION OF MULTIPLIER
# AIM: 
 To simulate and synthesis multiplier using Xilinx ISE.

# APPARATUS REQUIRED:
VIVADO 2023.2

# PROCEDURE:
```
STEP:1  Start  the Xilinx navigator, Select and Name the New project.
STEP:2  Select the device family, device, package and speed.       
STEP:3  Select new source in the New Project and select Verilog Module as the Source type.                       
STEP:4  Type the File Name and Click Next and then finish button. Type the code and save it.
STEP:5  Select the Behavioral Simulation in the Source Window and click the check syntax.                       
STEP:6  Click the simulation to simulate the program and  give the inputs and verify the outputs as per the truth table.               
STEP:7  Select the Implementation in the Sources Window and select the required file in the Processes Window.
STEP:8  Select Check Syntax from the Synthesize  XST Process. Double Click in the  FloorplanArea/IO/Logic-Post Synthesis process in the User Constraints process group. UCF(User constraint File) is obtained. 
STEP:9  In the Design Object List Window, enter the pin location for each pin in the Loc column Select save from the File menu.
STEP:10 Double click on the Implement Design and double click on the Generate Programming File to create a bitstream of the design.(.v) file is converted into .bit file here.
STEP:11  On the board, by giving required input, the LEDs starts to glow light, indicating the output.
```
# 2 bit Multiplier

![image](https://github.com/navaneethans/VLSI-LAB-EXP-3/assets/6987778/7713750f-65e6-41c0-8082-5005eac4031c)

# CODE:
```
module ha(a,b,s,carry);
input a,b;
output s,carry;
assign carry=a&b;
endmodule
module multiplier_2(a,b,c);
input [1:0]a,b;
output [3:0]c;
wire w;
assign c[0]=a[0]&b[0];
ha h1(a[0]&b[1],a[1]&b[0],c[1],w);
ha h2(a[1]&b[1],w,c[2],c[3]);
endmodule.
```
# OUTPUT:
![image](https://github.com/Devikavijaya/VLSI-LAB-EXP-3/assets/164987794/f6c0d03a-0f44-410a-b087-e957acdb1f4b)

# 4 Bit Multiplier

![image](https://github.com/navaneethans/VLSI-LAB-EXP-3/assets/6987778/d95215dd-8cf1-4e08-93cc-96adfdd7fbdc)


# CODE:
```
module ha(a,b,sum,carry);
input a,b;
output sum,carry;
assign sum=a^b;
assign carry=a&b;
endmodule

module fa(a,b,c,sum,carry);
input a,b,c;
output sum,carry;
assign sum=a^b^c;
assign carry=(a&b)|(b&c)|(a&c);
endmodule

module multi_4(a,b,p);
input[3:0]a,b;
output [7:0]p;
wire [17:1]w;
assign p[0]=a[0]&b[0];
ha h1(a[1]&b[0],a[0]&b[1],p[1],w[1]);
fa f1(w[1],a[2]&b[0],a[1]&b[1],w[2],w[3]);
fa f2(w[3],a[3]&b[0],a[2]&b[1],w[4],w[5]);
ha h2(a[3]&b[1],w[5],w[6],w[7]);
ha h3(a[0]&b[2],w[2],p[2],w[8]);
fa f3(w[8],a[1]&b[2],w[4],w[9],w[10]);
fa f4(w[10],a[2]&b[2],w[6],w[11],w[12]);
fa f5(w[12],w[7],a[3]&b[2],w[13],w[14]);
ha h4(a[0]&b[3],w[9],p[3],w[15]);
fa f6(w[15],a[1]&b[3],w[11],p[4],w[16]);
fa f7(w[16],a[2]&b[3],w[13],p[5],w[17]);
fa f8(w[17],w[14],a[3]&b[3],p[6],p[7]);
endmodule.
```
# OUTPUT:
![image](https://github.com/Devikavijaya/VLSI-LAB-EXP-3/assets/164987794/f502fb91-140a-420f-b22d-29259c61ede1)

# RESULT:
```
The simulate and synthesis multiplier using VIVADO is successfully verified.
```



