# Cloud Computing Lab

This repository contains the practical work completed as part of the Cloud Computing Laboratory. It covers virtual machine configuration, network connectivity, network topology creation, and Software-Defined Networking (SDN) implementation using open-source tools.

---

# Experiment 1 — Virtual Machine Setup and Configuration

## Overview

This experiment focuses on creating, configuring, and verifying an Ubuntu Virtual Machine using Oracle VirtualBox.

## Objective

To install and configure an open-source hypervisor, create an Ubuntu Virtual Machine, configure its virtual hardware resources, verify that the VM runs successfully, and install the required build tools and Linux kernel headers.

## Software and Environment

| Parameter | Configuration |
|---|---|
| Hypervisor | Oracle VirtualBox |
| Guest Operating System | Ubuntu |
| Architecture | 64-bit |
| Virtual Machine | Ubuntu 26.04 |
| Network Mode | NAT |
| Virtual CPU | 3 CPUs |
| Base Memory | 4096 MB |
| Virtual Hard Disk | 25 GB |

## Tasks Completed

### Task 1 — Install Oracle VirtualBox
Installed and configured Oracle VirtualBox, an open-source virtualization platform used to create and manage virtual machines.

### Task 2 — Create a New Virtual Machine
Created a new virtual machine with the following configuration:

- VM Name: Ubuntu 26.04
- Operating System: Linux
- Distribution: Ubuntu
- Version: Ubuntu (64-bit)

### Task 3 — Configure the Virtual Machine

Configured the virtual hardware resources:

- CPU: 3 processors
- RAM: 4096 MB
- Storage: 25 GB virtual hard disk
- Network: NAT

### Task 4 — Configure VM Hardware
Verified the CPU, memory, storage, and network configuration through Oracle VirtualBox settings.

### Task 5 — Configure Ubuntu Installation
Selected the Ubuntu ISO image and configured the required options for creating the Ubuntu virtual machine.

### Task 6 — Start the Virtual Machine
Started the Ubuntu virtual machine and proceeded with the boot process.

### Task 7 — Verify Ubuntu VM
Verified that the Ubuntu virtual machine successfully booted and the Ubuntu desktop environment was accessible.

### Task 8 — Install Required Build Tools

```bash
sudo apt update
sudo apt install -y build-essential linux-headers-$(uname -r)
```

---

# Experiment 2 — VM Cloning and Network Connectivity

## Overview

This experiment demonstrates the cloning of an Ubuntu Virtual Machine using Oracle VirtualBox and establishing network connectivity between the original and cloned virtual machines.

Both VMs are connected to a customized NAT Network, allowing them to communicate with each other through their assigned IP addresses.

## Objective

- Clone an existing Ubuntu Virtual Machine.
- Create and configure a customized NAT Network.
- Connect both VMs to the same NAT Network.
- Verify the network interface and IP configuration.
- Verify communication between the VMs using the `ping` command.
- Verify successful two-way connectivity through packet transmission.

## Tools and Technologies

- Oracle VirtualBox
- Ubuntu Linux
- NAT Network
- Linux Networking Commands

## Network Configuration

| Parameter | Configuration |
|---|---|
| Network Type | NAT Network |
| Network Name | MyNatNetwork |
| IPv4 Network | 10.0.2.0/24 |
| DHCP | Enabled |
| Network Interface | enp0s3 |

Both the original and cloned Ubuntu VMs were connected to the same `MyNatNetwork`.

## VM Configuration

### Original VM

- Attached to: NAT Network
- Network Name: MyNatNetwork
- Virtual Cable: Connected

### Useful Networking Commands

Check network interfaces and IP addresses:

```bash
ip a
```

Test connectivity between the virtual machines:

```bash
ping <destination-ip>
```

Stop the ping process:

```bash
Ctrl + C
```

---

# Experiment 3 — Creation of a Simple Network Topology Using Open-Source Network Virtualization Tools

## Overview

This experiment demonstrates the creation, configuration, and testing of different network topologies using Mininet, an open-source network virtualization tool running on an Ubuntu Linux Virtual Machine.

The experiment focuses on creating Single-Switch, Tree, and Linear topologies and verifying communication between virtual network nodes using basic Linux networking commands.

## Objective

To create and configure simple network topologies using Mininet and verify communication between virtual network nodes using basic Linux networking commands.

## Tools Used

- Ubuntu Linux
- Oracle VirtualBox
- Mininet
- Open vSwitch

## Mininet Installation and Setup

Mininet was installed along with its required dependencies using the Ubuntu package manager.

### Installation

