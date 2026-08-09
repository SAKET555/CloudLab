# Experiment 9: Use Google App Engine Launcher to Launch Web Applications

## Aim
To deploy a simple web application on Google App Engine and verify that it runs correctly.

## Procedure

### 1. Create the App Engine files
- Create a project folder and add the required configuration files.
- Use the sample files [app.yaml](app.yaml) and [main.py](main.py).

```yaml
runtime: python311
entrypoint: gunicorn -b :$PORT main:app
```

```python
from flask import Flask

app = Flask(__name__)

@app.route("/")
def hello():
    return "Hello from a Cloud Lab App Engine app!"
```

### 2. Deploy the application
- Use the Google Cloud SDK or App Engine tools to deploy the app.
- Verify the service URL in the console.

### 3. Test the deployment
- Open the deployed URL in a browser.
- Confirm that the response appears correctly.

## Results
The web application was successfully deployed and tested on Google App Engine.