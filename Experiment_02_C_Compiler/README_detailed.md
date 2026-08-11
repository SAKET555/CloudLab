# Experiment 2: Install C Compiler in Virtual Machine and Execute Simple Program (Detailed Guide)

## Aim
To import a pre-configured Ubuntu Linux virtual appliance (`.ova`) into Oracle VM VirtualBox, configure device compatibility, write a C language program using the Gedit editor, compile it with the GCC compiler, and execute the compiled binary.

---

## Conceptual Background

### 1. What is an OVA File?
An `.ova` (Open Virtualization Format Archive) file is a single-file folder package that contains a virtual machine description (configuration, hardware requirements) and its virtual disks (VMDK). It allows for easy distribution and importing of pre-built environments.

### 2. The GCC Compiler Toolchain
GCC (GNU Compiler Collection) is the standard C compiler on Linux. It converts source code (`.c` files) into machine-executable code through four main stages:
1. **Preprocessing**: Resolves header files (`#include`) and macros (`#define`).
2. **Compilation**: Translates source code into assembly code.
3. **Assembly**: Translates assembly code into machine object code.
4. **Linking**: Links the object code with standard libraries to build the final executable (`a.out`).

---

## Detailed Step-by-Step Procedure

### Step 1: Import the Ubuntu VM and Configure USB Support
1. Launch **VirtualBox** and navigate to **File** > **Import Appliance**.
2. Browse to find and select the `ubuntu_gt6.ova` file on your filesystem. Click **Next**.
3. Under the Import Settings list, locate the USB controller options. If your host doesn't have the VirtualBox Extension Pack installed, default USB 2.0/3.0 controllers may fail to load. Go to VM **Settings** > **USB** and select the **USB 1.1 (OHCI) Controller** to guarantee host-to-guest hardware compatibility.
4. Save the configuration and click **Start** to boot up the virtual machine.

![Step Screenshot](images/step_image_1.png)

### Step 2: Open Terminal and Create source file
1. Once the Ubuntu desktop loads, open the command terminal (shortcut: `Ctrl + Alt + T`).
2. Navigate to the desired workspace directory:
   ```bash
   cd /opt/axis2/axis2-1.7.3/bin
   ```
3. Open the Gedit text editor to create a new file named `first.c`:
   ```bash
   gedit first.c
   ```

![Step Screenshot](images/step_image_2.png)

### Step 3: Write the C Program Source Code
In the Gedit text window, write your C source code. For example, a simple "Hello, World!" program:
```c
#include <stdio.h>

int main() {
    printf("Hello World from Ubuntu VM!\n");
    return 0;
}
```
Save the file by clicking **Save** or pressing `Ctrl + S`, and then close the editor.

![Step Screenshot](images/step_image_3.png)

### Step 4: Compile the Source Code
Compile the program using the GNU Compiler Collection (GCC) toolchain by running the following command:
```bash
gcc first.c
```
If there are no syntax errors, GCC will compile the code and produce a default executable output binary named `a.out` in the same directory.

![Step Screenshot](images/step_image_4.png)

### Step 5: Execute the Program and Observe Output
Run the compiled binary executable from the terminal:
```bash
./a.out
```
The terminal will display the stdout output of the compiled program.

![Step Screenshot](images/step_image_5.png)

---

## Troubleshooting Tips
- **Gedit command not found**: If gedit is missing, install it via `sudo apt-get install gedit` or use another editor like `nano` or `vi`.
- **GCC compiler missing**: Install the essential build tools using:
  ```bash
  sudo apt update
  sudo apt install build-essential
  ```
- **Permission Denied for `./a.out`**: Ensure the executable flag is set using:
  ```bash
  chmod +x a.out
  ```

## Results
The pre-configured Ubuntu virtual machine was successfully imported. The GCC compilation toolchain was used to compile a custom C program source file, and the compiled executable output was verified on the command line interface.
