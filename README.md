# asic-design-class
Lab 1_Task1: to make 
C program and compile it using gcc compiler. Verify the output of the C program after execution.

![Screenshot 2024-07-17 032110](https://github.com/user-attachments/assets/250bf18c-2089-41dd-886c-055933482989)

Lab 1_task2:

The same c program was compiled using this command with riscv compiler:

`riscv64-unknown-elf-gcc -mabi=lp64 -march=rv64i -o sum1tot.o sum1ton.c`

After that the following command was used to dump the assembly code in the terminal:

`riscv64-unknown-elf-objdump -d sum1to1.o | less`


![Screenshot 2024-07-17 092335](https://github.com/user-attachments/assets/7a071373-a764-4698-857d-eab8acf6b801)
