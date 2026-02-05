In Linux, **Cron** is the system's primary time-based job scheduler. It allows you to automate repetitive tasks, such as backups, log rotation, or running security scripts, so they happen at exact intervals without manual intervention.

---

## 1. Cron (The System Daemon)

The `cron` daemon (often called `crond`) is a background process that stays active as long as the system is running.

- **Scanning**: Every minute, the daemon wakes up and scans configuration files to see if any scheduled tasks match the current time.
    
- **Execution**: If a match is found, it executes the command with the permissions of the user who owns that crontab.
    
- **Logging**: Activity is usually logged in `/var/log/syslog` or `/var/log/cron`, which you can check to verify if a job ran.
    

---

## 2. Crontab (The Command & Personal File)

The word `crontab` refers both to the **command** used to manage schedules and the **file** where those schedules are stored. Every user on the system has their own individual crontab file.

- **`crontab -e`**: **E**dits your crontab file. It opens a temporary file in a text editor; once you save and exit, the system validates the syntax and installs it.
    
- **`crontab -l`**: **L**ists the contents of your current crontab.
    
- **`crontab -r`**: **R**emoves (deletes) your current crontab entirely.
    
- **`crontab -u [user] -e`**: Allows root or a privileged user to edit the crontab for a **specific user**.
    

---

## 3. Crontab(5) (The Format & Manual)

Running `man 5 crontab` gives you the documentation specifically for the **file format**. A crontab entry consists of six fields: five for time and one for the command.

### **The Five Time Fields**

|**Field**|**Name**|**Range**|**Example**|
|---|---|---|---|
|**1**|Minute|0 - 59|`30` (runs at 30 mins past the hour)|
|**2**|Hour|0 - 23|`14` (runs at 2:00 PM)|
|**3**|Day of Month|1 - 31|`15` (runs on the 15th of the month)|
|**4**|Month|1 - 12|`8` (runs only in August)|
|**5**|Day of Week|0 - 7|`1` (runs on Monday; 0 or 7 is Sunday)|

### **Special Symbols**

- **`*` (Asterisk)**: Represents "every." An asterisk in the minute field means "every minute".
    
- **`,` (Comma)**: Specifies a list of values (e.g., `1,3,5` in the Day field for Mon, Wed, Fri).
    
- **`-` (Hyphen)**: Specifies a range (e.g., `1-5` for Monday through Friday).
    
- **`/` (Slash)**: Specifies increments (e.g., `*/15` in the minute field for every 15 minutes).
    
### **The `@reboot` Special String**

Instead of using the five time fields (minute, hour, etc.), you can simply write `@reboot` at the beginning of the line.

- **Function:** It instructs the cron daemon to execute the specified command **once**, immediately after the system starts up (boots).
    
- **Why use it?** It is perfect for starting custom servers, mounting drives, or running scripts that need to be active as soon as the machine turns on, without you having to log in manually.
---

## 4. System-Wide Cron Directories

In a CTF like Bandit, the most important files are often found in system directories rather than individual user crontabs.

- **`/etc/cron.d/`**: A directory where system packages and admins drop crontab-style files.
    
- **`/etc/cron.hourly/`, `.daily/`, `.weekly/`**: Directories where you place scripts to run at those specific frequencies.
    

### **CTF "Setuid" Connection**

If you find a cron job running a script as a higher-level user, and you have permission to edit that script, you can gain that user's privileges. Always use **full paths** (e.g., `/usr/bin/cat`) in your scripts because cron often has a very limited `PATH` environment variable.
