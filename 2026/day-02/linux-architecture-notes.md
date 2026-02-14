1️⃣ Core Components of Linux
🔹 Kernel

The kernel is the core of the Linux operating system. It directly interacts with hardware and manages:

CPU

Memory

Disk

Devices

Process scheduling

It acts as a bridge between hardware and user applications.

🔹 User Space

User space is where:

Applications run

Shell (bash) runs

User programs execute

It does not directly access hardware. Instead, it communicates with the kernel through system calls.

🔹 Init / systemd

init (old systems) or systemd (modern systems) is the first process started by the kernel (PID 1).

It is responsible for:

Starting system services

2️⃣ How Processes Are Created and Managed

Every running program in Linux is a process

Each process has a unique PID (Process ID)

A new process is created using:

fork() → creates a copy of the parent process

exec() → loads a new program into the process

The kernel manages:

CPU allocation (scheduling)

Memory allocation

Process states (running, sleeping, stopped, zombie)

Useful commands:

ps → view processes

top / htop → monitor processes


3️⃣ What systemd Does & Why It Matters

systemd is a modern init system used in most Linux distributions.

It:

Starts services in parallel (faster boot)

Manages services (start, stop, restart)

Tracks dependencies between services

Handles logging (via journald)

Example:

systemctl start nginx
systemctl stop docker
systemctl status sshd

Managing background processes

Handling system startup and shutdown




In Linux, every program running is a process, and each process moves between different states depending on what it’s doing.

You can check process states using:

ps aux


or

top



1️⃣ Running (R)

The process is either:

Currently executing on the CPU

Or waiting in the run queue to get CPU time

👉 Example:

A script executing

A server handling requests

State code: R


2️⃣ Sleeping (S)

The process is waiting for something to happen (like input/output).

Two types:

🔹 Interruptible Sleep (S)

Waiting for I/O (disk, network, user input)

Can be interrupted by signals

👉 Example:

Web server waiting for incoming request

State code: S


Uninterruptible Sleep (D)

Waiting for I/O (usually disk)

Cannot be interrupted easily

👉 Example:

Process stuck waiting for disk read

State code: D

In DevOps, many D-state processes may indicate disk issues.


3️⃣ Stopped (T)

Process execution is paused

Usually stopped manually or by debugger

Example:

Ctrl + Z


State code: T




**5 Linux Commands Used Daily (DevOps Perspective)**
1️⃣ ls

Purpose: List files and directories

Used to check:

Deployment folders

Config files

Log directories

Example:

ls -la

2️⃣ cd

Purpose: Change directory

Used constantly to navigate:

/var/log

/etc

Application directories

Example:

cd /var/log

3️⃣ ps

Purpose: View running processes

Used to:

Check if service is running

Identify high CPU processes

Example:

ps aux | grep nginx

4️⃣ top

Purpose: Real-time system monitoring

Used to check:

CPU usage

Memory usage

Running processes

Very important during production issues.

5️⃣ systemctl

Purpose: Manage services (systemd systems)

Used to:

Start/stop services

Restart applications

Check service status

Example:

systemctl status nginx
systemctl restart docker
