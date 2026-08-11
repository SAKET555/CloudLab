# Experiment 6: Simulate Cloud Scenario using CloudSim (Detailed Guide)

## Aim
To set up, configure, and execute a discrete event cloud simulation using the CloudSim framework in an Eclipse environment, modeling cloud resources (Datacenters, Hosts, Virtual Machines) and scheduling policies for tasks (Cloudlets).

---

## Conceptual Background

### 1. What is CloudSim?
CloudSim is an open-source Java framework for modeling and simulating cloud computing infrastructures and services. In real cloud environments, conducting experiments (like scheduling algorithms or load balancing policies) can be costly and difficult to reproduce. CloudSim allows researchers and developers to evaluate the performance of cloud provisioning policies under controlled and repeatable conditions without any financial cost.

### 2. Core Entities in CloudSim
- **Datacenter**: Represents the physical cloud infrastructure provider. It contains physical hardware (Hosts) and manages VM allocation policies.
- **Host**: Models a physical machine (PM) inside a datacenter. It has physical resource capacities like CPU cores (PEs - Processing Elements) with designated processing speeds (MIPS - Million Instructions Per Second), RAM, storage, and network bandwidth.
- **VM (Virtual Machine)**: Represents the software virtualization execution environment. VMs run on Hosts, sharing resources according to VM allocation and scheduling policies.
- **Cloudlet**: Represents application services or tasks to be executed in the cloud. Each cloudlet has a specified length (measured in Million Instructions, MI), file size, and output size.
- **Datacenter Broker**: Acts as a proxy or agent on behalf of the customer, negotiating with datacenters to submit VM provisioning plans and task/cloudlet scheduling queues.

---

## Detailed Step-by-Step Procedure

### Phase 1: Environment Setup in Eclipse
1. **Download CloudSim**: Download the CloudSim zip archive (e.g. version 3.0.3 or 4.0) from the official GitHub releases page and extract it locally.
2. **Launch Eclipse IDE** and set up a workspace folder.
3. **Create Java Project**: Navigate to **File** > **New** > **Java Project**. Enter a project name (e.g., `CloudSimDemo`) and click **Finish**.
4. **Configure Java Build Path**: 
   - Right-click your project in the Package Explorer and select **Build Path** > **Configure Build Path**.
   - Select the **Libraries** tab and click **Add External JARs**.
   - Navigate to your extracted CloudSim directory, select the `cloudsim-3.0.3.jar` (and other dependencies like `commons-math3` if needed), and click **Open**.
   - Click **Apply and Close**.

---

### Phase 2: Writing the Simulation Code

#### Step 1: Initialize CloudSim
Before instantiating any simulation objects, initialize the CloudSim library. It sets up the system clock, event queues, and logging:
```java
int num_user = 1; // number of cloud users / brokers
Calendar calendar = Calendar.getInstance(); // system calendar tracking
boolean trace_flag = false; // trace event logs to file

CloudSim.init(num_user, calendar, trace_flag);
```

#### Step 2: Create a Datacenter
A datacenter is created by instantiating a `Datacenter` class, which requires characteristics such as Host configuration, VM allocation policy, and network setup:
```java
// Define host processing elements (PEs) and their speed
List<Pe> peList = new ArrayList<Pe>();
int mips = 1000;
peList.add(new Pe(0, new PeProvisionerSimple(mips)));

// Define physical host resources
List<Host> hostList = new ArrayList<Host>();
int hostId = 0;
int ram = 2048; // Host memory (MB)
long storage = 1000000; // Host storage (MB)
int bw = 10000; // Bandwidth
hostList.add(new Host(
    hostId,
    new RamProvisionerSimple(ram),
    new BwProvisionerSimple(bw),
    storage,
    peList,
    new VmSchedulerTimeShared(peList)
));

// Define Datacenter characteristics
String arch = "x86";
String os = "Linux";
String vmm = "Xen";
double time_zone = 10.0;
double costPerSec = 3.0;
double costPerMem = 0.05;
double costPerStorage = 0.001;
double costPerBw = 0.0;

DatacenterCharacteristics characteristics = new DatacenterCharacteristics(
    arch, os, vmm, hostList, time_zone, costPerSec, costPerMem, costPerStorage, costPerBw
);

// Instantiate Datacenter
Datacenter datacenter = new Datacenter(
    "Datacenter_0",
    characteristics,
    new VmAllocationPolicySimple(hostList),
    new LinkedList<Storage>(),
    0
);
```

#### Step 3: Create a Broker
The broker acts as the customer management system:
```java
DatacenterBroker broker = new DatacenterBroker("Broker_0");
int brokerId = broker.getId();
```

#### Step 4: Create a Virtual Machine (VM)
Configure the VM specifications (RAM, CPU cores, processing speed, bandwidth, disk space) and attach it to the broker:
```java
int vmid = 0;
int vm_mips = 1000;
long size = 10000; // image size (MB)
int vm_ram = 512; // VM memory (MB)
long vm_bw = 1000; // Bandwidth
int pesNumber = 1; // number of CPUs
String vm_vmm = "Xen"; // VMM name

Vm vm = new Vm(vmid, brokerId, vm_mips, pesNumber, vm_ram, vm_bw, size, vm_vmm, new CloudletSchedulerTimeShared());

// Add VM to user VM List
List<Vm> vmlist = new ArrayList<Vm>();
vmlist.add(vm);
broker.submitVmList(vmlist);
```

#### Step 5: Create a Cloudlet (Task)
Define the task payload, size, and resource utilization models:
```java
int id = 0;
long length = 400000; // task length in Million Instructions (MI)
long fileSize = 300; // file input size (bytes)
long outputSize = 300; // output results size (bytes)

// Define resource utilization models (CPU, RAM, Bandwidth)
UtilizationModel utilizationModel = new UtilizationModelFull();

Cloudlet cloudlet = new Cloudlet(id, length, pesNumber, fileSize, outputSize, utilizationModel, utilizationModel, utilizationModel);
cloudlet.setUserId(brokerId);

// Add Cloudlet to user list
List<Cloudlet> cloudletList = new ArrayList<Cloudlet>();
cloudletList.add(cloudlet);
broker.submitCloudletList(cloudletList);
```

#### Step 6: Execute the Simulation
Run the simulation runner and wait for events to conclude:
```java
CloudSim.startSimulation();
CloudSim.stopSimulation();
```

---

### Phase 3: Analyzing Log Output
When running the simulation main class, CloudSim logs the creation of datacenters, initialization of virtual machine monitors, binding of resources, execution times, and financial calculations:

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

---

## Results
The CloudSim simulation library was successfully configured inside the Eclipse IDE. A virtual cloud computing landscape comprising datacenters, host machines, virtual machine specifications, and active user brokers was set up and executed. Tasks were scheduled and executed according to default resource allocation parameters, and the log outputs verified successful completion.