```bash
sudo apt update
sudo apt install mininet -y
```

### Verify Installation

```bash
mn --version
```

### Clean Previous Mininet Configurations

```bash
sudo mn -c
```

---

# Experiment 4 — Implementation of Software-Defined Networking Using Ryu, Mininet and Open vSwitch

## Overview

This experiment demonstrates the implementation of a Software-Defined Networking (SDN) environment using the Ryu SDN Controller, Mininet and Open vSwitch.

A single-switch topology containing three hosts is created in Mininet. The Ryu controller manages the virtual switch using OpenFlow 1.3. Host connectivity is tested, switch flow-table entries are inspected, and a traffic-filtering rule is added and removed using Open vSwitch commands.

## Objective

- Configure an SDN environment using open-source tools.
- Install and configure the Ryu SDN Controller.
- Create a virtual network topology using Mininet.
- Establish communication between the Ryu controller and Open vSwitch.
- Verify connectivity between virtual hosts.
- Inspect OpenFlow flow-table entries.
- Demonstrate traffic filtering using a drop rule.

## Tools and Technologies

| Component | Technology |
|---|---|
| Operating System | Ubuntu Linux |
| Virtualization Platform | Oracle VirtualBox |
| Network Emulator | Mininet |
| Virtual Switch | Open vSwitch |
| SDN Controller | Ryu 4.34 |
| Communication Protocol | OpenFlow 1.3 |
| Python Version | Python 3.9.25 |

## 1. Update Ubuntu and Install Required Packages

Update the Ubuntu package index:

```bash
sudo apt update
```

Upgrade installed packages:

```bash
sudo apt upgrade -y
```

Install the required utilities:

```bash
sudo apt install -y git curl ca-certificates build-essential
```

Install Mininet, Open vSwitch and Python tools:

```bash
sudo apt install -y mininet openvswitch-switch python3 python3-pip python3-venv
```

## 2. Start and Verify Open vSwitch

Enable and start the Open vSwitch service:

```bash
sudo systemctl enable --now openvswitch-switch
```

Check the service status:

```bash
sudo systemctl status openvswitch-switch
```

Display the Open vSwitch configuration:

```bash
sudo ovs-vsctl show
```

## 3. Install Python 3.9 Using uv

Install `uv`:

