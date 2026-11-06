# EC1801-DLC-EXP1
### EXPERIMENT 1 
### MINIMIZATION AND IMPLEMENTATION OF BOOLEAN FUNCTION
## Aim
To minimize and implement a Boolean function using logic gates and verify the functionality using Synopsys VCS and DVE.
## Software Required
•	Synopsys VCS
•	Synopsys DVE
•	Linux Terminal
•	Verilog HDL
## Boolean Function
Consider the Boolean function:
F(A,B,C,D)=Σm(0,2,5,7,8,10,13,15)
The minimized Boolean expression is: F=B'D'+BD
The function is implemented using Verilog HDL.
## Files Used
File	Description
exp1_boolean_min.v	Verilog design file
exp1_boolean_min_tb.v	Verilog testbench
exp1_boolean_min.vcd	VCD waveform dump generated during simulation

## Verilog Program
module boolfun (
input wire A, 
input wire B, 
input wire C, 
input wire D, 
output wire F 
); 
assign F = (~B & ~D)|(B & D) ;    // F = B'D' + BD 
endmodule

## TestBench Program
module boolfun_tb;

reg A, B, C, D;
wire F;

boolfun uut (
    .A(A),
    .B(B),
    .C(C),
    .D(D),
    .F(F)
);

initial begin

    $dumpfile("boolfun.vcd");
    $dumpvars(0, boolfun_tb);

    $monitor("Time=%0t A=%b B=%b C=%b D=%b F=%b",
              $time, A, B, C, D, F);

    A=0; B=0; C=0; D=0; #10;
    A=0; B=0; C=0; D=1; #10;
    A=0; B=0; C=1; D=0; #10;
    A=0; B=0; C=1; D=1; #10;

    A=0; B=1; C=0; D=0; #10;
    A=0; B=1; C=0; D=1; #10;
    A=0; B=1; C=1; D=0; #10;
    A=0; B=1; C=1; D=1; #10;

    A=1; B=0; C=0; D=0; #10;
    A=1; B=0; C=0; D=1; #10;
    A=1; B=0; C=1; D=0; #10;
    A=1; B=0; C=1; D=1; #10;

    A=1; B=1; C=0; D=0; #10;
    A=1; B=1; C=0; D=1; #10;
    A=1; B=1; C=1; D=0; #10;
    A=1; B=1; C=1; D=1; #10;

    $finish;
end

endmodule 
## Truth Table
 
<img width="719" height="308" alt="DLCD EXP 1 (1)" src="https://github.com/user-attachments/assets/6f013d2c-e95a-4560-92cb-7c709dfcf873" />

## Simulation Procedure
STEP 1 – Open Terminal
Open a terminal in the experiment folder.
bash

STEP 2 – Load Synopsys Environment
source /synopsys/start.sh

STEP 3 – Compile Using VCS
vcs exp1_boolean_min.v exp1_boolean_min_tb.v -full64
 
If compilation is successful, VCS generates the simulation executable:
simv

STEP 4 – Run Simulation
./simv
The terminal displays the input combinations and corresponding output F.
A VCD waveform file is also generated:
exp1_boolean_min.vcd

STEP 5 – Open DVE
dve -full64
Other option
dve -full64 &
A DVE environment will open.
## OUTPUT


## DVE Waveform Verification
In DVE:
1.	Open the testbench hierarchy.
2.	Locate the signals:
o	A
o	B
o	C
o	D
o	F
3.	Add the signals to the waveform window.
4.	Run/inspect the waveform.
5.	Verify that F = 1 whenever B and D are equal.
6.	Verify that F = 0 whenever B and D are different.
The waveform should agree with the truth table.


<img width="720" height="403" alt="DLCD EXP 2(2) " src="https://github.com/user-attachments/assets/3e0c431f-feb7-464e-8b23-00266cb0e367" />

### Expected Result
The Boolean function
F(A,B,C,D)=Σm(0,2,5,7,8,10,13,15), which simplifies to F=B'D'+BD.
was minimized to F=B'D'+BD.
and successfully implemented using Verilog HDL.
### OUTPUT
<img width="1920" height="1080" alt="Screenshot 2026-11-06 140941" src="https://github.com/user-attachments/assets/0bc7cefd-2781-4ab1-a4d8-91b7f67b0dc4" />




Result
Thus, the Boolean function was minimized, implemented using Verilog HDL, successfully simulated using Synopsys VCS, and verified using Synopsys DVE.

