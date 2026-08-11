# Experiment 5 (Detailed Guide): Implement an Outbound Email Service in Salesforce using Apex

## 1. Experiment Overview & Objectives
This detailed guide covers the configuration and deployment of an outbound transactional email service in a Salesforce environment. The goal is to build an Apex class that programmatically compiles, configures, sends, and validates outbound emails using the native Salesforce `Messaging` architecture.

### Objectives:
- Master the `Messaging.SingleEmailMessage` and `Messaging.sendEmail` API patterns.
- Write robust, deployable Apex classes and matching testing code.
- Deploy code using Salesforce Developer Console browser-based controls and VS Code / Salesforce CLI tools.
- Configure organization-wide deliverability controls to enable outbound transmissions.

---

## 2. Prerequisites
1. **Salesforce Developer Edition Org**: A free developer environment (sign up at [developer.salesforce.com](https://developer.salesforce.com/signup)).
2. **Access Permissions**: System Administrator profile permissions or standard credentials to open the Developer Console and run Apex code.
3. **Outbound Deliverability Settings**:
   - Outbound email transmission is blocked by default in sandboxes and new developer orgs.
   - Go to **Setup** > search for **Deliverability** > set **Access level** to **All email** > click **Save**.
4. **Developer Workspace (Optional for CLI)**: 
   - Salesforce CLI (`sf` tool) installed.
   - Visual Studio Code with the *Salesforce Extension Pack* extension bundle.

---

## 3. Complete Implementation Code

### File: `EmailService.cls`
```apex
public class EmailService {
    /**
     * Sends a single outbound email.
     * @param toAddress Target email recipient address.
     * @param subject Email subject line.
     * @param body Plain text email body.
     * @return Boolean indicating success status of the email transmission.
     */
    public static Boolean sendMail(String toAddress, String subject, String body) {
        // Create a single email message object
        Messaging.SingleEmailMessage mail = new Messaging.SingleEmailMessage();
        
        // Define recipient addresses (expects an array)
        String[] toAddresses = new String[] {toAddress};
        mail.setToAddresses(toAddresses);
        
        // Configure subject and text content
        mail.setSubject(subject);
        mail.setPlainTextBody(body);
        
        // Send email message using Messaging system utility
        Messaging.SendEmailResult[] results = Messaging.sendEmail(
            new Messaging.SingleEmailMessage[] { mail }
        );
        
        // Process results using a helper method
        return inspectResults(results);
    }
    
    /**
     * Inspects outbound email results and logs details.
     */
    private static Boolean inspectResults(Messaging.SendEmailResult[] results) {
        Boolean sendResult = true;
        for (Messaging.SendEmailResult res : results) {
            if (res.isSuccess()) {
                System.debug('Email sent successfully');
            } else {
                sendResult = false;
                for (Messaging.SendEmailError err : res.getErrors()) {
                    System.debug('Error occurred: ' + err.getStatusCode() + ' - ' + err.getMessage());
                }
            }
        }
        return sendResult;
    }
}
```

### File: `EmailService.cls-meta.xml`
```xml
<?xml version="1.0" encoding="UTF-8"?>
<ApexClass xmlns="http://soap.sforce.com/2006/04/metadata">
    <apiVersion>60.0</apiVersion>
    <status>Active</status>
</ApexClass>
```

### File: `EmailServiceTest.cls`
```apex
@isTest
public class EmailServiceTest {
    @isTest
    static void testSendMailSuccess() {
        // Test data preparation
        String toAddress = 'test@example.com';
        String subject = 'Test Subject';
        String body = 'Test Body';
        
        // Execute the method within startTest/stopTest block
        Test.startTest();
        Boolean result = EmailService.sendMail(toAddress, subject, body);
        Test.stopTest();
        
        // Assert email sending outcome
        // Note: In standard unit tests, Salesforce mocks successful email sends
        System.assertEquals(true, result, 'Email send transaction should succeed in testing context.');
    }
    
    @isTest
    static void testSendMailInvalidAddress() {
        // Test invalid data
        String toAddress = ''; // Invalid blank email address
        String subject = 'Test Subject';
        String body = 'Test Body';
        
        Test.startTest();
        try {
            Boolean result = EmailService.sendMail(toAddress, subject, body);
            System.assertEquals(false, result, 'Email transaction should fail with blank address.');
        } catch (Exception ex) {
            // Verify that a system exception is thrown for invalid parameters
            System.assertNotEquals(null, ex.getMessage(), 'Exception expected for missing recipient.');
        }
        Test.stopTest();
    }
}
```

### File: `EmailServiceTest.cls-meta.xml`
```xml
<?xml version="1.0" encoding="UTF-8"?>
<ApexClass xmlns="http://soap.sforce.com/2006/04/metadata">
    <apiVersion>60.0</apiVersion>
    <status>Active</status>
</ApexClass>
```

### File: `send_email.apex` (Anonymous Script)
```apex
// Script to verify outbound email transmission
String recipient = 'your_test_email@example.com'; // Replace with a valid test email address
String subject = 'Salesforce Outbound Email Test';
String body = 'Hello! This email was sent automatically from Salesforce using Apex Code.';

Boolean isSent = EmailService.sendMail(recipient, subject, body);
System.debug('Email service outcome status: ' + isSent);
```

---

## 4. Step-by-Step Execution Guide

### Method A: Salesforce Web Browser & Developer Console
1. **Open Console**: Log in to Salesforce setup, click the **Gear icon (Setup)** in the top-right corner, and select **Developer Console**.
2. **Create Classes**:
   - Go to **File** > **New** > **Apex Class**. Name it `EmailService`. Paste the `EmailService.cls` code and save (`Ctrl + S`).
   - Go to **File** > **New** > **Apex Class**. Name it `EmailServiceTest`. Paste the `EmailServiceTest.cls` code and save (`Ctrl + S`).
3. **Run Anonymous Code**:
   - Navigate to **Debug** > **Open Execute Anonymous Window** (`Ctrl + E`).
   - Paste the code from `send_email.apex` (inserting a real email recipient address).
   - Click the **Execute** button.
4. **Run Unit Tests**:
   - In the Developer Console, select **Test** > **New Run**.
   - Under class options, select `EmailServiceTest`, choose all methods, and click **Run**.
   - Check the **Tests** tab at the bottom to verify code execution results.

### Method B: VS Code & Salesforce CLI
1. **Project Setup**: Open a Salesforce DX project folder inside VS Code.
2. **Create Metadata Files**:
   - Place `EmailService.cls` and `EmailService.cls-meta.xml` under `/force-app/main/default/classes/`.
   - Place `EmailServiceTest.cls` and `EmailServiceTest.cls-meta.xml` in the same directory.
3. **Deploy to Org**:
   - Open the VS Code terminal and deploy your code to your active scratch org or sandbox:
     ```bash
     sf project deploy start
     ```
4. **Execute Verification script**:
   - Save your anonymous snippet as `send_email.apex` in your workspace.
   - Run the script via CLI:
     ```bash
     sf apex run --file send_email.apex
     ```
5. **Run Tests**:
   - Trigger the unit tests and inspect code coverage results:
     ```bash
     sf apex run test --class-names EmailServiceTest --detailed-results
     ```

---

## 5. Verification & Expected Output

### Debug Log Outputs
After running the script, the Developer Console log inspector should display logs containing:
```text
USER_DEBUG|[29]|DEBUG|Email sent successfully
USER_DEBUG|[6]|DEBUG|Email service outcome status: true
```

### Inbox Results
If deliverability settings are correct, you will receive an email in the recipient inbox with:
- **Sender**: Your Salesforce user account name and email.
- **Subject**: `Salesforce Outbound Email Test`
- **Body**: `Hello! This email was sent automatically from Salesforce using Apex Code.`

---

## 6. Troubleshooting & Common Errors

| Issue / Error Code | Root Cause | Solution |
|---|---|---|
| `NO_MASS_MAIL_PERMISSION` | Deliverability settings in Salesforce are set to "No access" or "System email only". | Go to **Setup** > **Deliverability**, update the Access Level dropdown to **All email**, and save. |
| `INVALID_EMAIL_ADDRESS` | Recipient address format is incorrect, empty, or unresolvable. | Double-check that your recipient string has a valid email syntax (e.g. `user@domain.com`). |
| `EMAIL_LIMIT_EXceeded` | The organization has exceeded the daily outbound email limit (Developer Orgs are limited to 15 single emails daily). | Wait 24 hours for the limit counter to reset, or use mock testing variables to avoid production exhaustion. |
| `'sf' is not recognized...` | The Salesforce CLI executable path is not added to your system's PATH environment variables. | Restart VS Code, verify the installation, or manually add the install path (e.g. `C:\Program Files\sf\bin`) to the Environment Variables. |
