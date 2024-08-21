# ASIC-design-class
<details>
 
<summary> <h2>Lab1</h2> </summary>

### Task1: 
To make a C program and compile it using gcc compiler. Verify the output of the C program after execution.

![Screenshot 2024-07-17 032110](https://github.com/user-attachments/assets/250bf18c-2089-41dd-886c-055933482989)

### task2:

The same c program was compiled using this command with riscv compiler:

`riscv64-unknown-elf-gcc -mabi=lp64 -march=rv64i -o sum1tot.o sum1ton.c`

After that the following command was used to dump the assembly code in the terminal:

`riscv64-unknown-elf-objdump -d sum1to1.o | less`


![Screenshot 2024-07-17 092335](https://github.com/user-attachments/assets/7a071373-a764-4698-857d-eab8acf6b801)
</details>


<details>
 
<summary> <h2>Lab2</h2> </summary>
 
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
</details>


 
<details>
 
<summary> <h2>Lab 3</h2> </summary>
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


`SW r2, r0, 4`

The waveform for the above command using the provided verilog code is given below:
![8](https://github.com/user-attachments/assets/439d0d49-f303-42b9-a417-ac72dc788150)

The waveform for the hardcoded command present in the code is given below:
![8t](https://github.com/user-attachments/assets/1a04cc75-fcc0-45f5-a4f2-f3a70bd02c88)

`SRL r06, r01, r1`

The waveform for the above command using the provided verilog code is given below:
![9](https://github.com/user-attachments/assets/5d4472ae-ef4c-4ab5-93d9-a4bfbb63d422)

The waveform for the hardcoded command present in the code is given below:
![9t](https://github.com/user-attachments/assets/77232dbd-8902-4d93-a4dc-49439c2f037d)

`BNE r0, r0, 20` 

The waveform for the above command using the provided verilog code is given below:
![10](https://github.com/user-attachments/assets/4577e6c5-4647-4fef-89ac-bce2846a4811)

The waveform for the hardcoded command present in the code is given below:
![10t](https://github.com/user-attachments/assets/7cc9514a-33ba-4f0a-a380-033e91e56ddc)

`BEQ r0, r0, 15`  

The waveform for the above command using the provided verilog code is given below:
![11](https://github.com/user-attachments/assets/e3273da3-265b-4924-a377-45de83f07c2d)


Similarly for other remaining instructions we can match our verilog instruction with hardcoded instructions waveform and we can say that it is not matching with the given instructions waveform.
</details>


 
<details>
 
<summary> <h2>Lab 4</h2> </summary>

## lab 4: project on Morse code encoder/decoder:
### morse code :
Morse code is a method of encoding text characters as sequences of dots (short signals) and dashes (long signals). Despite its origins in the 19th century, Morse code remains relevant in several fields today like Amateur Radio (Ham Radio),Maritime Communication,Military and Aviation,Education and Training,Assistive Technology etc.
###my project
Here in my program it asks user either input will be in morse code or in alphabets then it takes the input accordingly and according to predefined morse code of each letter from A to Z and digits 0 to 9 and three special characters used to facilitate more punctuations in user input(so user camn enter , . or ? sign it'll not show any error).

 ### code
 
```c
#include <stdio.h>
#include <string.h>
#include <ctype.h>  // For toupper() so that no error occur if we input in small char

// Morse code mappings
const char *morse[] = {
    ".-", "-...", "-.-.", "-..", ".", "..-.", "--.", "....", "..", ".---",  // A-J
    "-.-", ".-..", "--", "-.", "---", ".--.", "--.-", ".-.", "...", "-",   // K-T
    "..-", "...-", ".--", "-..-", "-.--", "--..",                         // U-Z
    "-----", ".----", "..---", "...--", "....-", ".....", "-....", "--...", // 0-7
    "---..", "----.",                                                   // 8-9
    "--..--", ".-.-.-", "..--.."                                        // ,  .  ?
};

const char alphabet[] = "ABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789,.?";

//this is my  Function to encode text to Morse code
void encode_to_morse(const char *text) {
    while (*text) {
        if (*text == ' ') {
            printf("   ");  // 3 spaces between words
        } else {
            char *p = strchr(alphabet, toupper(*text));
            if (p) {
                printf("%s ", morse[p - alphabet]);
            }
        }
        text++;
    }
    printf("\n");
}

// this is my Function to decode Morse code to text
void decode_from_morse(const char *morse_code) {
    char buffer[10];
    while (*morse_code) {
        int i = 0;
        while (*morse_code != ' ' && *morse_code != '\0') {
            buffer[i++] = *morse_code++;
        }
        buffer[i] = '\0';

        for (int j = 0; j < sizeof(alphabet) - 1; j++) {
            if (strcmp(buffer, morse[j]) == 0) {
                printf("%c", alphabet[j]);
                break;
            }
        }

        if (*morse_code == ' ') {
            morse_code++;  // Skip space between Morse characters
            if (*morse_code == ' ') {
                printf(" ");  // Additional space indicates a new word
                morse_code++;  // Skip the additional space
            }
        }
    }
    printf("\n");
}

int main() {
    char text[100];
    int choice;

    printf("1. Encode text to Morse code\n");
    printf("2. Decode Morse code to text\n");
    printf("Enter your choice: ");
    scanf("%d", &choice);
    getchar();  // Consume the newline character

    if (choice == 1) {
        printf("Enter text to encode: ");
        fgets(text, sizeof(text), stdin);
        text[strcspn(text, "\n")] = '\0';  // Remove the newline character
        printf("Morse code: ");
        encode_to_morse(text);
    } else if (choice == 2) {
        printf("Enter Morse code to decode (separate letters with spaces and words with triple spaces): ");
        fgets(text, sizeof(text), stdin);
        text[strcspn(text, "\n")] = '\0';
        printf("Decoded text: ");
        decode_from_morse(text);
    } else {
        printf("Invalid choice.\n");
    }

    return 0;
}

```
### code explanation:
Here in my code I am using '#include <ctype.h>' this is specially used to  include the C Standard Library header file that provides functions for character classification and conversion.
in my code i have used The  'toupper()' function which converts a lowercase character to its uppercase equivalent.
Since Morse code is case-insensitive and the alphabet[] array only contains uppercase letters, toupper() ensures that any lowercase input is converted to uppercase before processing.
If you don't include #include <ctype.h>, the compiler will not recognize the toupper() function, resulting in an error.
#### morse code mapping
```c

const char *morse[] = {
    ".-", "-...", "-.-.", "-..", ".", "..-.", "--.", "....", "..", ".---",  // A-J
    "-.-", ".-..", "--", "-.", "---", ".--.", "--.-", ".-.", "...", "-",   // K-T
    "..-", "...-", ".--", "-..-", "-.--", "--..",                         // U-Z
    "-----", ".----", "..---", "...--", "....-", ".....", "-....", "--...", // 0-7
    "---..", "----.",                                                   // 8-9
    "--..--", ".-.-.-", "..--.."                                        // ,  .  ?
};

```

So, basically it will take input  either in morse or in english then convert it into another accordingly.



### compilation in gcc
'gcc morsecode.c'
![Screenshot (56)](https://github.com/user-attachments/assets/c2479a9b-1aa2-4bb8-9fc7-509febdb91f9)
we clearly see that when we write our input in english it converts it into its respective morse then showing vice versa.
 ### compilation by using riscv gcc using -O1
 Optimization Level 1: This flag enables a set of basic optimizations that are relatively fast to perform and do not significantly increase the compilation time.
Effects:
Reduces code size and improves execution speed.
Eliminates some unnecessary code and does some basic inlining and loop optimizations.
Balances between performance and compilation time, making it a good choice for development builds.
'riscv64-unknown-elf-gcc -O1 -mabi=lp64 -march=rv64i -o morsecode.o morsecode.c'
![Screenshot (59)](https://github.com/user-attachments/assets/d869c0c5-2118-4b16-af5a-cb985781bfd2)

Compiles the morsecode.c source file: It generates an object file (morsecode.o) optimized at the -O1 level for the RISC-V 64-bit architecture.
Target ABI and Architecture: The resulting object file is intended for a system using the lp64 ABI and the rv64i architecture.
now to see the assembly code
'riscv64-unknown-elf-objdump -d morsecode.o'
![Screenshot (60)](https://github.com/user-attachments/assets/b73e074a-9ea8-4642-9a71-45bcf04be004)
![Screenshot (61)](https://github.com/user-attachments/assets/20ac0fe7-0f53-44f6-942b-45936e6cb0c3)

It is used to disassemble the object file morsecode.o for the RISC-V 64-bit architecture

-d: This option tells objdump to disassemble the executable code in the object file. Disassembling means converting the machine code (binary instructions) back into human-readable assembly code.
'riscv64-unknown-elf-objdump -d morsecode.o | less'
![image](https://github.com/user-attachments/assets/ed632ee1-cb1b-475a-8121-8a67f5ba43de)
![Screenshot (63)](https://github.com/user-attachments/assets/6b3e1653-729e-4345-a2c8-e1f38e416500)
#### to see output using spike O1
![Screenshot (72)](https://github.com/user-attachments/assets/0f3d3590-7a4b-42bc-89e5-3e360cba04a6)


The command disassembles the morsecode.o file and sends the disassembled output to less, allowing you to view it in a controlled, scrollable manner.

### compilation by using riscv gcc using -Ofast
'riscv64-unknown-elf-gcc -Ofast -mabi=lp64 -march=rv64i -o morsecode.o morsecode.c'



![Screenshot (68)](https://github.com/user-attachments/assets/3674f671-ccb6-442b-bc99-90219d7f52ee)

![Screenshot (69)](https://github.com/user-attachments/assets/bc3a2675-0a57-4f3c-9be0-cdd295aa463c)
![Screenshot (70)](https://github.com/user-attachments/assets/4ba5f587-c3d4-4124-adac-4230da034358)
#### to see output using spike Ofast

![Screenshot (71)](https://github.com/user-attachments/assets/1ad78b51-72da-4b08-b72d-802b2b4685d2)
</details>


<details>
 
<summary> <h2>Lab5</h2> </summary>


## lab5: make a Risc-V processor core using TL-Verilog 

TL-Verilog (Transaction-Level Verilog) is an extension of traditional Verilog that focuses on improving the abstraction and productivity in hardware design, especially for complex digital systems. It was developed to address some of the limitations of traditional RTL (Register-Transfer Level) design by introducing higher-level constructs and simplifying the design process.

### Key Features of TL-Verilog:
1. Pipelines: TL-Verilog introduces pipeline constructs that allow designers to easily manage and visualize pipelines in their designs. Pipelining is a common technique in digital design, but managing it in traditional RTL can be cumbersome. TL-Verilog makes it more straightforward.

2. Implicit Registers: Unlike traditional Verilog, where you explicitly define registers, TL-Verilog allows you to work with implicit registers, reducing the amount of code you need to write and making your designs cleaner.

3. Transactions: TL-Verilog emphasizes transaction-level abstractions, which means that it focuses more on data movement (transactions) rather than the low-level signal toggling. This abstraction allows for higher productivity and easier debugging.

4. Cleaner Syntax: TL-Verilog simplifies the syntax for many common operations, making the code easier to read and write. This is particularly helpful for reducing errors and speeding up the development process.

5. Scalability: TL-Verilog is designed to be scalable, meaning that it can handle large and complex designs more efficiently than traditional Verilog.

6. Integration with Traditional Verilog: TL-Verilog is built on top of traditional Verilog, so it can be integrated into existing Verilog design flows. Designers can start using TL-Verilog gradually without completely overhauling their design process.

### Use Cases:
Processor Design: TL-Verilog is particularly useful in designing complex processors, where pipelining and transaction-level abstraction can significantly reduce development time.
Digital Signal Processing (DSP): It can also be used in DSP applications where performance and efficiency are crucial.
System-on-Chip (SoC) Design: TL-Verilog's ability to handle complex and large-scale designs makes it suitable for SoC design.

boolean operators

![Screenshot (90)](https://github.com/user-attachments/assets/554ab17f-b215-4b6d-bcb5-66372222f0c6)


generated diagram:

![Screenshot (96)](https://github.com/user-attachments/assets/d03bc04f-004a-4b6e-abcf-821111fc86f1)

simulation passed:
![Screenshot (101)](https://github.com/user-attachments/assets/87d15680-ba53-4b08-b25e-634818988096)

viz:
![Screenshot (102)](https://github.com/user-attachments/assets/63c3bad8-66e5-484d-8baa-1eed117a70ed)

The signals including the "named clock : $clk_zunaid "
the waveform generated:
![Screenshot (92)](https://github.com/user-attachments/assets/936a4dbf-af49-4025-859e-7b0f4167d651)

### The final code:
```c
// ------------- Sum from 1 to 9 ------------
// This program sums the numbers 1 through 9 
// for the MYTH Workshop to validate RV32I.
// The steps involve adding 1, 2, 3,...,9.
//
// Registers:
//  x10 (a0): Input: 0, Output: Sum result
//  x12 (a2): Holds value 10
//  x13 (a3): Counter from 1 to 10
//  x14 (a4): Accumulated Sum
//

// Set x10 (a0) to 0.
m4_asm(ADD, x10, x0, x0)             

// Set x14 (a4) to 0 to start summation.
m4_asm(ADD, x14, x10, x0)            

// Initialize x12 (a2) with the value 10.
m4_asm(ADDI, x12, x10, 1010)        

// Set x13 (a3) to 0 as the starting value.
m4_asm(ADD, x13, x10, x0)           

// Loop: Add x13 (a3) to x14 (a4).
m4_asm(ADD, x14, x13, x14)           

// Increment x13 (a3) by 1 for the next iteration.
m4_asm(ADDI, x13, x13, 1)            

// Continue looping until x13 (a3) reaches x12 (a2).
m4_asm(BLT, x13, x12, 1111111111000) 

// Store the result in x10 (a0).
m4_asm(ADD, x10, x14, x0)            

// Validate Load and Store instructions.
m4_asm(SW, x0, x10, 100)             
m4_asm(LW, x15, x0, 100)             

// Optional infinite loop (uncomment to use).
// m4_asm(JAL, x7, 00000000000000000000) 

m4_define_hier(['M4_IMEM'], M4_NUM_INSTRS)

// CPU Implementation
|cpu
   @0
      $reset = *reset;
      $clk_zunaid = *clk;

   // Program Counter Logic
   @0
      $pc[31:0] = >>1$reset ? 0 
                 : >>3$branch_taken ? >>3$branch_target
                 : >>3$valid_mem_load ? >>3$next_pc
                 : >>3$jump_valid && >>3$is_jal ? >>3$branch_target
                 : >>3$jump_valid && >>3$is_jalr ? >>3$jalr_target
                 : >>1$next_pc;
      
      $start_signal = !$reset && >>1$reset;

   // Fetch and Decode Logic
   @1
      $next_pc[31:0] = $pc + 32'd4;
      $imem_rd_addr[M4_IMEM_INDEX_CNT-1:0] = $pc[M4_IMEM_INDEX_CNT+1:2];
      $imem_rd_en = !$reset;
      $instr_word[31:0] = $imem_rd_data[31:0];

      // Decode instruction types
      $i_type = $instr_word[6:2] ==? 5'b0000x || $instr_word[6:2] ==? 5'b001x0 || $instr_word[6:2] ==? 5'b11100;
      $r_type = $instr_word[6:2] ==? 5'b01011 || $instr_word[6:2] ==? 5'b01100 || $instr_word[6:2] ==? 5'b01110 || $instr_word[6:2] ==? 5'b10100;
      $b_type = $instr_word[6:2] ==? 5'b11000;
      $s_type = $instr_word[6:2] ==? 5'b0100x;
      $j_type = $instr_word[6:2] ==? 5'b11011;
      $u_type = $instr_word[6:2] ==? 5'b0x101;

      // Immediate value decoding
      $imm_value[31:0] = $i_type ? {{21{$instr_word[31]}}, $instr_word[30:20]} :
                         $s_type ? {{21{$instr_word[31]}}, $instr_word[30:25], $instr_word[11:7]} :
                         $b_type ? {{20{$instr_word[31]}}, $instr_word[7], $instr_word[30:25], $instr_word[11:8], 1'b0} :
                         $u_type ? {$instr_word[31:12], 12'b0} :
                         $j_type ? {{12{$instr_word[31]}}, $instr_word[19:12], $instr_word[20], $instr_word[30:21], 1'b0} :
                         32'b0;

      // Decode instruction components
      $opcode_val[6:0] = $instr_word[6:0];
      $rd_valid = $r_type || $j_type || $i_type || $u_type;
      $rs2_valid = $r_type || $s_type || $b_type;
      $rs1_valid = $r_type || $i_type || $b_type || $s_type;
      $funct3_valid = $r_type || $i_type || $b_type || $s_type;
      $funct7_valid = $r_type;

      // Assign register fields
      ?$rd_valid $rd[4:0] = $instr_word[11:7];
      ?$rs2_valid $rs2[4:0] = $instr_word[24:20];
      ?$rs1_valid $rs1[4:0] = $instr_word[19:15];
      ?$funct3_valid $funct3[2:0] = $instr_word[14:12];
      ?$funct7_valid $funct7[6:0] = $instr_word[31:25];

      // Instruction Decoding
      $instr_dec[10:0] = {$funct7[5], $funct3, $opcode_val};
      $is_beq = $instr_dec ==? 11'bx_000_1100011;
      $is_bne = $instr_dec ==? 11'bx_001_1100011;
      $is_blt = $instr_dec ==? 11'bx_100_1100011;
      $is_bge = $instr_dec ==? 11'bx_101_1100011;
      $is_bltu = $instr_dec ==? 11'bx_110_1100011;
      $is_bgeu = $instr_dec ==? 11'bx_111_1100011;

      $is_addi = $instr_dec ==? 11'bx_000_0010011;
      $is_add  = $instr_dec ==? 11'b0_000_0110011;
      $is_sub  = $instr_dec ==? 11'b1_000_0110011;

      $is_sltiu = $instr_dec ==? 11'bx_011_0010011;
      $is_xori = $instr_dec ==? 11'bx_100_0010011;
      $is_ori = $instr_dec ==? 11'bx_110_0010011;
      $is_andi = $instr_dec ==? 11'bx_111_0010011;
      $is_slli = $instr_dec ==? 11'b0_001_0010011;
      $is_srli = $instr_dec ==? 11'b0_101_0010011;
      $is_sral = $instr_dec ==? 11'b1_101_0010011;
      $is_sll = $instr_dec ==? 11'b0_001_0110011;
      $is_slt = $instr_dec ==? 11'b0_010_0110011;
      $is_sltu = $instr_dec ==? 11'b0_011_0110011;
      $is_xor = $instr_dec ==? 11'b0_100_0110011;
      $is_srl = $instr_dec ==? 11'b0_101_0110011;
      $is_sra = $instr_dec ==? 11'b1_101_0110011;
      $is_or = $instr_dec ==? 11'b0_110_0110011;
      $is_and = $instr_dec ==? 11'b0_111_0110011;

      $is_lui = $instr_dec ==? 11'bx_xxx_0110111;
      $is_auipc = $instr_dec ==? 11'bx_xxx_0010111;
      $is_jal = $instr_dec ==? 11'bx_xxx_1101111;
      $is_jalr = $instr_dec ==? 11'bx_000_1100111;
      $is_sb = $instr_dec ==? 11'bx_000_0100011;
      $is_sh = $instr_dec ==? 11'bx_001_0100011;
      $is_sw = $instr_dec ==? 11'bx_010_0100011;
      $is_lb = $instr_dec ==? 11'bx_000_0000011;
      $is_lh = $instr_dec ==? 11'bx_001_0000011;
      $is_lw = $instr_dec ==? 11'bx_010_0000011;
      $is_lbu = $instr_dec ==? 11'bx_100_0000011;
      $is_lhu = $instr_dec ==? 11'bx_101_0000011;

      $is_fence = $instr_dec ==? 11'bx_xxx_0001111;
      $is_ecall = $instr_dec ==? 11'bx_000_1110011;
      $is_ebreak = $instr_dec ==? 11'bx_001_1110011;
      $is_mret = $instr_dec ==? 11'bx_000_1110011;
      $is_csrrw = $instr_dec ==? 11'bx_001_1110011;
      $is_csrrs = $instr_dec ==? 11'bx_010_1110011;
      $is_csrrc = $instr_dec ==? 11'bx_011_1110011;
      $is_csrrwi = $instr_dec ==? 11'bx_101_1110011;
      $is_csrrsi = $instr_dec ==? 11'bx_110_1110011;
      $is_csrrci = $instr_dec ==? 11'bx_111_1110011;

      $branch_taken = $is_beq && $rs1_value ==? $rs2_value || $is_bne && $rs1_value !=? $rs2_value || $is_blt && $rs1_value <_signed $rs2_value || $is_bge && $rs1_value >=_signed $rs2_value || $is_bltu && $rs1_value < $rs2_value || $is_bgeu && $rs1_value >= $rs2_value;

      $branch_target = $pc + $imm_value;

   // Execute Logic
   @3
      $valid_mem_load = $is_lb || $is_lh || $is_lw || $is_lbu || $is_lhu;
      $valid_mem_store = $is_sb || $is_sh || $is_sw;
      $jump_valid = $is_jal || $is_jalr;
      $mem_addr = $rs1_value + $imm_value;
      $branch_valid = $branch_taken || $is_jal || $is_jalr;

      // ALU Operations
      $alu_result[31:0] = $is_lui || $is_auipc ? $imm_value :
                          $is_jal || $is_jalr ? $next_pc :
                          $is_addi || $is_lb || $is_lh || $is_lw || $is_lbu || $is_lhu || $is_sb || $is_sh || $is_sw ? $rs1_value + $imm_value :
                          $is_sltiu ? $rs1_value < $imm_value :
                          $is_xori ? $rs1_value ^ $imm_value :
                          $is_ori ? $rs1_value | $imm_value :
                          $is_andi ? $rs1_value & $imm_value :
                          $is_slli ? $rs1_value << $imm_value[4:0] :
                          $is_srli ? $rs1_value >> $imm_value[4:0] :
                          $is_sral ? $rs1_value >>> $imm_value[4:0] :
                          $is_add ? $rs1_value + $rs2_value :
                          $is_sub ? $rs1_value - $rs2_value :
                          $is_sll ? $rs1_value << $rs2_value[4:0] :
                          $is_slt ? $rs1_value <_signed $rs2_value :
                          $is_sltu ? $rs1_value < $rs2_value :
                          $is_xor ? $rs1_value ^ $rs2_value :
                          $is_srl ? $rs1_value >> $rs2_value[4:0] :
                          $is_sra ? $rs1_value >>> $rs2_value[4:0] :
                          $is_or ? $rs1_value | $rs2_value :
                          $is_and ? $rs1_value & $rs2_value :
                          32'b0;

      // Memory Operations
      $mem_wr_data[7:0] = $is_sb ? $rs2_value[7:0] : $is_sh ? $rs2_value[15:0] : $is_sw ? $rs2_value[31:0] : 8'b0;
      $mem_rd_en = $valid_mem_load;
      $mem_wr_en = $valid_mem_store;
      $branch_taken = $branch_valid;
      $branch_target = $branch_valid ? $pc + $imm_value : 32'b0;

   // Writeback Logic
   @4
      // Register Writeback
      $rd_wr_en = $rd_valid;
      $rd_wr_data[31:0] = $valid_mem_load ? $mem_rd_data[31:0] : $alu_result[31:0];
      $rd_wr_addr[4:0] = $rd[4:0];
      ?$rd_valid $reg_file[$rd[4:0]] <= $rd_wr_data[31:0];


```