```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

Refresh the terminal environment if necessary:

```bash
source ~/.bashrc
```

Install Python 3.9:

```bash
uv python install 3.9
```

Verify the Python installation:

```bash
uv python find 3.9
```

## 4. Create and Activate a Python Virtual Environment

Create a virtual environment using Python 3.9:

```bash
uv venv --python 3.9 ~/ryu-env39
```

Activate the environment:

```bash
source ~/ryu-env39/bin/activate
```

Verify the Python version:

```bash
python --version
```

Expected version: Python 3.9.25.

Install compatible packaging tools:

```bash
uv pip install --python ~/ryu-env39/bin/python setuptools==57.5.0 wheel
```

## 5. Install the Ryu SDN Controller

Clone the Faucet-maintained Ryu repository:

```bash
git clone --branch v4.34 https://github.com/faucetsdn/ryu.git ~/ryu-source
```

Move into the source directory:

```bash
cd ~/ryu-source
```

Install Ryu:

```bash
python setup.py install
```

Install the required runtime dependencies:

```bash
uv pip install --python ~/ryu-env39/bin/python eventlet msgpack netaddr oslo.config ovs routes six tinyrpc webob
```

Use a compatible Eventlet version to resolve the `ALREADY_HANDLED` import issue:

```bash
uv pip install --python ~/ryu-env39/bin/python eventlet==0.30.2
```

## 6. Verify the Ryu Installation

Check the Ryu version:

```bash
ryu-manager --version
```

Expected output:

```text
ryu-manager 4.34
```

Verify the OpenFlow 1.3 application:

```bash
python -c "import ryu.app.simple_switch_13; print('OpenFlow 1.3 application OK')"
```

Expected output:

```text
OpenFlow 1.3 application OK
```

## 7. Start the Ryu Controller

Open a separate terminal and activate the virtual environment:

```bash
source ~/ryu-env39/bin/activate
```

Start the Ryu controller with the OpenFlow 1.3 learning-switch application:

```bash
ryu-manager --ofp-tcp-listen-port 6653 ryu.app.simple_switch_13
```

Keep this terminal running while using Mininet.

The controller listens on port `6653`.

## 8. Create the Mininet Topology

Open another terminal and clean previous Mininet configurations:

```bash
sudo mn -c
```

Create a single-switch topology with three hosts and a remote Ryu controller:

```bash
sudo mn --topo single,3 --controller=remote,ip=127.0.0.1,port=6653 --switch ovsk,protocols=OpenFlow13
```

The topology contains:

- Three hosts: h1, h2 and h3
- One Open vSwitch switch: s1
- One remote controller: Ryu
- Communication protocol: OpenFlow 1.3

## 9. Verify the Network Topology

Inside the Mininet CLI, list the available nodes:

```bash
nodes
```

Display the network connections:

```bash
net
```

The expected topology is:

```text
h1 --- s1
h2 --- s1
h3 --- s1
```

## 10. Test Host Connectivity

Test connectivity between all hosts:

```bash
pingall
```

Test communication between two individual hosts:

```bash
h1 ping h2
```

Stop the continuous ping using:

```text
Ctrl + C
```

A successful ping test indicates that the hosts can communicate through the virtual switch.

## 11. Inspect OpenFlow Flow Tables

Open a separate Ubuntu terminal, not the Mininet CLI.

Display the flow-table entries of switch `s1`:

```bash
sudo ovs-ofctl -O OpenFlow13 dump-flows s1
```

This command displays the installed OpenFlow rules, priorities, packet counters, byte counters and forwarding actions.

## 12. Add a Traffic-Filtering Rule

Add a high-priority drop rule for traffic entering through port 1 of switch `s1`:

```bash
sudo ovs-ofctl -O OpenFlow13 add-flow s1 "priority=100,in_port=1,actions=drop"
```

The rule instructs the switch to drop matching incoming traffic instead of forwarding it.

Inspect the updated flow table:

```bash
sudo ovs-ofctl -O OpenFlow13 dump-flows s1
```

The output should contain a rule similar to:

```text
priority=100,in_port="s1-eth1" actions=drop
```

## 13. Remove the Traffic-Filtering Rule

Remove the installed flow entries:

```bash
sudo ovs-ofctl -O OpenFlow13 del-flows s1
```

Inspect the flow table again:

```bash
sudo ovs-ofctl -O OpenFlow13 dump-flows s1
```

## 14. Exit and Clean Up

Exit the Mininet CLI:

```bash
exit
```

Clean up Mininet configurations:

```bash
sudo mn -c
```

Stop the Ryu controller by pressing:

```text
Ctrl + C
```

## Important Execution Notes

- Keep the Ryu controller running before starting the Mininet topology.
- Use separate terminals for the Ryu controller, Mininet and Open vSwitch commands.
- Commands such as `nodes`, `net`, `pingall` and `h1 ping h2` must be executed inside the Mininet CLI.
- Commands such as `ovs-ofctl` must be executed in the Ubuntu terminal.
- If Mininet reports that it cannot contact the remote controller, verify that Ryu is running and listening on port `6653`.
- The drop rule uses switch port 1 (`s1-eth1`), which is connected to host `h1` in this topology.

## Results and Observations

- Successfully configured the Ryu SDN Controller.
- Created a three-host, single-switch Mininet topology.
- Connected the virtual switch to the remote Ryu controller using OpenFlow 1.3.
- Verified host connectivity using `pingall` and individual ping commands.
- Inspected the OpenFlow flow table using `ovs-ofctl`.
- Added and removed a traffic-filtering drop rule.

## Conclusion

The experiment demonstrates the implementation of a basic Software-Defined Networking environment using Ryu, Mininet and Open vSwitch. It provides practical experience in controller configuration, network topology creation, host connectivity testing and OpenFlow flow-table management.

---

## Repository Structure

```text
Cloud-Computing-Lab/
│
├── Experiment-1/
│   └── Virtual Machine Setup and Configuration
│
├── Experiment-2/
│   └── VM Cloning and Network Connectivity
│
├── Experiment-3/
│   └── Mininet Network Topology Creation
│
└── Experiment-4/
    └── SDN Implementation Using Ryu and Mininet
