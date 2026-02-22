# Day 02 – Linux Architecture, Processes, and systemd

## Task
Today’s goal is to **understand how Linux works under the hood**.

You will create a short note that explains:
- The core components of Linux (kernel, user space, init/systemd)
- How processes are created and managed
- What systemd does and why it matters
---
##Solution

1. What is Kernel?

A kernel is a computer program that functions as the beating heart of the OS, the system that allows users to interact with the computer’s hardware and software. 
What it does
Process management (CPU scheduling)
- Memory management
- Device drivers
- File systems
- Networking
- Security (permissions, SELinux/AppArmor hooks)
  
---

2. What is user space?
User space is the memory area where application software, daemons, and some drivers execute, typically with one address space per process.

DevOps relevance
- Everything you deploy runs in user space
- Containers = isolated user-space environments
- Permissions and security are enforced here
  
---

3. What is init/systemd?
The first process started by the kernel(PI = 1)

###What it does
- Starts and manages system services
- Handles boot sequence
- Manages service dependencies
- Restarts failed services
- Controls system state (shutdown, reboot)

Why does it matter?
Init/systemd matters because it starts, manages, monitors, and recovers system services after boot. Without it, Linux would not run applications reliably

---

5. How process are managed?
Processes are typically created via the fork() and exec() mechanism,The OS Scheduler manages their transitions between Ready, Running, and Waiting states to ensure CPU efficiency and multitasking.

6. List 5 commands that you would use?
Ls -l , cd, systemctl, grep,top



