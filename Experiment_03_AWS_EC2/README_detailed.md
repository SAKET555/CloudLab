# Experiment 3: Create EC2 Instance in AWS (Detailed Guide)

## Aim
To provision and launch an Amazon Elastic Compute Cloud (EC2) virtual machine on AWS, configure its hardware parameters, storage, and networking under the AWS Free Tier, and establish a remote terminal connection using SSH key-pair authentication.

---

## Conceptual Background

### 1. Amazon EC2
Amazon Elastic Compute Cloud (Amazon EC2) provides scalable computing capacity in the Amazon Web Services (AWS) cloud. It enables users to deploy virtual servers (called "instances"), configure security and networking, and manage storage volumes.

### 2. Core AWS EC2 Concepts
- **AMI (Amazon Machine Image)**: A template containing a software configuration (operating system, application server, and applications) required to launch your instance.
- **Instance Type**: Hardware configurations of CPU, memory, storage, and networking capacity. The `t2.micro` instance provides 1 vCPU and 1 GiB memory and is free-tier eligible.
- **Key Pair**: AWS uses public-key cryptography to secure the login information for your instance. The public key is stored on the instance, and the private key (`.pem` file) is kept by the user.
- **Security Groups**: A virtual firewall that controls inbound and outbound traffic for your instance.

---

## Detailed Step-by-Step Procedure

### Phase 1: Provisioning the Instance

#### Step 1: Access the EC2 Console
Log in to your AWS Management Console. Locate the **Services** menu on the top navigation bar, select the **Compute** category, and click **EC2**.

![Step Screenshot](images/step_image_1.png)

#### Step 2: Configure Name and Tags
In the EC2 Dashboard, click **Launch Instance**. In the metadata setup area, enter a name (e.g., `My-Web-Server`) to tag your resource for billing and organizational purposes.

![Step Screenshot](images/step_image_2.png)

#### Step 3: Choose an Operating System (AMI)
In the Application and OS Images panel, choose your preferred OS template. Ensure the tag **Free tier eligible** is visible (for example, *Amazon Linux 2023 AMI* or *Ubuntu Server 22.04 LTS*).

![Step Screenshot](images/step_image_3.png)

#### Step 4: Configure Instance Type and Key Pair
Select `t2.micro` (or `t3.micro` where applicable) as the instance type. In the key pair section, select an existing key pair or click **Create new key pair**. Download the `.pem` private key file and store it in a secure directory on your local machine.

![Step Screenshot](images/step_image_4.png)

#### Step 5: Configure Storage and Networking
Verify the storage configuration. Under the free tier, AWS allows up to 30 GB of General Purpose (SSD) or Magnetic EBS storage. Leave the network settings at their default values (which auto-assigns a Public IP and configures a default security group allowing inbound SSH traffic).

![Step Screenshot](images/step_image_5.png)

#### Step 6: Launch the Instance
Verify all configuration details in the Summary panel on the right. Once checked, click the **Launch instance** button. AWS will initiate the setup, and the instance state will transition to "Running" shortly.

![Step Screenshot](images/step_image_6.png)

---

### Phase 2: Connecting via SSH

#### Step 1: View Instance Details
Go back to the EC2 Instances page, select your newly launched running instance, and click the **Connect** button at the top menu bar.

![Step Screenshot](images/step_image_6.png)

#### Step 2: Retrieve SSH Client Details
In the connection wizard, navigate to the **SSH client** tab. This page displays the exact hostname and username details, along with a ready-to-copy SSH connect command template:
```bash
ssh -i "your-key.pem" username@ec2-public-ip.compute-1.amazonaws.com
```

![Step Screenshot](images/step_image_7.png)

#### Step 3: Run SSH in Terminal
1. Open a terminal on your host machine (e.g., Git Bash, Terminal, or PowerShell).
2. Navigate to the directory containing the downloaded `.pem` private key file:
   ```bash
   cd ~/Downloads
   ```
3. Set the appropriate file permissions (read-only by owner) on Unix-like operating systems to prevent SSH configuration warning errors:
   ```bash
   chmod 400 your-key.pem
   ```
4. Paste and execute the copied SSH command. Type `yes` when prompted to verify the host authenticity to establish a shell connection.

![Step Screenshot](images/step_image_8.png)

---

## Results
A virtual machine instance was provisioned, configured, and successfully launched on AWS EC2. Connection to the remote virtual server was established using terminal SSH-key credentials.