```
# ☁️ Cloud Computing Lab 6
## Familiarization and Usage of Cloud Services Using AWS and Open-Source Cloud Tools

![Cloud Computing](https://img.shields.io/badge/Domain-Cloud%20Computing-blue)
![AWS](https://img.shields.io/badge/Cloud-AWS-orange)
![Ubuntu](https://img.shields.io/badge/OS-Ubuntu-E95420)
![VirtualBox](https://img.shields.io/badge/Virtualization-Oracle%20VirtualBox-blue)

## 📌 Aim

To become familiar with different cloud services and perform basic cloud operations using **Amazon Web Services (AWS), Ubuntu Linux, Oracle VirtualBox, and AWS Command Line Interface (CLI).**

## 🛠️ Technologies & Tools Used

- **Amazon Web Services (AWS)**
- Ubuntu Linux
- Oracle VirtualBox
- Amazon S3
- AWS IAM
- Amazon EC2
- Amazon VPC
- Amazon CloudWatch
- AWS CLI / AWS CloudShell

## 📚 Experiment Overview

This experiment is divided into four major practical tasks.

| Task | Practical Area | Description |
|---|---|---|
| 1 | Virtual Machine Setup | Install Ubuntu using Oracle VirtualBox and perform basic Linux operations. |
| 2 | Cloud Storage | Create an Amazon S3 bucket and perform file upload, download and deletion. |
| 3 | Cloud Service Exploration | Explore IAM, EC2 and VPC services through AWS Console. |
| 4 | Monitoring & CLI | Explore CloudWatch and execute basic AWS CLI commands. |

---

## 🖥️ Task 1: Virtual Machine Setup

**Objective:** Set up an Ubuntu virtual machine using Oracle VirtualBox.

### Steps Performed

1. Create a virtual machine in Oracle VirtualBox.
2. Install Ubuntu Linux.
3. Update the package lists and installed packages.
4. Install basic utilities.
5. Execute basic Linux terminal commands.

### Commands

```bash
sudo apt update
sudo apt upgrade -y
```

---

## 🪣 Task 2: Cloud Storage Using Amazon S3

**Objective:** Understand object storage and perform basic storage operations using Amazon S3.

Amazon S3 (Simple Storage Service) is an object storage service used to store and retrieve data over the internet.

### Steps Performed

1. Access the AWS Management Console.
2. Search for and open Amazon S3.
3. Create a globally unique S3 bucket.
4. Select the appropriate AWS Region.
5. Keep Block Public Access enabled.
6. Retain default encryption settings.
7. Create a sample text file in Ubuntu.
8. Upload the file to the S3 bucket.
9. Download the uploaded object.
10. Verify its contents and delete the test object and empty bucket.

### Create a Sample File

```bash
mkdir cloud-lab6
cd cloud-lab6

echo "Cloud Computing Lab Experiment 6" > lab-note.txt

cat lab-note.txt
```

### Expected Result

A private S3 bucket is created successfully, and a sample file is uploaded, downloaded, verified and deleted.

---

## 🔐 Task 3A: Identity and Access Management (IAM)

**Objective:** Understand how AWS manages access to cloud resources.

AWS IAM (Identity and Access Management) controls who can access AWS services and what actions they can perform.

### Concepts Explored

- **Users:** Identities representing users.
- **Groups:** Collections of IAM users.
- **Roles:** Identities that provide temporary permissions.
- **Policies:** Documents defining allowed or denied actions.

### Example IAM Policy

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "s3:ListBucket"
      ],
      "Resource": "arn:aws:s3:::example-bucket"
    }
  ]
}
```

**Principle of Least Privilege:** Every user should receive only the minimum permissions necessary to perform their assigned tasks.

---

## 💻 Task 3B: Virtual Machine Provisioning Using Amazon EC2

**Objective:** Explore the process of creating and managing cloud-based virtual machines.

Amazon EC2 (Elastic Compute Cloud) provides virtual servers hosted on AWS infrastructure.

### EC2 Components Explored

- Amazon Machine Images (AMIs)
- Instance Types
- Key Pair Configuration
- Networking
- Security Groups
- Storage Configuration

### Steps

1. Open the EC2 Dashboard.
2. Select Launch Instance.
3. Enter an instance name.
4. Explore available AMIs and instance types.
5. Review key pair configuration.
6. Explore networking and security groups.
7. Review storage configuration.

**Note:** Launching an EC2 instance is optional and should only be performed with instructor approval and after checking the account's applicable pricing and eligibility.

---

## 🌐 Task 3C: Virtual Networking Using Amazon VPC

**Objective:** Understand virtual networking and its components in AWS.

Amazon VPC (Virtual Private Cloud) provides a logically isolated virtual network within AWS.

### VPC Components Explored

- VPC
- Public Subnets
- Private Subnets
- Route Tables
- Internet Gateways
- Security Groups

### Network Architecture

A typical AWS network architecture consists of a VPC containing public and private subnets, route tables, internet gateways and security groups.

A public subnet can provide internet connectivity when routing and security configurations permit it. A private subnet generally does not have a direct route to an internet gateway.

---

## 📊 Task 3D: Cloud Monitoring Using Amazon CloudWatch

