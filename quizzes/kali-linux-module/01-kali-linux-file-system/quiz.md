
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
- **List 5 that stand out:** `________________________`

---

### 🧩 Challenge 2 – Core Commands Check

- Find where `ls`, `bash`, and `grep` live
- **Command:** `which ls; which bash; which grep`
- **Output:**
    - `ls`: `___________`
    - `bash`: `___________`
    - `grep`: `___________`

> 💡 _Hint: Are they in `/bin`, `/usr/bin`, or both?_

---

### 🧩 Challenge 3 – Spot the Admin Tools

- List 3 binaries inside `/sbin` or `/usr/sbin` and what they do
- **Examples:**
    1. `_______` – `_________________`
    2. `_______` – `_________________`
    3. `_______` – `_________________`

---

### 🧩 Challenge 4 – Temporary Playground

- Explore `/tmp` and `/var/tmp`
- Create a file in both, then reboot and check if they persist
- **Commands:**
    - `echo 'test1' > /tmp/testfile`
    - `echo 'test2' > /var/tmp/testfile2`

- **Which one survived reboot?** `____________`

> 🧠 _What does this tell you about `/tmp` vs `/var/tmp`?_

---

### 🧩 Challenge 5 – What’s in Your Root?

- Check `/home/kali` and name one **dotfile** there
- **Command:** `ls -la ~`

- **Dotfile found:** `____________________`

---

### 🧩 Challenge 6 – Compare `/bin` vs `/usr/bin`

- Count how many binaries are in each
- **Command:** `ls /bin | wc -l; ls /usr/bin | wc -l`

- **What do you observe?** `____________________`

---

### 🧩 Challenge 7 – What’s in `/lib` and `/lib64`

- Explore shared libraries
- **Command:** `ls /lib; ls /lib64`

- **What types of files are these?** `____________________`

---

### 🧩 Challenge 8 – Explore `/media` and `/mnt`

- What’s the difference?
- **Command:** `ls /media; ls /mnt`
- **Purpose of each:**
    - `/media`: `________________`
    - `/mnt`: `________________`

---

### 🧩 Challenge 9 – What’s Running Under `/proc`

- Explore real-time process directories
- **Command:** `ls /proc | grep '^[0-9]' | head -n 5`
- **What do the numbers mean?** `____________________`

---

### 🧩 Challenge 10 – Kernel Info from `/proc`

- See what kernel you’re running
- **Command:** `cat /proc/version`

- **Output snippet:** `____________________`

---

### 🧩 Challenge 11 – View System Uptime

- Use `/proc` to see uptime
- **Command:** `cat /proc/uptime`

- **What does it show?** `____________________`

---

### 🧩 Challenge 12 – List All Mounted Filesystems

- View all active mounts
- **Command:** `cat /etc/mtab`

- **What is mounted on `/`?** `____________________`
---

### 🧩 Challenge 13 – Explore `/opt` for Custom Tools

- List tools in `/opt`
- **Command:** `ls /opt`

- **What did you find?** (e.g. burpsuite, Nessus) `____________`

---

### 🧩 Challenge 14 – Find Home Directories

- Check who has home folders
- **Command:** `ls /home`

- **Output:** `_____________`

---

### 🧩 Challenge 15 – Examine Virtual Sys Info

- View kernel-hardware interface
- **Command:** `ls /sys`

- **One interesting subdir:** `____________________`

---

## 🔹 **Part 2: Tool Arsenal Exploration (5 Tasks)**

### 🧩 Challenge 16 – The Heartbeat: `/usr/share/`

- List 5 tool-related directories in `/usr/share/`
- **Command**: `ls /usr/share | grep -i 'meta\|exploit\|wordlist\|web\|sql'`

- **Examples**: `__________`, `__________`, `__________`

---

### 🧩 Challenge 17 – Wordlist Recon

- Locate the legendary `rockyou.txt`
- Command: `locate rockyou.txt`
- **Full path**: `_____________________`

> 💡Bonus: Is it compressed? `Yes / No`

---

### 🧩 Challenge 18 – Metasploit Deep Dive

- Navigate to `/usr/share/metasploit-framework`
- Count how many `.rb` (Ruby) scripts are inside `/modules/exploits/`
- **Command**: `___________________________`

- **Number of `.rb` files**: `________`


> 🛠️ _These files are **Metasploit** modules used in real attacks._

---

### 🧩 Challenge 19 – Shell Game

- List available webshell types in `/usr/share/webshells`
- **Command**: `tree /usr/share/webshells -L 2`

- **Languages found**: `__________`, `__________`, `__________`

---

### 🧩 Challenge 20 – Exploit-DB Check

- What’s one example exploit in `/usr/share/exploitdb/exploits/linux/local/`?
- **Command**: `ls /usr/share/exploitdb/exploits/linux/local/ | head -n 1`

- **Filename**: `____________________`

---

## 🔹 **Part 3: Logs & Configs Mastery (5 Tasks)**

### 🧩 Challenge 21 – Identity Check

- What OS and version is this Kali machine running?
- **Command**: `cat /etc/os-release`

- **Output**: `_______________________`

---

### 🧩 Challenge 22 – Log Intelligence

- Search `/var/log/auth.log` for failed logins
- **Command**: `grep -i 'failed' /var/log/auth.log | wc -l`

- **Failed attempts found**: `________`

---

### 🧩 Challenge 23 – System Events Log

- What’s the size of `/var/log/syslog` in human-readable format?
- **Command**: `du -h /var/log/syslog`

- **Output**: `________________`


### 🧩 Challenge 24 – SSH Configuration

- View the SSH config file
- **Command**: `cat /etc/ssh/sshd_config | grep "Port"`

- **Port number used**: `__________`

---

### 🧩 Challenge 25 – Nmap Tuning

- What script categories are defined under `/usr/share/nmap/`
- **Command**: `ls /usr/share/nmap/`

- **Output examples**: `______________`

---

## 🔹 **Part 4: Deep Search & Practice (4 Tasks)**

### 🧩 Challenge 26 – Find Tools by Keyword

- Use `find` to locate tools with "john" in the name
- **Command**: `find /usr/sbin -type f -iname '*john*'`

- **Tool found**: `____________________`

---

### 🧩 Challenge 27 – Permission Check

- Show permissions for `/usr/share/wordlists/rockyou.txt`
- **Command**: `ls -l /usr/share/wordlists/rockyou.txt`

- **Output**: `____________________`

---

### 🧩 Challenge 28 – Look Inside `/proc`

- View CPU or memory info
- **Command**:
    1. `cat /proc/cpuinfo | head -5`
    2. `cat /proc/meminfo | head -3`

- **One fact learned**: `_____________________`    

---

### 🧩 Challenge 29 – Mount Awareness

- Show current mounts and identify the root (`/`) mount
- **Command**: `mount | grep 'on / '`

- **Output**: `______________________`

---
