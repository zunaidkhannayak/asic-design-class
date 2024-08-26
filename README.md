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
### Risc-v architecture

![Screenshot (104)](https://github.com/user-attachments/assets/2f5ce72f-c846-4505-bfd4-904f5efa94e4)


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

\m4_TLV_version 1d: tl-x.org
\SV
   // This code can be found in: https://github.com/stevehoover/RISC-V_MYTH_Workshop
   
   m4_include_lib(['https://raw.githubusercontent.com/BalaDhinesh/RISC-V_MYTH_Workshop/master/tlv_lib/risc-v_shell_lib.tlv'])

\SV
   m4_makerchip_module   // (Expanded in Nav-TLV pane.)
\TLV

   // /====================\
   // | Sum 1 to 9 Program |
   // \====================/
   //
   // Program for MYTH Workshop to test RV32I
   // Add 1,2,3,...,9 (in that order).
   //
   // Regs:
   //  r10 (a0): In: 0, Out: final sum
   //  r12 (a2): 10
   //  r13 (a3): 1..10
   //  r14 (a4): Sum
   // 
   // External to function:
   m4_asm(ADD, r10, r0, r0)             // Initialize r10 (a0) to 0.
   // Function:
   m4_asm(ADD, r14, r10, r0)            // Initialize sum register a4 with 0x0
   m4_asm(ADDI, r12, r10, 1010)         // Store count of 10 in register a2.
   m4_asm(ADD, r13, r10, r0)            // Initialize intermediate sum register a3 with 0
   // Loop:
   m4_asm(ADD, r14, r13, r14)           // Incremental addition
   m4_asm(ADDI, r13, r13, 1)            // Increment intermediate register by 1
   m4_asm(BLT, r13, r12, 1111111111000) // If a3 is less than a2, branch to label named <loop>
   m4_asm(ADD, r10, r14, r0)            // Store final result to register a0 so that it can be read by main program
   
   m4_asm(SW, r0, r10, 100)             //Command to check for Load instruction
   m4_asm(LW, r15, r0, 100)             // Command to check for the Store Instruction
   
   
   // Optional:
   // m4_asm(JAL, r7, 00000000000000000000) // Done. Jump to itself (infinite loop). (Up to 20-bit signed immediate plus implicit 0 bit (unlike JALR) provides byte address; last immediate bit should also be 0)
   m4_define_hier(['M4_IMEM'], M4_NUM_INSTRS)

   |cpu
      @0
         $reset = *reset;
         $clk_zunaid = *clk;



     
      @0
         $pc[31:0] = >>1$reset ? 0 
                    : >>3$valid_taken_br ? >>3$br_target_pc
                    : >>3$valid_load ? >>3$pc_inc
                    : >>3$valid_jump && >>3$is_jal ? >>3$br_target_pc
                    : >>3$valid_jump && >>3$is_jalr ? >>3$jalr_tgt_pc
                    : >>1$pc_inc;
         
         $start = !$reset && >>1$reset;
     //Program Counter (PC): Determines the next instruction to fetch based on the current state and instructions.

         
      @1
         $pc_inc[31:0] = $pc + 32'd4;
         //Fetch logic
         //Performs arithmetic and logical operations based on the instruction type (e.g., addition, subtraction).
         $imem_rd_addr[M4_IMEM_INDEX_CNT -1 : 0] = $pc[M4_IMEM_INDEX_CNT +1 : 2];
         $imem_rd_en = !$reset;
         $instr[31:0] = $imem_rd_data[31:0];
         
         // Instruction type identify
         $is_i_instr = $instr[6:2] ==? 5'b0000x ||
                       $instr[6:2] ==? 5'b001x0 ||
                       $instr[6:2] ==? 5'b11100 ;
//Identifies the type of instruction (e.g., I-type, R-type) and extracts immediate values, register addresses, and function codes.
         $is_r_instr = $instr[6:2] ==? 5'b01011 ||
                       $instr[6:2] ==? 5'b01100 ||
                       $instr[6:2] ==? 5'b01110 ||
                       $instr[6:2] ==? 5'b10100 ;
                       
         $is_b_instr = $instr[6:2] ==? 5'b11000;
         
         $is_s_instr = $instr[6:2] ==? 5'b0100x;
         
         $is_j_instr = $instr[6:2] ==? 5'b11011;
         
         $is_u_instr = $instr[6:2] ==? 5'b0x101;
         
         //decode logic for immediate values
         
         $imm[31:0] = $is_i_instr ? { {21{$instr[31]}}, $instr[30:20]}:
                      $is_s_instr ? { {21{$instr[31]}}, $instr[30:25], $instr[11:7]} :
                      $is_b_instr ? { {20{$instr[31]}}, $instr[7], $instr[30:25], $instr[11:8], 1'b0} :
                      $is_u_instr ? {$instr[31:12], 12'b0} :
                      $is_j_instr ? { {12{$instr[31]}}, $instr[19:12], $instr[20], $instr[30:21], 1'b0} :
                      32'b0;         
                
         //decoding other instruction elements
         
         $opcode[6:0] = $instr[6:0] ;
         
         $rd_valid = $is_r_instr || $is_j_instr || $is_i_instr || $is_u_instr;
         $rs2_valid = $is_r_instr || $is_s_instr || $is_b_instr;
         $rs1_valid = $is_r_instr || $is_i_instr || $is_b_instr || $is_s_instr;
         $funct3_valid = $is_r_instr || $is_i_instr || $is_b_instr || $is_s_instr;
         $funct7_valid = $is_r_instr;
         
         ?$rd_valid
            $rd[4:0] = $instr[11:7];
         
         ?$rs2_valid
            $rs2[4:0] = $instr[24:20];
         ?$rs1_valid
            $rs1[4:0] = $instr[19:15];
         ?$funct3_valid
            $funct3[2:0] = $instr[14:12];
         ?$funct7_valid
            $funct7[6:0] = $instr[31:25];
            
         //decoding instructions
         
         $dec_bits[10:0] = {$funct7[5],$funct3,$opcode};
         //Branch Instructions 
         //BEQ - Branch on equal 
         $is_beq = $dec_bits ==? 11'bx_000_1100011;
         //BNE - Branch on not equal
         $is_bne = $dec_bits ==? 11'bx_001_1100011;
         //BLT - Branch on less than
         $is_blt = $dec_bits ==? 11'bx_100_1100011;
         //BGE - Branch on greater than
         $is_bge = $dec_bits ==? 11'bx_101_1100011;
         //BLTU - Branch on less than equal
         $is_bltu = $dec_bits ==? 11'bx_110_1100011;
         //BGEU - Branch on greater than equal
         $is_bgeu = $dec_bits ==? 11'bx_111_1100011;
         
         //ADD Instructions 
         $is_addi = $dec_bits ==? 11'bx_000_0010011;
         $is_add  = $dec_bits ==? 11'b0_000_0110011;
         
         //Subtract Instructions
         $is_sltiu  = $dec_bits ==? 11'bx_011_0010011;
         $is_xori   = $dec_bits ==? 11'bx_100_0010011;
         $is_ori    = $dec_bits ==? 11'bx_110_0010011;
         $is_andi   = $dec_bits ==? 11'bx_111_0010011;
         $is_slli   = $dec_bits ==? 11'b0_001_0010011;
         $is_srli   = $dec_bits ==? 11'b0_101_0010011;
         $is_sral   = $dec_bits ==? 11'b1_101_0010011;
         $is_sub    = $dec_bits ==? 11'b1_000_0110011;
         $is_sll    = $dec_bits ==? 11'b0_001_0110011;
         $is_slt    = $dec_bits ==? 11'b0_010_0110011;
         $is_sltu   = $dec_bits ==? 11'b0_011_0110011;
         $is_xor    = $dec_bits ==? 11'b0_100_0110011;
         $is_srl    = $dec_bits ==? 11'b0_101_0110011;
         $is_sra    = $dec_bits ==? 11'b1_101_0110011;
         $is_or     = $dec_bits ==? 11'b0_110_0110011;
         $is_and    = $dec_bits ==? 11'b0_111_0110011;
         
         //Miscellaneous Instructions 
         $is_lui    = $dec_bits ==? 11'bx_xxx_0110111;
         $is_auipc  = $dec_bits ==? 11'bx_xxx_0010111;
         $is_jal    = $dec_bits ==? 11'bx_xxx_1101111;
         $is_jalr   = $dec_bits ==? 11'bx_000_1100111;
         $is_sb     = $dec_bits ==? 11'bx_000_0100011;
         $is_sh     = $dec_bits ==? 11'bx_001_0100011;
         $is_sw     = $dec_bits ==? 11'bx_010_0100011;
         $is_slti   = $dec_bits ==? 11'bx_010_0010011;
         
         
         //LOAD INSTRUCTION - As in ISA for Risc-V 
         $is_load   = $dec_bits ==? 11'bx_010_0000011;
         
         //assigning read index values into the register file
         
      @2
         
         
         $rf_rd_en1 = $rs1_valid;
         $rf_rd_index1[4:0] = $rs1;
         
         $rf_rd_en2 = $rs2_valid;
         $rf_rd_index2[4:0] = $rs2;
         
         //operating on the read values
         
         $src1_value[31:0] = (>>1$rf_wr_index == $rf_rd_index1) && >>1$rf_wr_en
                             ? >>1$result :
                             $rf_rd_data1;
          
         $src2_value[31:0] = (>>1$rf_wr_index == $rf_rd_index2) && >>1$rf_wr_en
                             ? >>1$result :
                             $rf_rd_data2;
         
         $taken_br = $is_beq ? ($src1_value == $src2_value) :
                     $is_bne ?($src1_value != $src2_value) :
                     $is_bltu ? ($src1_value <  $src2_value) :
                     $is_bgeu ? ($src1_value >= $src2_value) :
                     $is_blt ? (($src1_value < $src2_value) ^ ($src1_value[31] != $src2_value[31])) :
                     $is_bgeu ? (($src1_value >= $src2_value) ^ ($src1_value[31] != $src2_value[31])) :
                            1'b0;
         
         
         $br_target_pc[31:0] = $taken_br? $pc + $imm : 0;
         
         
         
      @3
         
         
         // scripting the only operations performed in the above programs 
         $result[31:0] = $is_add ?
                         $src1_value[31:0] + $src2_value[31:0] :
                         $is_sub ?
                         $src1_value[31:0] - $src2_value[31:0] :
                         $is_and ?
                         $src1_value[31:0] & $src2_value[31:0] :
                         $is_or ?
                         $src1_value[31:0] | $src2_value[31:0] :
                         $is_xor ?
                         $src1_value[31:0] ^ $src2_value[31:0] :
                         $is_addi ? 
                         $src1_value[31:0] + $imm[31:0] :
                         $is_andi ?
                         $src1_value[31:0] & $imm[31:0] :
                         $is_ori ?
                         $src1_value[31:0] | $imm[31:0] :
                         $is_xori ?
                         $src1_value[31:0] ^ $imm[31:0] :
                         //LOAD AND STORE COMPUTATION
                         $is_load ?
                         $src1_value[31:0] + $imm[31:0] :
                         $is_s_instr ?
                         $src1_value[31:0] + $imm[31:0] :
                         //ALU FOR MISCELLANEOUS OPERATIONS SHIFT OPERATIONS
                         $is_slli ?
                         $src1_value[31:0] << $imm[5:0] :
                         $is_srli ?
                         $src1_value[31:0] >> $imm[5:0] :
                         $is_sll ?
                         $src1_value[31:0] << $src2_value[4:0] :
                         $is_srl ?
                         $src1_value[31:0] >> $src2_value[4:0] :
                         //ALU FOR MISCELLANEOUS OPERATIONS
                         $is_sltu ? $sltu_rslt :
                         $is_sltiu ? $sltiu_rslt :
                         $is_lui ?
                         {$imm[31:12], 12'b0} :
                         $is_auipc ?
                         $pc + $imm :
                         $is_jal ?
                         $pc + 32'd4 :
                         $is_jalr ?
                         $pc + 32'd4 :
                         $is_srai ?
                         { {32{$src1_value[31]}}, $src1_value} >> $imm[4:0] :
                         $is_slt ?
                         ($src1_value[31] == $src2_value[31]) ? $sltu_rslt : {31'b0, $src1_value[31]} :
                         $is_slti ?
                         ($src1_value[31] == $imm[31]) ? $sltu_rslt : {31'b0, $src1_value[31]} :
                         $is_sra ?
                         { {32{$src1_value[31]}}, $src1_value} >> $src2_value[4:0] :
                         32'bx;
         
         $sltu_rslt[31:0]  = $src1_value[31:0] < $src2_value[31:0];
         $sltiu_rslt[31:0] = $src1_value[31:0] < $imm;
         
         //writing the result of alu into the register file
         $rf_wr_en = ($rd_valid && $rd!=0 && $valid) || >>2$valid_load ;  //writing only when rd is valid and rd is not equal to x0 register
         $rf_wr_index[4:0] = >>2$valid_load ? >>2$rd : $rd;
         
         $rf_wr_data[31:0] = >>2$valid_load ? >>2$ld_data[31:0] : $result;
         
         //checking for branch conditions
         
         
         
         $valid = !((>>1$valid_taken_br) || (>>2$valid_taken_br) || (>>1$valid_load) || (>>2$valid_load) || (>>1$valid_jump) || (>>2$valid_jump));
         
         //checking for branch instructions
         $valid_taken_br = $valid && $taken_br;
         
         //checking for load instructions
         $valid_load = $valid && $is_load;
         
         //checking for jump instructions
         $is_jump = $is_jal || $is_jalr;
         $valid_jump = $valid && $is_jump;
         
         $jalr_tgt_pc = $src1_value + $imm;
         
      @4
         //Data memory interface
//Manages data memory read and write operations for load and store instructions.
         $dmem_rd_en = $is_load;
         $dmem_wr_en = $is_s_instr && $valid;
         
         $dmem_addr[3:0] = $result[5:2];
         $dmem_wr_data[31:0] = $src2_value;
           
      @5
         $ld_data[31:0] = $dmem_rd_data;
        
         
         *passed = |cpu/xreg[15]>>5$value == 45;
     
Verifies if the result of the computation matches the expected outcome (sum of numbers from 1 to 9).
   
  
   
   *failed = 1'b0;
   
   // Macro instantiations for:
   //  o instruction memory
   //  o register file
   //  o data memory
   //  o CPU visualization
   |cpu
      m4+imem(@1)    // Args: (read stage)
      m4+rf(@2, @3)  // Args: (read stage, write stage) - if equal, no register bypass is required
      m4+dmem(@4)    // Args: (read/write stage)

   m4+cpu_viz(@4)   
\SV
   endmodule
```
### The waveform for the /xreg[14] where the sum of this program is store:
![Screenshot (103)](https://github.com/user-attachments/assets/4809a79c-eb21-46f4-b02f-596242c3cdba)
### summary:
This code sets up a simulation for a RISC-V processor with a specific program that computes the sum of integers from 1 to 9. The assembly code initializes the registers, performs a looped addition, and stores the final result. The simulation logic models how the processor would fetch, decode, and execute instructions while handling memory operations and validating the result.

</details>

 <details>
 
<summary> <h2>Lab6</h2> </summary>

### lab6: To convert the TLV to verilog using Sandpiper and then use GTKWave  pre-synthesis simulation to verify the design.
#### Purpose of modelling :
System models are specifically developed to support analysis, specification, design, verification and validation of a system, as well as to communicate certain information
#### What are we modelling? (VSDBabySoC)
1> Some initial input signals will be fed into vsdbabysoc module.
2> PLL will start generating the proper CLK for the circuit.
3> Clock signal CLK will make the rvmyth to execute instructions and some values are generated, these values are used by DAC core to provide the final output signal named OUT
There are 3 main elements (IP cores) and a wrapper as SoC and also a testbench module.

RVMYTH is designed and created by the TL-Verilog language. So we need a way for compile and transform it to the Verilog language and use the result in our SoC. Here the sandpiper-saas could help us do the job.
#### procedure :

1. Install These Required Packages:
   
  ```c
   
 $ sudo apt install make python python3 python3-pip git iverilog gtkwave docker.io
 $ sudo chmod 666 /var/run/docker.sock
 $ cd ~
 $ pip3 install pyyaml click sandpiper-saas
 
 ```

2. ` git clone https://github.com/manili/VSDBabySoC.git ` - clone this repo containing VSDBabySoC design files and testbench.

3. `cd /home/subhasis/VSDBabySoC`
Replace the rvmyth.tlv file in the VSDBabySoC Directory: replace in src/module with the rvmth.tlv.
![Screenshot (113)](https://github.com/user-attachments/assets/5a869dfa-c56c-47dc-bc6b-f82c8a4da9ce)

#### Convert .tlv to .v using converter:
`sandpiper-saas -i ./src/module/*.tlv -o rvmyth.v --bestsv --noline -p verilog --outdir ./src/module/`
Make the pre_synth_sim.vcd: We will create the pre_synth_sim.vcd by running the following command
![Screenshot (115)](https://github.com/user-attachments/assets/3d7b2473-d185-481b-b929-7c7c714749ec)

`make pre_synth_sim`
#### Now to compile and simulate RISC-V design run the following code: To compile and simulate vsdbabysoc design.
`iverilog -o output/pre_synth_sim.out -DPRE_SYNTH_SIM src/module/testbench.v -I src/include -I src/module`
`cd output`
`./pre_synth_sim.out` To generate pre_synth_sim.vcd file,which is our simulation waveform file.
`gtkwave pre_synth_sim.out `- to open simulation waveform in gtkwave tool
 #### The following diagram contains:-
`clk_zunaid`: This is the clock input to the RISC-V core.

reset: This is the input reset signal to the RISC-V core.
![Screenshot (117)](https://github.com/user-attachments/assets/89b4a573-3062-49a2-a5d6-25171e91bbf1)
![Screenshot (120)](https://github.com/user-attachments/assets/333f1527-ceed-47f0-8117-6c91d222e092)



`OUT[9:0]:` This is the 10-bit output [9:0] OUT port of the RISC-V core. 
This port comes from the RISC-V register #14.
we can see the output waveform through GTKwave output 002D which is final output of our program. 
![Screenshot (120)](https://github.com/user-attachments/assets/ecf204c5-1020-4da9-b595-8dc9f7cb2b32)