**Objective:** Understand cloud resource monitoring and performance observation.

Amazon CloudWatch is a monitoring and observability service that collects and displays metrics, logs and monitoring information.

### Activities

1. Open the CloudWatch Dashboard.
2. Explore the Metrics section.
3. Identify metrics organised by AWS services.
4. Observe metric dimensions.
5. Explore the Alarms section.
6. Understand threshold-based alarm configuration.

**Example:** An alarm can notify an administrator when EC2 CPU utilisation exceeds a specified threshold for a defined period.

---

## ⌨️ Task 4: Basic AWS Operations Using AWS CLI

**Objective:** Perform AWS cloud operations through command-line instructions.

AWS CLI allows users to interact with AWS services directly from a terminal.

### 1. Verify AWS CLI Installation

```bash
aws --version
```

### 2. Verify AWS Account Identity

```bash
aws sts get-caller-identity
```

### 3. List Available S3 Buckets

```bash
aws s3 ls
```

### 4. Create a Local Sample File

```bash
mkdir cloud-lab6-cli
cd cloud-lab6-cli

echo "AWS CLI Cloud Storage Test" > sample.txt
```

### 5. Upload File to S3

```bash
aws s3 cp sample.txt s3://YOUR-BUCKET-NAME/sample.txt
```

### 6. List Objects in the Bucket

```bash
aws s3 ls s3://YOUR-BUCKET-NAME/
```

### 7. Download the File

```bash
aws s3 cp s3://YOUR-BUCKET-NAME/sample.txt downloaded.txt
```

### 8. Verify Downloaded File

```bash
cat downloaded.txt
```

### 9. Delete the Test Object

```bash
aws s3 rm s3://YOUR-BUCKET-NAME/sample.txt
```

Replace `YOUR-BUCKET-NAME` with the actual S3 bucket name.

---

## 🔒 Security & Cost Management

The following precautions should be followed during the experiment:

- Use only an authorised AWS account.
- Never share passwords, secret access keys or private keys.
- Avoid using the root account for routine operations.
- Enable Multi-Factor Authentication (MFA) wherever possible.
- Keep S3 Block Public Access enabled.
- Follow the principle of least privilege.
- Check applicable AWS pricing, credits and account eligibility before creating resources.
- Do not launch EC2 instances without instructor approval.
- Terminate unused instances and remove unnecessary resources.
- Delete temporary S3 objects and buckets after the practical.
- Review the AWS Billing Dashboard after completing the experiment.

**Important:** AWS Free Tier does not mean that every service or configuration is automatically free. Charges may depend on the account plan, Region, instance type, storage and applicable offers.

---

## 🎯 Learning Outcomes

After completing this experiment, students will be able to:

1. Set up and operate an Ubuntu virtual machine using VirtualBox.
2. Understand cloud storage using Amazon S3.
3. Perform basic file upload, download and deletion operations.
4. Understand identity and access management using AWS IAM.
5. Explore cloud-based virtual machines using Amazon EC2.
6. Understand virtual networking through Amazon VPC.
7. Explore cloud monitoring using Amazon CloudWatch.
8. Execute basic cloud storage operations using AWS CLI.

## 📸 Practical Screenshots

Screenshots demonstrating the practical implementation and command outputs are included in the repository's experiment documentation.

---

## 📖 Conclusion

This experiment provides practical exposure to cloud computing concepts and AWS services. It demonstrates how virtual machines, object storage, identity management, networking, monitoring and command-line tools can be used to understand and manage cloud infrastructure.

---
# ☁️ Cloud Computing Lab 7
## Familiarization and Usage of Collaborative Applications (SaaS)

