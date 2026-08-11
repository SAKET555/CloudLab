# Experiment 9: Use Google App Engine Launcher to Launch Web Applications

## Aim
To use the Google App Engine Launcher to run and deploy a local web application.


## Procedure

### Step 1: Create the Project Files
Create a new project directory on your desktop or workspace named `ae-01-trivial`. Inside this folder, create the following two files:

#### Application Configuration (`app.yaml`)
```yaml
application: ae-01-trivial
version: 1
runtime: python
api_version: 1

handlers:
  - url: /.*
    script: index.py
```

#### Python Script (`index.py`)
```python
print 'Content-Type: text/plain'
print ''
print 'Hello there Chuck'
```

---

### Step 2: Add the Application to the GAE Launcher
1. Open the **Google App Engine Launcher** application.
2. Select **File** > **Add Existing Application** from the top menu.
3. Browse to and select the `ae-01-trivial` folder, then click **Add**.
4. Select the application in the launcher list to enable controls.

![Step Screenshot](images/step_image_1.png)

---

### Step 3: Run and Browse the Application
1. Click the **Run** button at the top of the GAE Launcher interface to start the local server. A green status indicator will appear next to the project name.
2. Click the **Browse** button or open your web browser and navigate to `http://localhost:8080/`. You should see the text output displayed.

![Step Screenshot](images/step_image_2.png)

3. Open `index.py` in your text editor, change the name `'Chuck'` to your own name, save the file, and refresh your browser to verify the updates.

---

### Step 4: Monitor Application Logs
1. Click the **Logs** button in the launcher to open the real-time server log window.
2. Every time you reload the browser page, you will see server GET requests being processed:

![Step Screenshot](images/step_image_3.png)

---

### Step 5: Troubleshooting and Dealing with Errors
If there is a syntax or handler error in your script (e.g., misconfigured `app.yaml` or `index.py`), the browser will output an error details page:

![Step Screenshot](images/step_image_4.png)

To diagnose the problem, open the GAE Launcher log console to view the traceback and locate the issue:

![Step Screenshot](images/step_image_5.png)


## Results

The Python web application was successfully launched, modified, and monitored using the Google App Engine Launcher.