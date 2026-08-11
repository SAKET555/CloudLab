# Experiment 2: Install C Compiler in Virtual Machine and Execute Simple Program

## Aim
To install a C compiler (GCC) within an Ubuntu virtual machine hosted on VirtualBox and execute a simple C program.


## Procedure

### Import the Ubuntu Virtual Appliance (.ova)

- Open VirtualBox and navigate to **File** > **Import Appliance**.
- Browse and select the `ubuntu_gt6.ova` virtual appliance file.
- Go to VM **Settings** > **USB** and choose the **USB 1.1 (OHCI) Controller** (to prevent USB controller boot conflicts).
- Save changes and click **Start** to run the `ubuntu_gt6` virtual machine.

![Step Screenshot](images/step_image_1.png)


### Write and Run the C Program

- Open a terminal within the Ubuntu virtual machine.
- Navigate to the working directory: `cd /opt/axis2/axis2-1.7.3/bin`
- Create and open a new file named `first.c` in the gedit text editor:
```bash
gedit first.c
```

![Step Screenshot](images/step_image_2.png)

- Write the simple C program (e.g., Hello World) in the text editor and save the file.

![Step Screenshot](images/step_image_3.png)

- Compile the C program using the GCC compiler by running: `gcc first.c`

![Step Screenshot](images/step_image_4.png)

- Run the compiled binary output (`./a.out`) to display the program's output on the terminal:

![Step Screenshot](images/step_image_5.png)


## Results

The installation of the C compiler within the Ubuntu virtual machine and execution of a simple C program were successfully completed and verified.