# Experiment 2: Install C Compiler in Virtual Machine and Execute Simple Program

## Aim
To install a C compiler in the virtual machine and execute a simple program successfully.

## Procedure

### 1. Prepare the virtual machine
- Start the Linux virtual machine in VirtualBox.
- Open the terminal and update the package list.
- Install the GNU C Compiler if it is not already present.

```bash
sudo apt update
sudo apt install build-essential -y
```

### 2. Create the C source file
- Create a file named hello_lab.c using a text editor.

```c
#include <stdio.h>

int main(void) {
    printf("Cloud lab C program executed successfully\n");
    return 0;
}
```

### 3. Compile and run the program
- Compile the code using gcc.
- Execute the generated binary.

```bash
gcc hello_lab.c -o hello_lab
./hello_lab
```

### 4. Observe the output
The program should print the success message on the terminal.

## Results
The C compiler was installed successfully and the sample program executed correctly in the virtual machine.