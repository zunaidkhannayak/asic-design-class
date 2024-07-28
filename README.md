# asic-design-class
## Lab 1
### Task1: to make 
C program and compile it using gcc compiler. Verify the output of the C program after execution.

![Screenshot 2024-07-17 032110](https://github.com/user-attachments/assets/250bf18c-2089-41dd-886c-055933482989)

### task2:

The same c program was compiled using this command with riscv compiler:

`riscv64-unknown-elf-gcc -mabi=lp64 -march=rv64i -o sum1tot.o sum1ton.c`

After that the following command was used to dump the assembly code in the terminal:

`riscv64-unknown-elf-objdump -d sum1to1.o | less`


![Screenshot 2024-07-17 092335](https://github.com/user-attachments/assets/7a071373-a764-4698-857d-eab8acf6b801)

## Lab 2
 To Execute  the object file created by the RISC-V GCC compiler by use of Spike-Simulator.
 
for executing an object file created by the RISC-V GCC compiler we use the following command:
spike pk sum1ton.o
"pk" means proxy kernel.
The proxy kernel(pk) is a lightweight runtime environment for RISC-V programs, acting as a minimal operating system that provides essential services like system calls.
It helps to bridge the gap between simulator and application.
![Screenshot (7)](https://github.com/user-attachments/assets/038242d6-dac5-4a5a-b518-c38296583371)

Now debug using spike simulator
To debug the assembly code generated in the object file in using the spike.
we use following command:
spike -d pk sum1ton.c
![Screenshot (9)](https://github.com/user-attachments/assets/02bf2f4e-2b4d-4756-8501-f9ab74651bd0)
Now to jump to begining of the "main" section we  use following command:
until sp 0 0x100b0
![Screenshot (11)](https://github.com/user-attachments/assets/c4364c44-605c-4a34-917e-4dcdaa4f68ef)
![Screenshot (3)](https://github.com/user-attachments/assets/0dd6c3c9-c852-4657-a34c-970515b01199)
for checking value of any register we use following command:
reg 0 a0,
To execute the current instruction pointed by 'sp' and to appear on the next instruction, "Enter" button can be pressed to go to next instruction.
![Screenshot (12)](https://github.com/user-attachments/assets/dec0eb25-32ea-4519-966e-c23cbec376af)

## Lab 3
### Task 1 Identify various RISC V instruction type.
the instructions were given and thus we found out format of each instruction.

| **Operation/Task**                |
|-----------------------------------|
| `ADD r10, r11, r12`               |
| `SUB r12, r10, r11`               |
| `AND r11, r10, r12`               |
| `OR r8, r11, r5`                  |
| `XOR r8, r10, r4`                 |
| `SLT r00, r1, r4`                 |
| `ADDI r02, r2, 5`                 |
| `SW r2, r0, 4`                    |
| `SRL r06, r01, r1`                |
| `BNE r0, r0, 20`                 |
| `BEQ r0, r0, 15`                 |
| `LW r03, r01, 2`                  |
| `SLL r05, r01, r1`                |


| **Instruction** | **Operation**         | **Destination Register** | **Source Register 1** | **Source Register 2** | **Immediate/Offset** | **Instruction Format** |
|-----------------|------------------------|--------------------------|-----------------------|-----------------------|-----------------------|------------------------|
| `ADD`           | Addition               | `r10`                    | `r11`                 | `r12`                 | -                     | R-type                 |
| `SUB`           | Subtraction            | `r12`                    | `r10`                 | `r11`                 | -                     | R-type                 |
| `AND`           | Bitwise AND            | `r11`                    | `r10`                 | `r12`                 | -                     | R-type                 |
| `OR`            | Bitwise OR             | `r8`                     | `r11`                 | `r5`                  | -                     | R-type                 |
| `XOR`           | Bitwise XOR            | `r8`                     | `r10`                 | `r4`                  | -                     | R-type                 |
| `SLT`           | Set Less Than          | `r00`                    | `r1`                  | `r4`                  | -                     | R-type                 |
| `ADDI`          | Add Immediate          | `r02`                    | `r2`                  | -                     | `5`                   | I-type                 |
| `SW`            | Store Word             | -                        | `r2`                  | `r0`                  | `4`                   | I-type                 |
| `SRL`           | Shift Right Logical    | `r06`                    | `r01`                 | `r1`                  | -                     | R-type                 |
| `BNE`           | Branch if Not Equal    | -                        | `r0`                  | `r0`                  | `20`                  | I-type                 |
| `BEQ`           | Branch if Equal        | -                        | `r0`                  | `r0`                  | `15`                  | I-type                 |
| `LW`            | Load Word              | `r03`                    | `r01`                 | -                     | `2`                   | I-type                 |
| `SLL`           | Shift Left Logical     | `r05`                    | `r01`                 | `r1`                  | -                     | R-type                 |



now their hexadeximal representation 




| **Assembly Instruction** | **Hexadecimal Representation** |
|--------------------------|--------------------------------|
| `ADD r10, r11, r12`     | `0x013A6020`                  |
| `SUB r12, r10, r11`     | `0x01FAA020`                  |
| `AND r11, r10, r12`     | `0x013A6024`                  |
| `OR r8, r11, r5`        | `0x01B84025`                  |
| `XOR r8, r10, r4`       | `0x014A4026`                  |
| `SLT r00, r1, r4`       | `0x001A402A`                  |
| `ADDI r02, r2, 5`       | `0x00200320`                  |
| `SW r2, r0, 4`          | `0x0020002B`                  |
| `SRL r06, r01, r1`      | `0x00132102`                  |
| `BNE r0, r0, 20`        | `0x0000A0F0`                  |
| `BEQ r0, r0, 15`        | `0x0000A0E0`                  |
| `LW r03, r01, 2`        | `0x00230023`                  |
| `SLL r05, r01, r1`      | `0x00132100`                  |

### Task 2 To execute in instructed assembly instructions using a given verilog code for a riscV processor.

| **Operation**               | **Standard RISCV ISA** | **Hardcoded ISA** |
|-----------------------------|-------------------------|--------------------|
| `ADD r10, r11, r12`         | `32'h00c313b3`          | `32'h00c3b300`     |
| `SUB r12, r10, r11`         | `32'h40a303b3`          | `32'h40a3b380`     |
| `AND r11, r10, r12`         | `32'h00c3a533`          | `32'h00c3a400`     |
| `OR r8, r11, r5`            | `32'h0052a033`          | `32'h0052a400`     |
| `XOR r8, r10, r4`           | `32'h0042a033`          | `32'h0042a500`     |
| `SLT r00, r1, r4`           | `32'h0002a073`          | `32'h0002a500`     |
| `ADDI r02, r2, 5`           | `32'h0050a023`          | `32'h0050a200`     |
| `SW r2, r0, 4`              | `32'h0040a023`          | `32'h0040a300`     |
| `SRL r06, r01, r1`          | `32'h0001a073`          | `32'h0001a100`     |
| `BNE r0, r0, 20`            | `32'h0010f063`          | `32'h0010f200`     |
| `BEQ r0, r0, 15`            | `32'h00000e63`          | `32'h00000f00`     |
| `LW r03, r01, 2`            | `32'h0020a083`          | `32'h0020a100`     |
| `SLL r05, r01, r1`          | `32'h0001a033`          | `32'h0001a400`     |

on the terminal following command was used for execution

`iverilog -o Test_code Test_code.v Test_code_tb.b`

`./Test_code`

We can notice some difference between  the following two images when comparing as the verilog code availabe is not designed in agreement to the ISA which is used by me in this program.

`ADD r10, r11, r12`
The waveform for the above command using the provided verilog code is given below:
![1](https://github.com/user-attachments/assets/f791f458-f2e8-488a-8263-169749510a28)


The waveform for the hardcoded command present in the code is given below:
![1t](https://github.com/user-attachments/assets/c112439d-c1de-4dd3-8d00-2f349a48f3ea)



`SUB r12, r10, r11`
The waveform for the above command using the provided verilog code is given below:
![2](https://github.com/user-attachments/assets/4df0eff8-7d91-4e1c-ae01-77bc97b38b5b)

The waveform for the hardcoded command present in the code is given below:
![2t](https://github.com/user-attachments/assets/408486d6-0cc4-4978-b851-e762414fb3b6)


`AND r11, r10, r12`

The waveform for the above command using the provided verilog code is given below:


![3](https://github.com/user-attachments/assets/0d6e05cd-d5ba-4d2e-aa34-7f0fecfc6e35)

The waveform for the hardcoded command present in the code is given below:
![3t](https://github.com/user-attachments/assets/f6114a2e-47ce-4c37-816a-b40c4176158a)


`OR r8, r11, r5`
The waveform for the above command using the provided verilog code is given below:
![4](https://github.com/user-attachments/assets/5eb880b9-d7de-4cee-9b6b-ddd61fc17655)


The waveform for the hardcoded command present in the code is given below:
![4t](https://github.com/user-attachments/assets/ccf43786-3c9b-41b0-8a11-13d3556b7640)


`XOR r8, r10, r4`  
The waveform for the above command using the provided verilog code is given below:
![5](https://github.com/user-attachments/assets/be49cbce-8961-4e02-b4cf-b786c2d5a961)



The waveform for the hardcoded command present in the code is given below:

![5t](https://github.com/user-attachments/assets/f8215d09-690a-4ef7-a48f-def1a7e84317)


`SLT r00, r1, r4` 
The waveform for the above command using the provided verilog code is given below:

![6](https://github.com/user-attachments/assets/84949026-bdbb-4a62-812a-4345d496e357)


The waveform for the hardcoded command present in the code is given below:

![6t](https://github.com/user-attachments/assets/4b0bd2b3-3d41-436e-a3b0-f98e58440ba7)

`ADDI r02, r2, 5` 
The waveform for the above command using the provided verilog code is given below:
![7](https://github.com/user-attachments/assets/79643fbf-8d04-42c1-9782-f988a6aa1280)


The waveform for the hardcoded command present in the code is given below:
![7t](https://github.com/user-attachments/assets/6a909995-6ab4-4b09-af97-4d40ea723ba6)

