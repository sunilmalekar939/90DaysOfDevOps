# DAY 2 – Linux Basics Notes

## Copy Command
- Command to copy a file:
cp <sourcefile> <destfile>

- To copy a directory, use `-r` (recursive):
cp -r <sourcedir> <destdir>


### Important Note
- Linux shows **error messages** if a command is wrong or incomplete.
- Always **read CLI error messages carefully**.

**Example error:**
cp: -r not specified
---

## Process Information
- Everything running on a Linux node is called a **process**.
- To find a specific running process:
ps aux | grep <keyword>

- Using the **PID**, a process can be stopped or killed.---

## Process States

### Running
- Actively using CPU or waiting for CPU time.

### Sleeping
#### Interruptible Sleep
- Waiting for a simple task.
- Can be started or stopped.

#### Uninterruptible Sleep
- Waiting for a critical task.
- Cannot be killed until the task completes.

### Stopped
- Process stopped manually using:
Ctrl + Z

### Zombie
- Appears in process table.
- Does not use CPU or memory.

## systemd
- `systemd` is the **first process** started after the kernel boots.
- It is assigned: PID 1

