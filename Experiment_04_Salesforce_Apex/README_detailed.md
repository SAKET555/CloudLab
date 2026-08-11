# Experiment 4: Develop Simple Application using Apex on Salesforce (Detailed Guide)

## Aim
To set up a Salesforce Developer Environment, create a custom class using the Apex programming language, and run it using the Developer Console's anonymous execution tool.

---

## Conceptual Background

### 1. What is Salesforce and Force.com?
Salesforce is a cloud-based Customer Relationship Management (CRM) platform. Underneath it is **Force.com**, a Platform-as-a-Service (PaaS) framework that allows developers to build custom applications using proprietary languages (Apex and Visualforce/Lightning Web Components).

### 2. The Apex Programming Language
Apex is a strongly typed, object-oriented programming language that executes on the Force.com multitenant platform. It features:
- **Java/C# like Syntax**: Includes classes, methods, variables, interfaces, and standard control structures.
- **Database Integration**: Direct support for database manipulation (DML commands like `insert`, `update`, `delete`) and queries (SOQL - Salesforce Object Query Language).
- **Execution in the Cloud**: Unlike traditional languages, Apex code is compiled and stored in Salesforce cloud metadata and runs entirely on Salesforce servers.

### 3. Developer Console and Anonymous Blocks
The Developer Console is an integrated developer environment (IDE) for Salesforce. The **Execute Anonymous Window** allows you to run fragments of Apex code on the fly. It is extremely useful for running one-off scripts, testing logic, or debugging classes without creating permanent triggers or buttons.

---

## Detailed Step-by-Step Procedure

### Step 1: Sign up for a Salesforce Developer Org
1. Visit the [Salesforce Developer Signup Page](https://developer.salesforce.com/signup).
2. Fill out the registration form. A developer account is free and comes with standard Salesforce configuration objects and sample data.
3. Check your email for login credentials and click the link to activate your account.

### Step 2: Log in to your Developer Org
Go to [login.salesforce.com](https://login.salesforce.com) and enter your username and password.

### Step 3: Launch the Developer Console
In the top-right corner of the setup screen, click the **Gear icon (Setup)** and select **Developer Console**. This will launch the console in a standalone window.

### Step 4: Create a New Apex Class
1. In the Developer Console menu bar, select **File** > **New** > **Apex Class**.
2. Type `HelloWorldApp` in the text field and click **OK**.
3. The IDE will generate a template with `public class HelloWorldApp {}`.

### Step 5: Implement the Apex Method
1. Modify the class body by adding a public static method `sayHello()` that outputs a string message:
```apex
public class HelloWorldApp {
    public static void sayHello() {
        System.debug('WELCOME TO APEX PROGRAMMING');
    }
}
```
2. Click **File** > **Save** (or press `Ctrl + S`). Salesforce compiles the class upon saving; if there are syntax errors, they will appear in the **Problems** tab at the bottom.

### Step 6: Run Code Anonymously
1. Select **Debug** > **Open Execute Anonymous Window** (or press `Ctrl + E`).
2. Delete any existing code in the text editor and input the static call:
```apex
HelloWorldApp.sayHello();
```
3. Ensure the **Open Log** checkbox is checked. This tells the console to open the debug log automatically when execution finishes.
4. Click **Execute**.

### Step 7: Analyze debug logs
1. The execution log window will pop up showing the chronological system execution events.
2. At the bottom of the log viewer, check the **Debug Only** checkbox. This filters the system events to display only user-defined debug statements.
3. You will see the timestamped output:
   ```text
   |DEBUG|WELCOME TO APEX PROGRAMMING
   ```

---

## Results
A Salesforce developer instance was configured. A custom Apex class `HelloWorldApp` was created, saved to the cloud, compiled, and executed. The output log verified that the execution completed successfully.
