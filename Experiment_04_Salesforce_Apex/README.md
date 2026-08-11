# Experiment 4: Develop Simple Application using Apex Programming Language on Salesforce

## Aim
To develop a simple custom application using the Apex programming language on the Salesforce cloud platform.


## Procedure

### Step 1: Sign up for a Salesforce Developer Org
If you do not have one, sign up for a free developer account on the [Salesforce Developer Signup Page](https://developer.salesforce.com/signup).

### Step 2: Log in to your Developer Org
Log in to your Salesforce instance using your developer credentials.

### Step 3: Open the Developer Console
Click the **Gear icon (Setup)** in the top-right corner of the Salesforce Classic interface or Lightning Experience, and select **Developer Console** from the dropdown menu.

### Step 4: Create a New Apex Class
In the Developer Console, click on **File** > **New** > **Apex Class**. Enter `HelloWorldApp` as the class name and click **OK**.

### Step 5: Write the Apex Code
A default class structure is automatically generated. Add a static method to print a message to the debug log as follows:
```apex
public class HelloWorldApp {
    public static void sayHello() {
        System.debug('WELCOME TO APEX PROGRAMMING');
    }
}
```
Save the file by clicking **File** > **Save** (or pressing `Ctrl + S`).

### Step 6: Execute the Apex Code
1. In the Developer Console, click the **Debug** menu and select **Open Execute Anonymous Window**.
2. Input the following code block to invoke your static method:
```apex
HelloWorldApp.sayHello();
```
3. Check the **Open Log** checkbox and click **Execute**.

### Step 7: View the Output
The execution log will open automatically. Check the **Debug Only** checkbox in the log inspector at the bottom of the screen to filter out system logs. The message `"WELCOME TO APEX PROGRAMMING"` will be displayed in the console output.


## Results

The Apex programming class was successfully created, saved, compiled, and executed, verifying its functionality within the Salesforce Developer Environment.