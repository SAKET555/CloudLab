# Experiment 3: Create EC2 Instance in AWS (Amazon)

## Aim
To create an Amazon EC2 instance and configure it for a basic cloud computing task.

## Procedure

### 1. Launch an EC2 instance
- Sign in to the AWS Management Console.
- Open the EC2 service and click Launch Instance.
- Choose an Amazon Machine Image (AMI), instance type, and storage settings.
- Assign a key pair and configure the security group.

![Step Screenshot](images/step_image_1.png)

### 2. Connect to the instance
- Select the running instance and click Connect.
- Use the private key file to connect using SSH.
- Verify that the instance is reachable.

![Step Screenshot](images/step_image_2.png)

### 3. Bootstrap the instance
- Use a user-data script to install a service automatically after boot.
- A sample script is provided in [user-data.sh](user-data.sh).

```bash
#!/bin/bash
yum update -y
yum install -y nginx
systemctl enable nginx
systemctl start nginx
```

### 4. Verify the service
- Open the public IP address in a browser.
- Confirm that the web server responds correctly.

## Results
The EC2 instance was created successfully and initialized with a basic bootstrap configuration for remote access and service deployment.