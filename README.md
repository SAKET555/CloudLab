# Cloud Computing Lab Manual (2022 Scheme)

Welcome to the **Cloud Computing Lab** repository! This repository contains a comprehensive collection of 11 hands-on experiments covering major cloud platforms, virtualization, cloud simulation, Apex programming, and serverless architectures.

All experiments are organized into dedicated folders containing step-by-step procedures, source code, configuration files, output screenshots, and results.

---

## Table of Experiments

| Exp # | Experiment Title | Tech Stack / Platform | Link | Screenshots |
|:---:|---|---|:---:|:---:|
| **01** | **Virtualization Setup**<br>Install VirtualBox/VMware Workstation with Linux or Windows OS | VirtualBox, Linux / Windows | [View Experiment](./Experiment_01_VirtualBox) | 6 Images |
| **02** | **Virtual Machine C Compiler**<br>Install C Compiler in Virtual Machine and Execute Simple Program | Linux (Ubuntu), GCC, VirtualBox | [View Experiment](./Experiment_02_C_Compiler) | 5 Images |
| **03** | **AWS EC2 Instance**<br>Create EC2 Instance in AWS (Amazon Web Services) | AWS EC2, Linux AMI, SSH | [View Experiment](./Experiment_03_AWS_EC2) | 8 Images |
| **04** | **Salesforce Apex Application**<br>Develop Simple Application using Apex Programming Language | Salesforce Developer Console, Apex | [View Experiment](./Experiment_04_Salesforce_Apex) | Apex Code |
| **06** | **CloudSim Simulation**<br>Simulate Cloud Scenario using CloudSim & Custom Scheduling Algorithm | Java, CloudSim API, Eclipse | [View Experiment](./Experiment_06_CloudSim_Simulation) | Console Logs |
| **09** | **Google App Engine**<br>Use Google App Engine Launcher to Launch Web Applications | Google App Engine, Python, `app.yaml` | [View Experiment](./Experiment_09_Google_App_Engine) | 5 Images |

---

## Repository Structure

```
CLOUD_LAB/
├── README.md                              # Universal Repository Guide
├── Experiment_01_VirtualBox/              # Exp 1: VirtualBox & OS Installation
├── Experiment_02_C_Compiler/              # Exp 2: VM C Compiler Setup & Execution
├── Experiment_03_AWS_EC2/                 # Exp 3: AWS EC2 Instance Creation
├── Experiment_04_Salesforce_Apex/         # Exp 4: Salesforce Apex Application
├── Experiment_06_CloudSim_Simulation/     # Exp 6: CloudSim Simulation & Scheduling
└── Experiment_09_Google_App_Engine/       # Exp 9: Google App Engine Web App
```

---

## Summary of Technologies & Platforms Used
- **Cloud Providers**: Amazon Web Services (AWS EC2, S3, CloudFront), Microsoft Azure (Blob Storage), Salesforce Cloud, Google App Engine (GAE).
- **Virtualization & Simulation**: Oracle VM VirtualBox, CloudSim Simulation Toolkit.
- **Languages & Frameworks**: C (`gcc`), Python (`Pillow`, `azure-storage-blob`), Java (CloudSim), Apex (Salesforce), YAML, JSON.
- **Web Servers & CDNs**: Apache HTTP Server (`httpd`), AWS CloudFront CDN.

---

## Getting Started

To explore any experiment:
1. Navigate into the experiment folder of interest (e.g. `cd Experiment_03_AWS_EC2`).
2. Read `README.md` for complete aim, procedure, code, configuration steps, and screenshot walkthroughs.
3. Screenshots are stored inside each folder's `images/` directory.
