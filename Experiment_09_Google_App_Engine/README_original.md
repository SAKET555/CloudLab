# Experiment 9: Use Google App Engine Launcher to Launch Web Applications

## Aim
To use Google App Engine Launcher to launch web applications.


## Procedure

9. Use Google App Engine Launcher to launch web applications.
C:\Documents and Settings\csev\Desktop\apps And then make a sub--‐folder in within apps called “ae--01--trivial” – the path to this folder would be: C:\ Documents and Settings \csev\Desktop\apps\ae--01--trivial Using a text editor such as JEdit (www.jedit.org)
### Application Configuration (`app.yaml`)
```yaml
application: ae-01-trivial
version: 1
runtime: python
api_version: 1

handlers:
  - url: /.*
    script: index.py
```

### Python Script (`index.py`)
```python
print 'Content-Type: text/plain'
print ''
print 'Hello there Chuck'
```
Then create a file in the ae--01--trivial folder called index.py with three lines in it: print 'Content-Type: text/plain' print ' ' print 'Hello there Chuck'
Then start the GoogleAppEngineLauncher program that can be found under Applications. Use the File --> Add Existing Application command and navigate into the apps directory and select the ae--01--trivial folder.
Once you have added the application, select it so that you can control the application using the launcher.

![Step Screenshot](images/step_image_1.png)

Once you have selected your application and press Run. After a few moments your application will start and the launcher will show a little green icon next to your application.
Then press Browse to open a browser pointing at your application which is running at http://localhost:8080/
Paste http://localhost:8080 into your browser and you should see your application as follows:

![Step Screenshot](images/step_image_2.png)

Edit the index.py to change the name “Chuck” to your own name and press Refresh in the browser to verify your updates.
Watching the Log You can watch the internal log of the actions that the web server is performing when you are interacting with your application in the browser.
Select your application in the Launcher and press the Logs button to bring up a log window:
Each time you press Refresh in your browser – you can see it retrieving the output with a GET request.

![Step Screenshot](images/step_image_3.png)

Dealing with Errors
### Application Configuration (`app.yaml`)
```yaml
application: ae-01-trivial
version: 1
runtime: python
api_version: 1

handlers:
  - url: /.*
    script: index.py
```

### Python Script (`index.py`)
```python
print 'Content-Type: text/plain'
print ''
print 'Hello there Chuck'
```

![Step Screenshot](images/step_image_4.png)

To get more detail on what is going wrong, take a look at the log for the application:

![Step Screenshot](images/step_image_5.png)


## Results

Thus the GAE web applications were created.
