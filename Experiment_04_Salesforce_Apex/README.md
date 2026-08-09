# Experiment 4: Develop Simple Application using Apex Programming Language on Salesforce

## Aim
To create and execute a simple Apex class in a Salesforce developer org.

## Procedure

### 1. Open the developer console
- Sign in to Salesforce and open the Developer Console.
- Create a new Apex class.

### 2. Write the Apex code
A simple example is provided in [HelloWorld.cls](HelloWorld.cls).

```apex
public class HelloWorldApp {
    public static String greet(String name) {
        return 'Hello ' + name + ' from Apex';
    }
}
```

### 3. Execute the code
- Open the Execute Anonymous window.
- Run the following snippet:

```apex
String msg = HelloWorldApp.greet('Cloud Lab');
System.debug(msg);
```

### 4. Check the output
- Open the debug log and verify that the message appears correctly.

## Results
The Apex class was created and executed successfully, and the expected output was observed in the Salesforce debug log.