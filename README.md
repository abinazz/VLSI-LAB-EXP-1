# VLSI-LAB-EXPERIMENTS
AIM: To simulate and synthesis Logic Gates,Adders and Subtractor using Xilinx ISE.

APPARATUS REQUIRED: Vivado 2023.1


PROCEDURE: 
1. Open Vivado: Launch Xilinx Vivado software on your computer.

2. Create a New Project: Click on "Create Project" from the welcome page or navigate through "File" > "Project" > "New".

3. Project Settings: Follow the prompts to set up your project. Specify the project name, location, and select RTL project type.

4. Add Design Files: Add your Verilog design files to the project. You can do this by right-clicking on "Design Sources" in the Sources window, then selecting "Add Sources". Choose your Verilog files from the file browser.

5. Specify Simulation Settings: Go to "Simulation" > "Simulation Settings". Choose your simulation language (Verilog in this case) and simulation tool (Vivado Simulator).

6. Run Simulation: Go to "Flow" > "Run Simulation" > "Run Behavioral Simulation". This will launch the Vivado Simulator and compile your design for simulation.

7. Set Simulation Time: In the Vivado Simulator window, set the simulation time if it's not set automatically. This determines how long the simulation will run.

8. Run Simulation: Start the simulation by clicking on the "Run" button in the simulation window.

9. View Results: After the simulation completes, you can view waveforms, debug signals, and analyze the behavior of your design.
Logic Diagram :

Logic Gates:
![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/ee17970c-3ac9-4603-881b-88e2825f41a4)


Half Adder:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/0e1ecb96-0c25-4556-832b-aeeedfdfe7b9)


Full adder:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/9bb3964c-438f-469d-a3de-c1cca6f323fb)


Half Subtractor:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/731470b7-eb4e-49f8-8bb7-2994052a7184)



Full Subtractor:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/d66f874b-c1f2-44b3-a035-7149b56430c1)



8 Bit Ripple Carry Adder

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/7385a408-40a5-4203-8050-b72818622d79)



VERILOG CODE:

# Program
# Logic Gates:
```
module logicgate (a,b,andgate,orgate,xorgate,nandgate,norgate,xnorgate,notgate);
input a,b;  
output andgate,orgate,xorgate,nandgate,norgate,xnorgate,notgate;
and(andgate,a,b);
or(orgate,a,b);
xor(xorgate,a,b);
nand(nandgate,a,b); 
nor(norgate,a,b);
xnor(xnorgate,a,b);
not(notgate,a);
endmodule
```
# Half Adder:
```
module halfadder(a,b,sum,carry);
input a,b;
output sum,carry;
xor g1(sum,a,b);
and g2(carry,a,b);
endmodule
```
# Half Subractor:
```
module halfsubtractor(a,b,diff,borrow);
input a,b;
output diff,borrow;
xor g1(diff,a,b);
and g2(borrow,~a,b);
endmodule
```
# Full Adder:
```
module fadd(a,b,c,sum,carry);
input a,b,c;
output sum,carry;
wire w1,w2,w3;
xor g1(w1,a,b);
and g2(w2,a,b);
xor g3(sum,w1,c);
and g4(w3,w1,c);
or g5(carry,w3,w2);
endmodule
```
# Full Subtractor:
```
module fs(a,b,bin,d,bout);
input a,b,bin; 
output d,bout;
wire w1,w2,w3;
xor g1(w1,b,bin; 
xor g2(d,w1,a);
and g3(w2,a,~w1);
and g4(w3,~b,bin);
or g5(bout,w2,w3);
endmodule
```
# 4 bit ripple carry adder:
```
module rippe_adder(S,Cout,X,Y,Cin);
input [3:0] X,Y;
input Cin;
output [3:0] S;
output Cout;
wire w1,w2,w3;
fulladder u1(S[0],w1,X[0],Y[0],Cin);
fulladder u2(S[1],w2,X[1],Y[1],w1);
fulladder u3(S[2],w3,X[2],Y[2],w2);
fulladder u4(S[3],Cout,X[3],Y[3],w3);
endmodule

module fulladder(S,CO,X,Y,Ci);
input X,Y,Ci;
output S,CO;
wire w1,w2,w3;
xor G1(w1,X,Y);
xor G2(S,w1,Ci);
and G3(w2,X,Ci);
and G4(w3,X,Y);
or G5(CO,w3,w3);
endmodule
```
# 8 bit ripple carry adder:
```
module rippe_adder(S,Cout,X,Y,Cin);
input [7:0] X,Y;
input Cin;
output [7:0] S;
output Cout;
wire w1,w2,w3,w4,w5,w6,w7;
fulladder u1(S[0],w1,X[0],Y[0],Cin);
fulladder u2(S[1],w2,X[1],Y[1],w1);
fulladder u3(S[2],w3,X[2],Y[2],w2);
fulladder u4(S[3],w4,X[3],Y[3],w3);
fulladder u5(S[4],w5,X[4],Y[4],w4);
fulladder u6(S[5],w6,X[5],Y[5],w5);
fulladder u7(S[6],w7,X[6],Y[6],w6);
fulladder u8(S[7],Cout,X[7],Y[7],w7);
endmodule

module fulladder(S,CO,X,Y,Ci);
input X,Y,Ci;
output S,CO;
wire w1,w2,w3;
xor G1(w1,X,Y);
xor G2(S,w1,Ci);
and G3(w2,X,Ci);
and G4(w3,X,Y);
or G5(CO,w3,w3);
endmodule
```

