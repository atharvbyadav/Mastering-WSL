# **Mastering WSL (Windows Subsystem for Linux)**
*A Beginner-Friendly Guide to Using WSL on Windows*

---

## Table of Contents

1. [Introduction & Getting Started](#part-1-introduction--getting-started)  
2. [Managing WSL Distros & Configuration](#part-2-managing-wsl-distros-and-system-configuration)  
3. [File Access, Interoperability & Advanced Tips](#part-3-interoperability-file-access--advanced-wsl-configuration)

---

## **Part 1: Introduction & Getting Started**

### **What is WSL?**
WSL (Windows Subsystem for Linux) is a compatibility layer developed by Microsoft that allows you to run a GNU/Linux environment directly on Windows—without the need for a traditional virtual machine or dual-boot setup.

This means you can run Linux commands, tools, and applications alongside your Windows software, all on the same computer.

---

### **Why Use WSL?**
- Run **Linux development tools** (e.g., `bash`, `gcc`, `apt`, `git`) natively on Windows.
- Use **both Windows and Linux applications** side-by-side.
- Avoid using heavy virtual machines or dual-booting.
- Ideal for web development, system administration, scripting, and learning Linux.

---

### **WSL Versions**
- **WSL 1**: Lightweight and fast, but doesn’t offer full system call compatibility.
- **WSL 2**: Uses a real Linux kernel with better performance and compatibility (recommended).

---

## **Installing WSL (The Easy Way)**

### **Step-by-Step Installation**
#### For Windows 10 (2004+) or Windows 11:

1. Open **PowerShell as Administrator**.
2. Run the following command:
   ```bash
   wsl --install
   ```
   - This installs WSL and sets **WSL 2** as the default version.
   - It also installs **Ubuntu** as the default Linux distribution.

3. **Restart your computer** if prompted.
4. On reboot, a terminal window will launch asking you to set up your **Linux username and password**.

---

### **Installing a Specific Linux Distro**
If you want a different distribution (like Debian, Kali Linux, etc.), run:
```bash
wsl --install -d <DistroName>
```

#### Example:
```bash
wsl --install -d Debian
```

---

### **Checking Installed Distros**
```bash
wsl --list --online
```
This shows all available distros you can install.

---

### **Switching Between WSL Versions**
By default, WSL uses version 2. To manually switch a distro’s version:
```bash
wsl --set-version <DistroName> 2
```

#### Example:
```bash
wsl --set-version Ubuntu 2
```

---

### **Setting Default Version for New Installs**
```bash
wsl --set-default-version 2
```

---

## **Using WSL for the First Time**
To launch your installed Linux distro:
```bash
wsl
```

Or to launch a specific one:
```bash
wsl -d <DistroName>
```

---

## **Useful First Commands (Inside WSL Terminal)**

| Command | Description |
|---------|-------------|
| `ls` | Lists files in the current directory. |
| `cd` | Changes directory. |
| `pwd` | Prints the current directory path. |
| `mkdir <dir>` | Creates a new directory. |
| `sudo apt update && sudo apt upgrade` | Updates your Linux packages. |
| `exit` | Exits the WSL terminal and returns to Windows. |

---

### **Accessing Windows Files from WSL**
Your C: drive is mounted inside WSL at `/mnt/c`. You can access any file using:
```bash
cd /mnt/c/Users/<YourWindowsUsername>/
```

---

### **Accessing WSL Files from Windows**
Open File Explorer and type:
```
\\wsl$
```
You’ll see all installed Linux distributions and their file systems.

---