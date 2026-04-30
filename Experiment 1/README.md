# 🖥️ Experiment 1 — Linux Setup Using Virtual Machine (VirtualBox / VMware)

> **Course:** Introduction to Linux with Bash Scripting Lab  
> **Instructor:** Dr. Rajesh Kumar  
> **CO Mapped:** CO1 — Familiarity with Linux environment, system setup, and basic system operations

---

## 🎯 Learning Outcomes

After completing this experiment, you will be able to:

- **LO1:** Understand the concept of virtualization and virtual machines
- **LO2:** Install Oracle VirtualBox or VMware on a host operating system
- **LO3:** Import and configure a Linux OS using an OVA file
- **LO4:** Verify successful Linux installation and system readiness

---

## 📖 Theory

### Linux Operating System
Linux is an open-source, Unix-like OS widely used in servers, cloud platforms, DevOps pipelines, and cybersecurity environments. Its robust permission model, command-line utilities, and scripting capabilities make it an industry-preferred OS.

### Virtualization
Virtualization enables multiple operating systems (guest OS) to run on a single physical machine (host OS) by abstracting hardware resources such as CPU, memory, storage, and networking — providing isolation, flexibility, and efficient resource utilization.

### VirtualBox vs VMware

| Feature | Oracle VirtualBox | VMware Workstation |
|---|---|---|
| License | Open-source (Free) | Commercial (Pro) / Free (Player) |
| Best for | Academic / Learning | Professional use |
| Performance | Good | High |
| Networking | Supported | Advanced |

### OVA File
An **OVA (Open Virtual Appliance)** is a pre-configured VM package containing:
- Guest operating system
- Virtual disk image
- Hardware configuration

Using an OVA eliminates manual Linux installation steps — just import and run.

---

## ⚙️ System Requirements

| Component | Minimum | Recommended |
|---|---|---|
| RAM | 4 GB | 8 GB |
| Free Disk Space | 20 GB | 40 GB |
| Host OS | Windows / Linux / macOS | — |
| BIOS Setting | Virtualization enabled | — |

**Software needed:**
- Oracle VirtualBox → https://www.virtualbox.org  
  **or** VMware Workstation Player/Pro
- Linux OVA file *(provided by instructor)*

---

## 🚀 Procedure

### Option A — Oracle VirtualBox

```
1. Download and install VirtualBox from https://www.virtualbox.org
2. Launch VirtualBox Manager
3. Click:  File → Import Appliance
4. Select the provided Linux OVA file
5. Review VM settings (RAM, CPU, storage)
6. Click Import to create the virtual machine
7. Start the virtual machine
8. Log in and verify Linux boots successfully
```

### Option B — VMware Workstation

```
1. Install VMware Workstation Player or Pro on the host system
2. Launch VMware Workstation
3. Select: Open a Virtual Machine
4. Browse and select the provided Linux OVA file
5. Allow VMware to import and convert the appliance
6. Review and adjust hardware settings if required
7. Power on the virtual machine
8. Log in and verify Linux boots successfully
```

> 💡 **Note:** This is an installation-based experiment. No Linux terminal commands are required.

---

## ✅ Expected Output

- Linux OS boots successfully inside VirtualBox or VMware
- Desktop or terminal interface is accessible
- Virtual machine is ready for executing Linux commands and Bash scripts

---

## 📸 Submission Requirements

Attach screenshots of:
- [ ] VM import screen (OVA file selection)
- [ ] Linux running successfully inside the VM

---

## 📝 Result

The Linux operating system was successfully installed and configured using VirtualBox or VMware Workstation with an OVA file. The virtualized Linux environment is now ready for performing Linux and Bash scripting experiments.