OUTPUT:

# OR gate:
![OR  gate](https://github.com/navaneethans/VLSI-LAB-EXP-1/assets/165630162/366cb360-2e37-463c-968c-999f0230738a)
# NOT gate:
![NOT gate](https://github.com/navaneethans/VLSI-LAB-EXP-1/assets/165630162/9bd8b890-442e-4106-b9eb-c00a75cf1df4)
# AND gate:
![AND gate](https://github.com/navaneethans/VLSI-LAB-EXP-1/assets/165630162/a117eeea-cd9c-4fd2-8271-18b8b74eb4dd)
# NAND gate:
![NAND gate](https://github.com/navaneethans/VLSI-LAB-EXP-1/assets/165630162/1894223b-7b48-443c-897d-b6a6aaf5fd67)
# NOR gate:
![NOR gate](https://github.com/navaneethans/VLSI-LAB-EXP-1/assets/165630162/13886c1c-7ff3-433d-b12b-1ad178a6ffc4)
# XNOR gate:
![XNOR gate](https://github.com/navaneethans/VLSI-LAB-EXP-1/assets/165630162/db24bdaa-a80e-4293-8d3a-5cf533e056bb)
# XOR gate:
![XOR gate](https://github.com/navaneethans/VLSI-LAB-EXP-1/assets/165630162/730e6e80-328e-4bb7-84fc-76d2f0081324)
# Half Adder:
![HALF ADDER](https://github.com/navaneethans/VLSI-LAB-EXP-1/assets/165630162/42557c0c-3870-4abb-899f-33299ecdebb9)
# Half Subtracter:
![HALF SUB](https://github.com/navaneethans/VLSI-LAB-EXP-1/assets/165630162/a3040bb4-69a6-4dfe-87ff-eb7e5057037f)
# Full Adder:
![FULL ADDER](https://github.com/navaneethans/VLSI-LAB-EXP-1/assets/165630162/3da7c03c-33b1-45d6-b1e0-7ebf39c2f766)
# Full Subtracter:
![FULL SUB](https://github.com/navaneethans/VLSI-LAB-EXP-1/assets/165630162/a175a707-e52e-4452-9d10-de0eab1c841e)
# 4 Bit Ripple Carry Adder:
![4 BIT](https://github.com/navaneethans/VLSI-LAB-EXP-1/assets/165630162/51203939-dfac-4e5b-b0e9-014333ef902c)
# 8 Bit Ripple Carry Adder:
![8 BIT](https://github.com/navaneethans/VLSI-LAB-EXP-1/assets/165630162/5d6e7310-32b8-43ed-8f48-222cd7305736)

RESULT: simulation of Logic Gates ,Adders and Subtractors using Vivado 2023.2 completed successfully
