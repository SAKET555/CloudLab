# Experiment 6: Simulate Cloud Scenario using CloudSim and Custom Scheduling Algorithm

## Aim
To Simulate a cloud scenario using CloudSim and run a scheduling algorithm that is not present in Cloud Sim.


## Procedure

6. Simulate a cloud scenario using CloudSim and run a scheduling algorithm that is not present in CloudSim.
To use CloudSim in Eclipse:

### Step 1: Download CloudSim installable files from
https://code.google.com/p/cloudsim/downloads/list and unzip

### Step 2: Open Eclipse

### Step 3: Create a new Java Project: File ->New

### Step 4: Import an unpacked CloudSim project into the new Java Project

### Step 5: The first step is to initialize the CloudSim package by initializing the CloudSim library as follows:
```java
CloudSim.init(num_user, calendar, trace_flag)
```

### Step 6: Data centres are the resource providers in CloudSim; hence, creation of data centres is a second step. To create Datacenter, you need the Data center Characteristics object that stores the properties of a data centre such as architecture, OS, list of machines, allocation policy that covers the time or space shared, the time zone and its price:
```java
Datacenter data center 9883 = new Datacenter(name, characteristics, new Vm Allocation Policy Simple(host List)
```

### Step 7: The third step is to create abroker:
```java
DatacenterBroker broker = createBroker();
```

### Step 8: The fourth step is to create one virtual machine unique ID of the VM, userId ID of the VM‟s owner, mips, number of Pes amount of CPUs, amount of RAM, amount of bandwidth, amount of storage, virtual machine monitor, and cloud let Scheduler policy for cloudlets:
```java
Vm vm = new Vm(vmid, brokerId, mips, pesNumber, ram, bw, size, vmm, new
```
CloudletSchedulerTimeShared())

### Step 9: Submit the VM list to the broker: broker.submitVmList(vmlist)

### Step 10: Create a cloudlet with length, file size, output size, and utilisationmodel:
```java
Cloudlet cloudlet = new Cloudlet(id, length, pesNumber, fileSize, outputSize, utilizationModel, utilizationMode
```

### Step 11: Submit the cloudlet list to the broker: broker.submitCloudletList(cloudletList)

### Step 12: Start the simulation: CloudSim.startSimulation()

### Sample Output from the Existing Example:
```text
Starting
CloudSimExample1...
```
Initialising...
```text
Starting CloudSim version 3.0 Datacenter_0 is starting...
```
>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>null
```text
Broker is
```
starting...
```text
Entities started.
```
: Broker: Cloud Resource List received with
1resource(s) 0.0: Broker: Trying to Create VM #0
inDatacenter_0
: Broker: VM #0 has been created in Datacenter #2, Host#0
0.1: Broker: Sending cloudlet 0 to VM #0
400.1: Broker: Cloudlet 0 received
: Broker: All Cloudlets executed. Finishing....400.1: Broker:
Destroying VM#0
```text
Broker is shutting down...
Simulation: No more future events
```
CloudInformationService: Notify all CloudSim entities for shutting down. Datacenter_0 is shutting down...
```text
Broker is shutting down...
Simulation completed.
Simulation completed.
```

### =========OUTPUT===========
Cloudlet ID STATUS Data center ID VM ID Time Start Time Finish Time
```text
0 SUCCESS 20 400 0.1 400.1
*****Datacenter: Datacenter_0***** Userid Debt
```
3 35.6
```text
CloudSimExample1 finished!
```

## Results

The experiment for 'Simulate Cloud Scenario using CloudSim and Custom Scheduling Algorithm' was successfully implemented, configured, and verified.