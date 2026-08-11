# Experiment 6: Simulate Cloud Scenario using CloudSim and Custom Scheduling Algorithm

## Aim
To simulate a cloud computing scenario using the CloudSim framework and execute a custom scheduling policy.


## Procedure

### Setting Up CloudSim in Eclipse

#### Step 1: Download and Extract CloudSim
Download the CloudSim library from the official repository and extract the files to a directory on your local machine.

#### Step 2: Open Eclipse IDE
Launch your Eclipse IDE workspace.

#### Step 3: Create a New Java Project
Navigate to **File** > **New** > **Java Project** to create a blank Java project.

#### Step 4: Import CloudSim Libraries
Import the extracted CloudSim folder and JAR files into your newly created Java project's Build Path.

#### Step 5: Initialize the CloudSim Library
Initialize the CloudSim package core before setting up any simulation entities:
```java
CloudSim.init(num_user, calendar, trace_flag);
```

#### Step 6: Create a Datacenter
Datacenters serve as resource providers in CloudSim. Instantiate a `Datacenter` object with its core characteristics (architecture, OS, host list, allocation policy, time zone, and pricing):
```java
Datacenter datacenter = new Datacenter(name, characteristics, new VmAllocationPolicySimple(hostList), storageList, schedulingInterval);
```

#### Step 7: Create a Datacenter Broker
Create a `DatacenterBroker` object to manage and coordinate VMs and cloudlets:
```java
DatacenterBroker broker = createBroker();
```

#### Step 8: Instantiate a Virtual Machine (VM)
Create a Virtual Machine (VM) configuration specifying its VM ID, owner ID (broker ID), MIPS rating, CPU count (PEs), RAM, bandwidth, storage size, hypervisor monitor name, and cloudlet scheduler policy:
```java
Vm vm = new Vm(vmid, brokerId, mips, pesNumber, ram, bw, size, vmm, new CloudletSchedulerTimeShared());
```

#### Step 9: Submit the VM List to the Broker
Register the list of VMs with the broker:
```java
broker.submitVmList(vmlist);
```

#### Step 10: Create Cloudlets (Tasks)
Instantiate a `Cloudlet` representation of your tasks, specifying the ID, length (in MI), CPU count, file size, output size, and utilization model:
```java
Cloudlet cloudlet = new Cloudlet(id, length, pesNumber, fileSize, outputSize, utilizationModel, utilizationModel, utilizationModel);
```

#### Step 11: Submit the Cloudlet List to the Broker
Register the list of Cloudlets with the broker:
```java
broker.submitCloudletList(cloudletList);
```

#### Step 12: Start the Simulation
Execute the CloudSim engine:
```java
CloudSim.startSimulation();
```

---

### Sample Console Output Log
```text
Starting CloudSimExample1...
Initializing...
Starting CloudSim version 3.0
Datacenter_0 is starting...
Broker is starting...
Entities started.
0.0: Broker: Cloud Resource List received with 1 resource(s)
0.0: Broker: Trying to Create VM #0 in Datacenter_0
0.1: Broker: VM #0 has been created in Datacenter #2, Host #0
0.1: Broker: Sending cloudlet 0 to VM #0
400.1: Broker: Cloudlet 0 received
400.1: Broker: All Cloudlets executed. Finishing...
400.1: Broker: Destroying VM #0
Broker is shutting down...
Simulation: No more future events
CloudInformationService: Notify all CloudSim entities for shutting down.
Datacenter_0 is shutting down...
Broker is shutting down...
Simulation completed.
Simulation completed.

========== OUTPUT ==========
Cloudlet ID   STATUS    Datacenter ID   VM ID   Time    Start Time   Finish Time
0             SUCCESS   2               0       400     0.1          400.1

*****Datacenter: Datacenter_0*****
Userid   Debt
3        35.6

CloudSimExample1 finished!
```


## Results

The cloud simulation using CloudSim was successfully configured, executed, and verified.