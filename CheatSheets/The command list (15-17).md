
---

### 1. `ssh` (Secure Shell)

- **`-i [file]` (Identity)**: Forces SSH to use the specific private key provided instead of trying passwords or default keys. **Requirement:** The file must have permissions `600` (Read/Write for owner only) or it will be ignored.
    
- **`-p [port]`**: Connects to a non-standard port (Bandit uses `2220`).
    
- **`-L [local]:[remote_host]:[remote_port]` (Tunneling)**: Maps a port on your Kali machine to a port on the internal Bandit network that is otherwise blocked by a firewall.
    

### 2. `telnet`

- **Syntax**: `telnet [host] [port]`.
    
- **Usage**: It is a raw text protocol. It is often used in CTFs to interact with simple "challenge" services that don't use encryption.
    
- **Limitation**: It cannot handle the SSL/TLS "handshake," so it will fail on encrypted ports where `openssl` succeeds.
    

### 3. `nc` (Netcat)

- **`-l` (Listen)**: Turns your machine into a server waiting for a connection.
    
- **`-v` (Verbose)**: Provides more detail about the connection (e.g., "Connection to port 30000 succeeded!").
    
- **`-n` (Numeric)**: Prevents DNS resolution, making the connection faster and stealthier.
    
- **`-p [port]`**: Specifies the source port.
    

### 4. `openssl s_client`

- **`-connect [host]:[port]`**: The standard syntax to initiate an encrypted connection.
    
- **`-ign_eof` (Ignore EOF)**: Keeps the connection open even after you send data. This is helpful if the server takes a few seconds to process your input and return the flag.
    
- **`-quiet`**: Suppresses the certificate information and only shows the data you are interested in.
    

### 5. `nmap` (Network Mapper)

- **`-sV` (Service Version)**: Probes open ports to determine what software and version are running (e.g., identifying `OpenSSH 8.9p1`).
    
- **`-sC` (Default Scripts)**: Runs a collection of safe "Nmap Scripting Engine" (NSE) scripts to detect common vulnerabilities automatically.
    
- **`-p [range]`**: Scans specific ports (e.g., `-p 30000-31000`) or use `-p-` to scan all 65,535 possible ports.
    
- **`-oN [file]`**: Saves the results to a text file for later reference.
    

---

### Command Integration Table

| **If the service is...** | **Use this command...** | **Key Option to add**    |
| ------------------------ | ----------------------- | ------------------------ |
| **Encrypted (SSL/TLS)**  | `openssl s_client`      | `-connect host:port`     |
| **Raw/Unencrypted**      | `nc`                    | `-v`                     |
| **Hidden/Firewalled**    | `ssh`                   | `-L` (Tunneling)         |
| **Unknown/Closed**       | `nmap`                  | `-sV` (Discover service) |
