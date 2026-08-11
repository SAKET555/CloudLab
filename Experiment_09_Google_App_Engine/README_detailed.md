# Experiment 9: Use Google App Engine Launcher to Launch Web Applications (Detailed Guide)

## Aim
To develop a basic web application, configure its runtime handler, run it locally using the Google App Engine (GAE) Software Development Kit (SDK) / Launcher interface, and monitor logs for application troubleshooting.

---

## Conceptual Background

### 1. What is Platform-as-a-Service (PaaS)?
Unlike Infrastructure-as-a-Service (IaaS, like AWS EC2) where you manage virtual machines and OS patches yourself, **Platform-as-a-Service (PaaS)** manages the underlying VM, OS, scaling, load balancing, and runtime environment for you. Google App Engine is a fully managed PaaS solution. You simply upload your code, and GAE takes care of resource scaling and networking.

### 2. GAE Configuration (`app.yaml`)
The `app.yaml` file is the deployment descriptor. It specifies how App Engine routes URLs to your server scripts and defines resource and runtime settings:
- `application`: A unique identifier for your project.
- `runtime`: The language environment (e.g., `python`).
- `api_version`: Specifies the API integration tier (e.g., `1`).
- `handlers`: Routing rules. The mapping `- url: /.*` and `script: index.py` acts as a wildcard catch-all, directing all traffic (`http://localhost:8080/anything`) to the `index.py` script.

### 3. CGI (Common Gateway Interface) Scripting
The python code in this experiment utilizes the traditional CGI pattern. In CGI, the web server runs a script and returns its stdout directly to the client's browser. The script must output:
1. **HTTP Headers**: Specifically `Content-Type` (e.g., `Content-Type: text/plain` or `text/html`).
2. **An Empty Line**: Serves as a delimiter separating the HTTP headers from the response body.
3. **The Response Body**: The actual data (text/html) rendered to the user.

---

## Detailed Step-by-Step Procedure

### Step 1: Create application directories and source files
1. Create a root directory named `apps` on your system.
2. Inside `apps`, create a project subfolder named `ae-01-trivial`.
3. Open a text editor (such as VS Code, Notepad++, or JEdit) and create the configuration file `app.yaml` in the project directory:
```yaml
application: ae-01-trivial
version: 1
runtime: python
api_version: 1

handlers:
  - url: /.*
    script: index.py
```
4. Create the main script file named `index.py` in the same directory:
```python
print 'Content-Type: text/plain'
print '' # CRITICAL: blank line delimiter
print 'Hello there Chuck'
```

### Step 2: Register project in GAE Launcher
1. Open the **Google App Engine Launcher**.
2. Select **File** > **Add Existing Application**.
3. Browse and select the `ae-01-trivial` directory. Click **Add**. The application will appear in the main project list.

![Step Screenshot](images/step_image_1.png)

### Step 3: Run the web server and test locally
1. Click the **Run** button (green arrow) in the launcher dashboard. This spins up the local Python web server.
2. Once the server is running, the status light next to the application name turns green.
3. Click the **Browse** button or open a web browser and go to `http://localhost:8080`. The text output will load:

![Step Screenshot](images/step_image_2.png)

4. Update `index.py` to customize the printed message, save the changes, and click **Refresh** in your browser. GAE automatically detects file changes and reloads the server instantly.

### Step 4: Monitor server access logs
1. Click the **Logs** button in the launcher dashboard. A console window will open.
2. When you refresh the browser page, you can monitor HTTP request logs showing access protocols, timestamps, path info, and response codes (e.g. `200 OK` or `304 Not Modified`):

![Step Screenshot](images/step_image_3.png)

### Step 5: Handling and Debugging Errors
If you introduce a syntax or logic error (for example, omitting the blank print statement delimiter between headers and body), the GAE server will fail to parse the HTTP response and output a `500 Internal Server Error` in the browser:

![Step Screenshot](images/step_image_4.png)

To diagnose the problem, open the GAE console logs to see the exception stack trace and identify which file and line number caused the execution failure:

![Step Screenshot](images/step_image_5.png)

---

## Results
A Python web application was built and configured using custom routing files (`app.yaml`). The application was successfully registered, hosted, and debugged on a local server using the Google App Engine Launcher.
