# Experiment 5: Implement a Mailing Service using Apex Programming Language on Salesforce

## Aim
To implement and execute a custom mailing service class using the Apex programming language in the Salesforce Developer Console.


## Procedure

### Step 1: Access the Developer Console
Log in to your Salesforce Developer account, click the **Gear icon (Setup)** in the top-right corner, and select **Developer Console**.

### Step 2: Create the Apex Class
1. In the Developer Console, click on **File** > **New** > **Apex Class**.
2. Name the class `EmailManager` and click **OK**.

### Step 3: Implement the EmailManager Code
Replace the generated class body with the following code, which sets up a single email message and a helper method to verify if the email was sent successfully:

```apex
public class EmailManager {
    // Public method to send a mail message
    public void sendMail(String address, String subject, String body) {
        // Create an email message object
        Messaging.SingleEmailMessage mail = new Messaging.SingleEmailMessage();
        String[] toAddresses = new String[] {address};
        mail.setToAddresses(toAddresses);
        mail.setSubject(subject);
        mail.setPlainTextBody(body);
        
        // Pass this email message to the built-in sendEmail method of the Messaging class
        Messaging.SendEmailResult[] results = Messaging.sendEmail(
                                 new Messaging.SingleEmailMessage[] { mail });
                                 
        // Call a helper method to inspect the returned results
        inspectResults(results);
    }

    // Helper method to verify the email execution status
    private static Boolean inspectResults(Messaging.SendEmailResult[] results) {
        Boolean sendResult = true;
        // Iterate through the list to inspect results
        for (Messaging.SendEmailResult res : results) {
            if (res.isSuccess()) {
                System.debug('Email sent successfully');
            }
            else {
                sendResult = false;
                System.debug('The following errors occurred: ' + res.getErrors());
            }
        }
        return sendResult;
    }
}
```

### Step 4: Save the Class
Save the class by selecting **File** > **Save** or pressing `Ctrl + S`. Ensure there are no compilation errors listed in the **Problems** tab.

### Step 5: Execute the Code and Verify Output
1. In the Developer Console, navigate to **Debug** > **Open Execute Anonymous Window** (or press `Ctrl + E`).
2. Input the following code to instantiate the `EmailManager` class and trigger the email method (replace `'Your email address'` with your actual email address):
```apex
EmailManager em = new EmailManager();
em.sendMail('Your email address', 'Email Subject', 'Email Body');
```
3. Check the **Open Log** checkbox and click **Execute**.
4. Check the **Debug Only** checkbox in the log inspector at the bottom to view the execution outcome.

*Alternative (Static Method approach):*
If you want to call the method directly without using `new`, define the method with the `static` keyword:
```apex
public static void sendMail(String address, String subject, String body) { ... }
```
Then run the method statically:
```apex
EmailManager.sendMail('Your email address', 'Email Subject', 'Email Body');
```


## Results

The Apex mailing service class was successfully implemented, compiled, and executed, verifying email transmission functionality within the Salesforce environment.
