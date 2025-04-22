# **Mastering WSL (Windows Subsystem for Linux)**
*A Beginner-Friendly Guide to Using WSL on Windows*
---
<p align="center">
  <img src="https://raw.githubusercontent.com/atharvbyadav/Mastering-WSL/main/banner.png" alt="Mastering WSL" width="600" />
</p>

## 🔗 **Repository**
[**Mastering-WSL by @atharvbyadav**](https://github.com/atharvbyadav/Mastering-WSL)

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
- **WSL 1**: Lightweight and fast, but doesn't offer full system call compatibility.
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
By default, WSL uses version 2. To manually switch a distro's version:
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
You'll see all installed Linux distributions and their file systems.

---

# **Part 2: Managing WSL Distros and System Configuration**

In this section, you'll learn how to manage your installed Linux distributions on WSL and customize your setup. Perfect for keeping things clean, organized, and optimized!

---

## **1. Listing Installed Distros**

To see all the Linux distributions you have installed:

```bash
wsl --list
```
or
```bash
wsl -l
```

### Example Output:
```
Windows Subsystem for Linux Distributions:
Ubuntu (Default)
Debian
Kali-Linux
```

To see which ones are currently **running**:

```bash
wsl --list --running
```

To see versions (WSL 1 or 2) of each installed distro:

```bash
wsl -l -v
```

---

## **2. Setting a Default Distro**

If you use one distro more than others, make it the default:

```bash
wsl --set-default <DistroName>
```

### Example:
```bash
wsl --set-default Debian
```

Now, running just `wsl` will launch Debian.

---

## **3. Uninstalling a Distro**

To remove (unregister) a distro and **delete all its data**:

```bash
wsl --unregister <DistroName>
```

### Example:
```bash
wsl --unregister Ubuntu
```

> **Warning:** This permanently deletes the Linux file system for that distro!

---

## **4. Exporting and Backing Up a Distro**

To create a backup of your entire Linux distro:

```bash
wsl --export <DistroName> <PathToFile.tar>
```

### Example:
```bash
wsl --export Ubuntu ubuntu-backup.tar
```

This file can be stored and later restored.

---

## **5. Importing a Distro from Backup**

To import your saved distro to a new location:

```bash
wsl --import <NewDistroName> <InstallLocation> <BackupFile.tar>
```

### Example:
```bash
wsl --import UbuntuBackup C:\WSL\Ubuntu\ ubuntu-backup.tar
```

---

## **6. Changing WSL Version (1 or 2)**

You can choose which version each distro uses:

```bash
wsl --set-version <DistroName> <1|2>
```

### Example:
```bash
wsl --set-version Kali-Linux 2
```

To set **WSL 2** as the default for all new installs:

```bash
wsl --set-default-version 2
```

---

## **7. Shutting Down and Terminating**

- **Shut down all WSL instances:**
  ```bash
  wsl --shutdown
  ```

- **Terminate a specific distro:**
  ```bash
  wsl --terminate <DistroName>
  ```

This is useful if something hangs or you want to free up resources.

---

## **8. Checking System Configuration**

Run this to see:
- Default distro
- Default version
- Kernel version
- Whether WSL is running

```bash
wsl --status
```

---

## **9. Updating the WSL Kernel**

Microsoft occasionally updates the WSL 2 kernel. To update:

```bash
wsl --update
```

If something breaks and you want to roll back:

```bash
wsl --update rollback
```

---

## **10. Full Help Command**

To see everything WSL can do, use:

```bash
wsl --help
```

This gives a list of all commands and options.

---

Here's **Part 3** of your complete WSL README guide — focused on **interoperability, file system access, and advanced configuration**.

---

# **Part 3: Interoperability, File Access & Advanced WSL Configuration**

---

## **1. Accessing Windows Files from Linux (WSL)**

Inside your WSL terminal, Windows drives are mounted under `/mnt/`.

### Examples:
| Action | Command |
|--------|---------|
| Navigate to `C:\Users\YourName\Downloads` | `cd /mnt/c/Users/YourName/Downloads` |
| List contents of D: drive | `ls /mnt/d` |

---

## **2. Accessing WSL Files from Windows**

To explore your WSL file system through Windows File Explorer:

1. Press `Win + R`
2. Type:  
   ```
   \\wsl$
   ```
3. Hit Enter

This opens a network-style view of all installed Linux distros. You can drag/drop files in and out from here.

---

## **3. Running Linux Commands from Windows (PowerShell or CMD)**

You can execute Linux commands directly from a Windows terminal using:

```bash
wsl <linux-command>
```

### Examples:
```bash
wsl ls -la
wsl cat /etc/os-release
```

To run a Linux command in a specific distro:
```bash
wsl -d <DistroName> <command>
```

---

## **4. Running Windows Programs from Linux (WSL)**

Inside WSL, you can launch Windows apps using their `.exe` names.

### Examples:
```bash
notepad.exe
code.exe            # Opens VS Code
explorer.exe .      # Opens current directory in File Explorer
```

You can also use Windows paths in commands, just prefix them with `/mnt/`:

```bash
cat /mnt/c/Users/YourName/Desktop/note.txt
```

---

## **5. Advanced Configuration Files**

WSL supports two config files for custom behavior:

---

### **A. Global Config: `.wslconfig`**
Location:  
`C:\Users\<YourWindowsUsername>\.wslconfig`

This file affects **all WSL 2** distributions.

#### Example `.wslconfig`:
```ini
[wsl2]
memory=4GB
processors=2
swap=2GB
localhostForwarding=true
```

| Option | Description |
|--------|-------------|
| `memory` | Max RAM WSL can use |
| `processors` | Number of CPU cores |
| `swap` | Swap file size |
| `localhostForwarding` | Enables Windows to Linux networking |

> After editing this file, restart WSL:
```bash
wsl --shutdown
```

---

### **B. Per-Distro Config: `wsl.conf`**
Location:  
Inside each distro at `/etc/wsl.conf`

#### Example `wsl.conf`:
```ini
[automount]
enabled = true
root = /mnt/
options = "metadata,umask=22,fmask=11"

[network]
generateResolvConf = false
```

This file controls:
- How drives are mounted
- File permission behavior
- Network settings

> Restart the WSL distro after editing this config.

---

## **6. Tips & Best Practices**

- **Use WSL 2** unless you have specific needs for WSL 1.
- **Keep backups** of your important Linux distros using `--export`.
- Use **VS Code with WSL** (`code .`) for full-featured Linux dev on Windows.
- Run `sudo apt update && sudo apt upgrade` frequently to keep Linux packages updated.
- Avoid editing Linux files using Windows tools directly (use `/mnt/` instead).

---

## **7. Troubleshooting Common Issues**

| Problem | Solution |
|--------|----------|
| WSL not launching | Restart computer or run `wsl --shutdown` |
| File permission errors | Check mount options in `wsl.conf` |
| Can't access Windows files | Try navigating to `/mnt/c/Users/` |
| WSL commands not recognized | Make sure Windows features are enabled (see Part 1) |

---

## **Want More?**

- [Official WSL Docs](https://learn.microsoft.com/en-us/windows/wsl/)
- [WSL GitHub Repo](https://github.com/microsoft/WSL)
- [WSL Issues & Discussions](https://github.com/microsoft/WSL/issues)

---

## **Conclusion**

You've now mastered:
- Installing and launching WSL
- Managing multiple distros
- Running commands across Linux and Windows
- Configuring WSL to match your system and workflow

This guide is made to be saved, starred and shared. Happy coding!

---

## Made with love for learners & devs.

---