![Cloud Computing](https://img.shields.io/badge/Domain-Cloud%20Computing-blue)
![SaaS](https://img.shields.io/badge/Cloud%20Model-SaaS-green)
![Google Workspace](https://img.shields.io/badge/Platform-Google%20Workspace-4285F4)

## 📌 Aim

To understand the Software as a Service (SaaS) cloud delivery model and demonstrate web-based applications for document creation, spreadsheet management, presentation creation, online meetings and real-time collaboration.

## 🛠️ Applications Used

- Google Docs
- Google Sheets
- Google Slides
- Google Meet
- Google Drive
- Web Browser
- Internet Connection

## 📚 Introduction

**Software as a Service (SaaS)** is a cloud-based software delivery model in which applications are hosted by a service provider and accessed through the internet.

Users can access software through a web browser without installing or managing the underlying infrastructure locally.

## 🧪 Practical Implementation

### 1. Google Docs – Collaborative Document Editing

**Objective:** Create, edit and share a document using Google Docs.

**Activities Performed:**

1. Open Google Docs.
2. Create a new document titled `Cloud Computing Lab 7 – Collaborative Document`.
3. Add an introduction to SaaS and its features.
4. Create and format a table.
5. Share the document with another Google account.
6. Assign Editor permissions.
7. Perform collaborative editing.
8. Add comments and explore Version History.

**Concepts Observed:**
- Online document editing
- Real-time collaboration
- Sharing permissions
- Comments and version history
- Automatic cloud saving

### 2. Google Sheets – Cloud-Based Spreadsheet Management

**Objective:** Create and manage a spreadsheet using Google Sheets.

**Activities Performed:**

1. Create a spreadsheet titled `Cloud Computing Lab 7 – Collaborative Spreadsheet`.
2. Enter student details and marks.
3. Organise data using rows and columns.
4. Apply spreadsheet formulas.
5. Share the spreadsheet with a collaborator.
6. Observe collaborative editing and comments.

**Sample Dataset:**

| Student ID | Name | Subject | Marks |
|---|---|---|---:|
| S101 | Student A | Cloud Computing | 82 |
| S102 | Student B | Cloud Computing | 75 |
| S103 | Student C | Cloud Computing | 91 |
| S104 | Student D | Cloud Computing | 68 |
| S105 | Student E | Cloud Computing | 87 |

**Formulas Used:**

```excel
=SUM(D3:D7)
=AVERAGE(D3:D7)
=MAX(D3:D7)
=MIN(D3:D7)
```

**Calculated Results:**

| Operation | Result |
|---|---:|
| Total Marks | 403 |
| Average Marks | 80.6 |
| Highest Marks | 91 |
| Lowest Marks | 68 |

### 3. Google Slides – Cloud-Based Presentation

**Objective:** Create, edit and share a presentation using Google Slides.

**Activities Performed:**

1. Create a presentation titled `Software as a Service (SaaS)`.
2. Create four slides.
3. Add an introduction to SaaS.
4. Include examples of SaaS applications.
5. Describe the advantages of SaaS.
6. Format slide content using the toolbar.
7. Share the presentation with another Google account.
8. Assign Editor permissions.
9. Observe collaborative slide editing and comments.

**Topics Covered in the Presentation:**
- Introduction to SaaS
- What is SaaS?
- Examples: Google Docs, Google Sheets, Microsoft 365, Microsoft Teams and Salesforce
- Advantages of SaaS

### 4. Google Meet – Online Meeting and Communication

**Objective:** Explore online meeting creation and communication using Google Meet.

**Activities Performed:**

1. Open Google Meet through a web browser.
2. Select the New Meeting option.
3. Generate a meeting link.
4. View the meeting joining information.
5. Copy and explore the meeting link.
6. Explore the meeting interface and available controls.
7. Observe the meeting dashboard.

**Concepts Observed:**
- Online video conferencing
- Meeting link generation
- Remote communication
- Internet-based collaboration

---

## ⭐ Key Features of SaaS Observed

- **Internet-Based Accessibility:** Applications can be accessed through the internet.
- **Real-Time Collaboration:** Multiple users can work on shared files.
- **Automatic Updates:** Software updates are managed by the service provider.
- **Cloud Storage:** Data is stored and accessed through cloud infrastructure.
- **Reduced Maintenance:** Users do not manage the underlying servers or infrastructure.
- **Scalability:** Access and usage can be expanded according to requirements.

## 🎯 Learning Outcomes

After completing this experiment, students will be able to:

1. Understand the Software as a Service (SaaS) model.
2. Create and edit cloud-based documents using Google Docs.
3. Perform calculations and manage data using Google Sheets.
4. Design and share presentations using Google Slides.
5. Generate online meeting links using Google Meet.
6. Understand real-time collaboration and cloud-based sharing.
7. Explore document comments, sharing permissions and version history.

## 📸 Practical Screenshots

Screenshots documenting the practical implementation of Google Docs, Google Sheets, Google Slides and Google Meet are included in the experiment report.

## ✅ Result

The SaaS model was successfully studied through practical demonstrations of Google Docs, Google Sheets, Google Slides and Google Meet. Document editing, spreadsheet calculations, presentation creation, online meeting generation and collaborative sharing features were explored.

## 📝 Conclusion

This experiment demonstrated how Software as a Service applications provide ready-to-use software over the internet. Google Workspace applications simplify document management, data processing, presentation creation and online communication while enabling real-time collaboration without requiring users to manage the underlying infrastructure.

---
# ☁️ Cloud Computing Lab 8
## Implementing Applications using Google App Engine (PaaS)

![Cloud Computing](https://img.shields.io/badge/Domain-Cloud%20Computing-blue)
![PaaS](https://img.shields.io/badge/Cloud%20Model-PaaS-green)
![Python](https://img.shields.io/badge/Language-Python-3776AB)
![Flask](https://img.shields.io/badge/Framework-Flask-black)
![Google Cloud](https://img.shields.io/badge/Platform-Google%20Cloud-4285F4)

## 📌 Aim

To become familiar with Platform as a Service (PaaS) and implement, deploy and manage a simple web application using Google App Engine.

## 🛠️ Technologies & Tools Used

- Google Cloud Platform (GCP)
- Google App Engine
- Python
- Flask Framework
- Google Cloud CLI (`gcloud`)
- Ubuntu Linux
- Terminal
- Web Browser

## 📚 Introduction

**Platform as a Service (PaaS)** is a cloud computing service model that provides a platform for developing, running and managing applications without requiring users to manage the underlying infrastructure.

Google App Engine is a fully managed PaaS platform provided by Google Cloud. It allows developers to deploy applications while Google manages the infrastructure, scaling and application environment.

## 🧪 Experiment Overview

This experiment is divided into four practical tasks.

| Task | Practical Area | Description |
|---|---|---|
| 1 | PaaS and App Engine Setup | Create a Google Cloud project and configure App Engine. |
| 2 | Web Application Development | Develop a simple Flask application locally. |
| 3 | Google Cloud CLI Setup | Install and configure the Google Cloud CLI. |
| 4 | Deployment and Management | Deploy the application and explore versions, logs, instances and monitoring. |

---

## ☁️ Task 1: PaaS and Google App Engine Setup

**Objective:** Understand PaaS and configure a Google Cloud project for App Engine.

### Steps Performed

1. Open Google Cloud Console.
2. Sign in using a Google account.
3. Create a new project named `Cloud-Lab8`.
4. Open the App Engine Dashboard.
5. Explore the App Engine interface and available services.
6. Enable the App Engine Admin API.

### Project Details

| Property | Value |
|---|---|
| Project Name | Cloud-Lab8 |
| Project ID | `cloud-lab8-514907` |
| Cloud Platform | Google Cloud Platform |
| PaaS Service | Google App Engine |

### Enable App Engine Admin API

```bash
gcloud services enable appengine.googleapis.com
```

Verify enabled services:

```bash
gcloud services list --enabled
```

---

## 🐍 Task 2: Develop a Simple Web Application Using Flask

**Objective:** Develop and run a simple Python web application locally.

### Step 1: Create the Project Directory

```bash
mkdir cloud-lab8
cd cloud-lab8
```

### Step 2: Create `main.py`

```python
from flask import Flask

app = Flask(__name__)

@app.route("/")
def home():
    return """
    <h1>Cloud Computing Lab 8</h1>
    <p>Application successfully implemented using Google App Engine.</p>
    <p>This application demonstrates Platform as a Service (PaaS).</p>
    """

if __name__ == "__main__":
    app.run(host="127.0.0.1", port=8080)
```

### Step 3: Create `requirements.txt`

```text
Flask
```

### Step 4: Create and Activate a Virtual Environment

```bash
python3 -m venv venv
source venv/bin/activate
```

### Step 5: Install Dependencies

```bash
pip install -r requirements.txt
```

### Step 6: Run the Flask Application

```bash
python main.py
```

### Step 7: Access the Application

Open the following URL in a web browser:

```text
http://127.0.0.1:8080
```

**Expected Output:**

The browser displays:

- Cloud Computing Lab 8
- Application successfully implemented using Google App Engine.
- This application demonstrates Platform as a Service (PaaS).

---

## ⚙️ Task 3: Google Cloud CLI Installation and Configuration

**Objective:** Install and configure Google Cloud CLI to interact with Google Cloud services through the terminal.

### Step 1: Install Google Cloud CLI

Update the Ubuntu package lists:

```bash
sudo apt-get update
```

Install the required utilities:

```bash
sudo apt-get install ca-certificates gnupg curl -y
```

Add the Google Cloud package signing key:

```bash
curl https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo gpg --dearmor -o /usr/share/keyrings/cloud.google.gpg
```

Add the Google Cloud CLI repository:

```bash
echo "deb [signed-by=/usr/share/keyrings/cloud.google.gpg] https://packages.cloud.google.com/apt cloud-sdk main" | sudo tee -a /etc/apt/sources.list.d/google-cloud-sdk.list
```

Update the package list and install Google Cloud CLI:

```bash
sudo apt-get update
sudo apt-get install google-cloud-cli -y
```

### Step 2: Verify Installation

```bash
gcloud --version
```

### Step 3: Authenticate Google Cloud CLI

```bash
gcloud auth login
```

Complete the authentication process through the browser.

### Step 4: List Google Cloud Projects

```bash
gcloud projects list
```

### Step 5: Select the Project

```bash
gcloud config set project cloud-lab8-514907
```

Verify the selected project:

```bash
gcloud config get-value project
```

### Step 6: Create `app.yaml`

Create the App Engine configuration file:

```bash
nano app.yaml
```

Add the following configuration:

```yaml
runtime: python312
```

Save and verify:

```bash
cat app.yaml
```

---

## 🚀 Task 4: Application Deployment and Management

**Objective:** Deploy the Flask application using Google App Engine and explore application management features.

### Step 1: Create the App Engine Application

Open Google Cloud Console and navigate to the App Engine Dashboard.

Select the appropriate App Engine region according to the lab requirements.

**Note:** The region selected during App Engine application creation is generally permanent and cannot be changed later.

### Step 2: Deploy the Application

After App Engine application creation and billing prerequisites are satisfied, execute:

```bash
gcloud app deploy
```

Confirm the deployment when prompted.

### Step 3: Open the Deployed Application

```bash
gcloud app browse
```

The application should open through its Google App Engine URL.

### Step 4: List Application Versions

```bash
gcloud app versions list
```

This command displays the deployed application versions.

### Step 5: View Application Logs

```bash
gcloud app logs tail
```

This command allows users to observe application logs.

### Step 6: Update the Application

Modify the message in `main.py`, for example:

```python
<p>Welcome to Cloud Computing Lab 8 - Version 2!</p>
```

Deploy the updated application again:

```bash
gcloud app deploy
```

### Step 7: Explore App Engine Management Features

Explore the following sections in Google Cloud Console:

- Services
- Versions
- Instances
- Logs
- Monitoring
- Traffic Management

---

## 📊 Important Concepts

| Concept | Description |
|---|---|
| PaaS | Provides a managed platform for application development and deployment. |
| Google App Engine | Managed application hosting service in Google Cloud. |
| Flask | Lightweight Python web framework. |
| `gcloud` CLI | Command-line tool for managing Google Cloud resources. |
| `app.yaml` | Configuration file specifying App Engine runtime settings. |
| Application Versions | Different deployed versions of an application. |
| Application Logs | Records of application activity and events. |

## 🔒 Billing and Cost Considerations

- Google Cloud billing may be required to create and deploy an App Engine application.
- Check the applicable pricing and free usage limits before enabling billing.
- Do not add a payment method without authorisation.
- Monitor cloud resource usage and billing information.
- Use an authorised Google Cloud account.

**Practical Note:** The local Flask application can be developed and tested without deploying it to Google Cloud. Actual App Engine deployment requires the necessary project configuration and billing eligibility.

## 🎯 Learning Outcomes

After completing this experiment, students will be able to:

1. Understand the Platform as a Service (PaaS) model.
2. Familiarise themselves with Google App Engine.
3. Develop a basic web application using Python and Flask.
4. Configure a Python virtual environment and install dependencies.
5. Install and authenticate Google Cloud CLI.
6. Configure a Google Cloud project and App Engine runtime.
7. Understand the application deployment process.
8. Explore application versions, logs, instances and monitoring.

## 📸 Practical Screenshots

Screenshots documenting the experiment include:

- Google Cloud project creation
- App Engine Dashboard
- Google Cloud CLI installation
- Project authentication and configuration
- Flask application development
- Localhost application execution
- `app.yaml` configuration
- App Engine API activation
- Deployment and management activities, where completed

## ✅ Result

A simple Flask web application was developed and successfully executed in the local Ubuntu environment. Google Cloud project configuration, Google Cloud CLI authentication, App Engine Admin API activation and application configuration were also performed.

Actual App Engine deployment remains subject to billing activation and successful application creation.

## 📝 Conclusion

This experiment provided practical exposure to the Platform as a Service (PaaS) model using Google App Engine. A basic web application was developed using Flask and tested locally. Google Cloud CLI was installed and configured to interact with Google Cloud resources. The experiment helped demonstrate how managed cloud platforms simplify application development, configuration, deployment and management.

---

## Author

**Debasmita Bose**

Cloud Computing Laboratory
