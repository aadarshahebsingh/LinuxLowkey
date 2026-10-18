# LinuxLowkey

![Linux](https://img.shields.io/badge/Linux-Ubuntu%2024.04-E95420?style=for-the-badge&logo=ubuntu&logoColor=white)
![Bash](https://img.shields.io/badge/Shell-Bash-121011?style=for-the-badge&logo=gnubash&logoColor=white)
![Automation](https://img.shields.io/badge/Focus-Automation-blue?style=for-the-badge)

Bash scripts that automate common Linux administration tasks: server health checks, disk alerts, backups, log cleanup, user creation and log analysis.

All scripts were written and tested on Ubuntu 24.04 LTS.

---

# Project Goals

The goal of this project is to practice everyday system administration tasks and automate them with Bash.

The scripts focus on:

- reusable automation
- logging and reporting
- basic error handling
- monitoring workflows
- scheduled execution with cron

---

# Scripts Included

| Script | Purpose | Key Features |
|---|---|---|
| `server_health.sh` | Server health check | CPU, RAM, Disk, Services, Network |
| `disk_alerter.sh` | Disk usage monitoring | Threshold alerts, logs, reports |
| `log_cleaner.sh` | Log maintenance | Compression, deletion, cleanup reports |
| `user_creation.sh` | User creation | Validation, groups, sudo setup |
| `backup.sh` | Backup | Compression, verification, retention |
| `find_large_files.sh` | Disk investigation | Finds large files |
| `log_analyzer.sh` | Log analysis | grep + awk + sed summaries |

---

# Technologies Used

- Linux (Ubuntu 24.04 LTS)
- Bash scripting
- Cron
- grep, awk, sed
- tar, gzip
- rsync

---

# Environment

| Component | Details |
|---|---|
| OS | Ubuntu 24.04 LTS |
| Where tested | [your setup: local VM / WSL / dual boot] |
| Shell | Bash |

---

# Project Structure

```text
LinuxLowkey/
│
├── backup.sh
├── disk_alerter.sh
├── find_large_files.sh
├── log_analyzer.sh
├── log_cleaner.sh
├── server_health.sh
├── user_creation.sh
│
├── logs/
├── backups/
└── README.md
```

---

# Workflow

```text
Cron Job
   ↓
Monitoring Script
   ↓
Logs Generated
   ↓
Alerts Triggered
   ↓
Cleanup / Backup
```

---

# Features

## Monitoring
- CPU usage
- RAM usage
- Disk usage
- Service status checks
- Internet connectivity check

## Automation
- Scheduled runs with cron
- Automated log cleanup
- Automated backups
- Threshold-based alerts

## System Administration
- User creation
- Group management
- Permission handling
- Backup retention

## Log Processing
- Error detection
- Warning extraction
- Pattern filtering
- Summary counts

---

# Usage

## Clone Repository

```bash
git clone https://github.com/aadarshahebsingh/LinuxLowkey.git

cd LinuxLowkey
```

## Make Scripts Executable

```bash
chmod +x *.sh
```

---

# 1. Server Health Check

```bash
./server_health.sh
```

Checks CPU, RAM and disk usage, the status of selected services, and internet connectivity.

### Example Output

```text
================================================
 SERVER HEALTH CHECK REPORT
================================================

CPU Usage: 12%
RAM Usage: 43%
Disk Usage: 38%

cron: RUNNING
rsyslog: RUNNING

Internet: CONNECTED
```

---

# 2. Disk Usage Alerter

```bash
./disk_alerter.sh
```

- checks all mounted partitions
- raises an alert when usage crosses a threshold
- writes results to a log file

### Example

```text
ALERT: / is at 85%
```

---

# 3. Log Cleaner

```bash
./log_cleaner.sh
```

- deletes old logs
- compresses recent logs
- prints a cleanup report

---

# 4. User Creation Script

## Interactive Mode

```bash
sudo ./user_creation.sh --interactive
```

## CSV Batch Mode

```bash
sudo ./user_creation.sh --file users.csv
```

### CSV Format

```text
username, full_name, group, sudo
```

- username validation
- home directory creation
- sudo assignment
- group management
- welcome file creation

---

# 5. Backup Script

```bash
./backup.sh
```

- compressed backups
- integrity verification
- retention cleanup
- multiple source folders
- logging

### Example

```text
Backup created successfully
Verification passed
```

---

# 6. Find Large Files

```bash
# files larger than 100MB
./find_large_files.sh /home 100M

# files larger than 1GB
./find_large_files.sh / 1G
```

---

# 7. Log Analyzer

```bash
./log_analyzer.sh /path/to/logfile.log
```

Generates:
- error counts
- warning counts
- hourly distribution
- filtered summaries

---

# Cron Automation

Example cron jobs (replace `<user>` and the paths with your own):

```cron
# Health check every 15 minutes
*/15 * * * * /home/<user>/LinuxLowkey/server_health.sh >> /home/<user>/LinuxLowkey/logs/health.log 2>&1

# Disk alerts every hour
0 * * * * /home/<user>/LinuxLowkey/disk_alerter.sh >> /home/<user>/LinuxLowkey/logs/disk.log 2>&1

# Daily backups at 2 AM
0 2 * * * /home/<user>/LinuxLowkey/backup.sh >> /home/<user>/LinuxLowkey/logs/backup.log 2>&1

# Weekly log cleanup (Sunday 11 PM)
0 23 * * 0 /home/<user>/LinuxLowkey/log_cleaner.sh >> /home/<user>/LinuxLowkey/logs/cleaner.log 2>&1
```

---

# Concepts Demonstrated

## Linux Administration
- process and service checks
- user management
- file permissions
- disk usage

## Bash Scripting
- variables
- loops
- functions
- conditionals
- exit codes

## Automation
- cron scheduling
- cleanup and backup automation
- logging

## Log Analysis
- grep
- awk
- sed
- pipelines

---

# What I Learned

- how to automate repetitive Linux tasks with Bash
- how cron schedules jobs
- how backup retention works
- how to analyze logs with grep, awk and sed
- how to write reusable scripts with functions
- how to manage Linux users and permissions

---

# Future Improvements

- email alerts
- Slack/Discord notifications
- Dockerfile to run the scripts in a container
- GitHub Actions workflow with ShellCheck

---

# Author

Aadarsh Shaheb Singh

Built as part of my Linux and automation learning.
