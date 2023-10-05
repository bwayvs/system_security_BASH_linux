# Linux System Security Checker

This project focuses on performing basic security checks on a Linux system. Leveraging the power of BASH scripting, the project evaluates several potential security issues on the system and provides an overview of potential vulnerabilities. This tool aids system administrators in ensuring the integrity of their Linux machines and highlights areas of concern.

## Sources

### BASH (Bourne Again SHell)

Provided by: GNU Project

Shell scripting: Various Contributors

https://www.gnu.org/software/bash/

## Project Details

The security checker evaluates the Linux system based on common potential vulnerabilities. Some of its key functionalities include:

### Checking for Users Without Passwords
This feature scans for user accounts that have no set passwords, a significant potential security risk.

```bash
awk -F: '($2 == "" ) { print $1 }' /etc/shadow
```

### Listing All Sudoers
Displays all users with `sudo` privileges, helping admins keep track of who can execute commands with elevated permissions.

```bash
cat /etc/group | grep sudo
```

### World-Writable Files & Directories
World-writable files and directories can be modified by any user, presenting a security risk. The script identifies these entities.

```bash
find / -type f -perm -002 -print 2>/dev/null
find / -type d -perm -002 -print 2>/dev/null
```

### No Owner Files
Files with no owners can indicate orphaned or improperly configured files and directories.

```bash
find / -nouser -o -nogroup -print 2>/dev/null
```

### Analyzing Login Attempts
Reviewing the last 100 lines of the auth log to check for failed login attempts, which could indicate brute force attacks.

```bash
tail -100 /var/log/auth.log | grep "Failed password"
```

### SSH Root Login Permissions
Checking whether root login via SSH is permitted, which is often considered a security risk.

```bash
grep "PermitRootLogin" /etc/ssh/sshd_config | grep -v "#"
```


## Authors

- Veronica Broadway (https://bwayvs.github.io/Professional_Portfolio/)

## 🚀 About Me
I'm Veronica, a results-driven Data Analyst with expertise in SAP and process improvement. With a background in translating complex requirements into actionable insights, I leverage SQL, data visualization tools, and Agile methodologies to optimize supply chains and drive business decisions. My passion lies in turning data into meaningful business strategies, ensuring organizational alignment, and fostering cross-functional collaboration.

## 🔗 LinkedIn Profile
[![linkedin](https://img.shields.io/badge/linkedin-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/veronicabroadway/)

