
---

# 🧾 **Kali Linux Filesystem Scavenger Hunt: Tools, Logs, and Configs**

**Module:** Mastering the Kali Linux File Structure  
**Objective:** Understand where Kali stores critical tools, logs, and configs — essential for effective red/blue teaming.  
**Difficulty:** Intermediate (no sudo needed unless noted)  
**Format:** Hands-on terminal tasks with answers, observations, or command outputs.

---

# 🔹 **Part 1: Know Your Roots (15 Tasks)**

### 🧩 Challenge 1 – Map the Skeleton

- List top-level directories in Kali’s root (`/`)
- **Command:** `ls /`
- **List 5 that stand out:** `bin, boot, etc, usr, var`

---

### 🧩 Challenge 2 – Core Commands Check

- Find where `ls`, `bash`, and `grep` live
- **Command:** `which ls; which bash; which grep`
- **Output:**
    - `ls`: `/bin/ls`
    - `bash`: `/bin/bash`
    - `grep`: `/bin/grep`

> 💡 _Hint: Are they in `/bin`, `/usr/bin`, or both?_

---

### 🧩 Challenge 3 – Spot the Admin Tools

- List 3 binaries inside `/sbin` or `/usr/sbin` and what they do
- **Examples:**
    1. `ifconfig` – `Displays and configures network interfaces`
    2. `fsck` – `Checks and repairs filesystems`
    3. `reboot` – `Reboots the system`

---

### 🧩 Challenge 4 – Temporary Playground

- **Commands:**
    - `echo 'test1' > /tmp/testfile`
    - `echo 'test2' > /var/tmp/testfile2`

- **Which one survived reboot?** `/var/tmp/testfile2`


> 🧠 _What does this tell you about `/tmp` vs `/var/tmp`?_  
> `/tmp` is cleared on reboot, `/var/tmp` is not.

---

### 🧩 Challenge 5 – What’s in Your Root?

- **Command:** `ls -la ~`
- **Dotfile found:** `.bashrc`

---

### 🧩 Challenge 6 – Compare `/bin` vs `/usr/bin`

- **Command:** `ls /bin | wc -l; ls /usr/bin | wc -l`
- **What do you observe?** `/usr/bin` contains far more binaries than `/bin` — it holds non-essential user programs.    

---

### 🧩 Challenge 7 – What’s in `/lib` and `/lib64`

- **Command:** `ls /lib; ls /lib64`

- **What types of files are these?** `Shared libraries required by binaries`    

---

### 🧩 Challenge 8 – Explore `/media` and `/mnt`

- **Command:** `ls /media; ls /mnt`
- **Purpose of each:**
    - `/media`: `Auto-mounted external drives`
    - `/mnt`: `Manual mount point for sysadmin use`

---

### 🧩 Challenge 9 – What’s Running Under `/proc`

- **Command:** `ls /proc | grep '^[0-9]' | head -n 5`
- **What do the numbers mean?** `Each is a PID (process ID) of a running process`

---

### 🧩 Challenge 10 – Kernel Info from `/proc`

- **Command:** `cat /proc/version`
- **Output snippet:** `Linux version 6.x (Debian 6.x) ...`

---

### 🧩 Challenge 11 – View System Uptime

- **Command:** `cat /proc/uptime`
- **What does it show?** `Uptime in seconds and total idle time`

---

### 🧩 Challenge 12 – List All Mounted Filesystems

- **Command:** `cat /etc/mtab`
- **What is mounted on `/`?** `/dev/sda1` or similar, depending on the system    

---

### 🧩 Challenge 13 – Explore `/opt` for Custom Tools

- **Command:** `ls /opt`
- **What did you find?** `burpsuite` (if installed), or `empty`

---

### 🧩 Challenge 14 – Find Home Directories

- **Command:** `ls /home`
- **Output:** `kali`

---

### 🧩 Challenge 15 – Examine Virtual Sys Info

- **Command:** `ls /sys`    
- **One interesting subdir:** `kernel` or `block`

---

## 🔹 **Part 2: Tool Arsenal Exploration (5 Tasks)**

### 🧩 Challenge 16 – The Heartbeat: `/usr/share/`

- **Command**: `ls /usr/share | grep -i 'meta\|exploit\|wordlist\|web\|sql'`
- **Examples**: `metasploit-framework`, `exploitdb`, `wordlists`

---

### 🧩 Challenge 17 – Wordlist Recon

- **Command**: `locate rockyou.txt`    
- **Full path**: `/usr/share/wordlists/rockyou.txt.gz`

> 💡Bonus: Is it compressed? `Yes`

---

### 🧩 Challenge 18 – Metasploit Deep Dive

- **Command**:  
    `find /usr/share/metasploit-framework/modules/exploits/ -name '*.rb' | wc -l`    
- **Number of `.rb` files**: `400+` (depends on version)

---

### 🧩 Challenge 19 – Shell Game

- **Command**: `tree /usr/share/webshells -L 2`    
- **Languages found**: `php`, `asp`, `jsp`

---

### 🧩 Challenge 20 – Exploit-DB Check

- **Command**: `ls /usr/share/exploitdb/exploits/linux/local/ | head -n 1`
- **Filename**: `10018.sh` or similar

---

## 🔹 **Part 3: Logs & Configs Mastery (5 Tasks)**

### 🧩 Challenge 21 – Identity Check

- **Command**: `cat /etc/os-release`
- **Output**: `PRETTY_NAME="Kali GNU/Linux Rolling"`

---

### 🧩 Challenge 22 – Log Intelligence

- **Command**: `grep -i 'failed' /var/log/auth.log | wc -l`
- **Failed attempts found**: `Depends on system usage (e.g., 5)`

---

### 🧩 Challenge 23 – System Events Log

- **Command**: `du -h /var/log/syslog`
- **Output**: `1.2M` (example)

---

### 🧩 Challenge 24 – SSH Configuration

- **Command**: `cat /etc/ssh/sshd_config | grep "Port"`
- **Port number used**: `22` (or custom)

---

### 🧩 Challenge 25 – Nmap Tuning

- **Command**: `ls /usr/share/nmap/`
- **Output examples**: `nmap-services`, `nmap-protocols`, `nmap-mac-prefixes`

---

## 🔹 **Part 4: Deep Search & Practice (4 Tasks)**

### 🧩 Challenge 26 – Find Tools by Keyword

- **Command**: `find /usr/sbin -type f -iname '*john*'`
- **Tools found**: `/usr/sbin/ua2fjohn, /usr/sbin/eapmd5tojhon`

---

### 🧩 Challenge 27 – Permission Check

- **Command**: `ls -l /usr/share/wordlists/rockyou.txt*`
- **Output**: `-rw-r--r-- 1 root root ... rockyou.txt.gz`

---

### 🧩 Challenge 28 – Look Inside `/proc`

- **Command**:
    1. `cat /proc/cpuinfo | head -5`
    2. `cat /proc/meminfo | head -3`
- **One fact learned**: `CPU model and number of cores; total memory`

---

### 🧩 Challenge 29 – Mount Awareness

- **Command**: `mount | grep 'on / '`
- **Output**: `/dev/sda1 on / type ext4 (rw,relatime,errors=remount-ro)`

---
