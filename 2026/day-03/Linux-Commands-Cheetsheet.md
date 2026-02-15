1️⃣ Process Management
🔹 ps aux

Shows all running processes with user, CPU, memory usage and PID.

🔹 top

Displays real-time CPU and memory usage of processes.

🔹 htop

Improved interactive version of top (if installed).

🔹 pgrep <name>

Finds the PID of a process by name.

🔹 pstree

Shows process hierarchy in tree format.

🔹 systemctl status <service>

Checks the status of a service managed by systemd.

🔹 systemctl start/stop/restart <service>

Controls service lifecycle.


📂 2️⃣ File System Commands
🔹 ls -la

Lists all files (including hidden) with detailed permissions.

🔹 cd <directory>

Changes current directory.

🔹 pwd

Displays current working directory.

🔹 mkdir <folder>

Creates a new directory.

🔹 rm <file>

Deletes a file.

🔹 rm -rf <folder>

Force deletes a directory and its contents.

🔹 cp <source> <destination>

Copies files or folders.

🔹 mv <source> <destination>

Moves or renames files/folders.

🔹 cat <file>

Displays file content.

🔹 less <file>

Views large files page by page.

🔹 tail -f <file>

Shows live updates of a file (used for log monitoring).

🔹 df -h

Displays disk space usage in human-readable format.

🔹 du -sh <folder>

Shows size of a folder.

🔹 chmod 755 <file>

Changes file permissions.

🔹 chown user:group <file>




3️⃣ Networking Troubleshooting
🔹 ip a

Displays IP addresses of the system.

🔹 hostname -I

Shows system IP address quickly.

🔹 ping <host>

Tests network connectivity.

🔹 ss -tulnp

Shows listening ports and associated processes.

🔹 netstat -tulnp

Displays active connections and open ports (older command).

🔹 lsof -i :<port>

Shows which process is using a specific port.

🔹 nslookup <domain>

Checks DNS resolution.

🔹 dig <domain>

Provides detailed DNS information.

🔹 traceroute <host>

Shows path packets take to reach a host.

🔹 nc -zv <host> <port>

Tests if a specific port is reachable.

Changes file ownership.
