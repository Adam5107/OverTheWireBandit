In a CTF like Bandit, these tools are essential for managing multiple tasks simultaneously and ensuring your processes (like a port scanner or a listener) keep running even if your connection drops.

---

### 1. Bash (Bourne Again Shell)

Bash is the command processor you are currently using in Bandit. It is the "glue" that allows you to pipe commands together.

- **CTF Tip:** Use `bash --version` to check for specific vulnerabilities like Shellshock, or use `bash -p` to maintain root privileges when executing a **setuid** binary.
    

### 2. Unix 'Job Control'

Job control allows you to manage multiple processes within a single terminal window.

- **`&` (Backgrounding):** Adding this to the end of a command runs it in the background.
    
    - _Example:_ `nmap -p- localhost > scan.txt &`.
        
- **`CTRL-Z`:** Suspends the currently running foreground process and sends it to the background in a "stopped" state.
    
- **`jobs`:** Lists all currently running or suspended jobs in your session.
    
- **`bg`:** Resumes a suspended job in the **background**.
    
- **`fg`:** Brings a background job back to the **foreground** so you can interact with it.
    

---

### 3. Screen and Tmux (Terminal Multiplexers) ( Video : [NetworkChuck](https://youtu.be/nTqu6w2wc68) )

These tools are "super-powered" versions of job control. They allow you to create multiple "windows" inside one SSH session and, most importantly, **detach** from them.
#### **Tmux (The Modern Choice)**

- **Start:** Type `tmux`.
    
- **New Window:** `CTRL-B` then `c`.
    
- **Switch Windows:** `CTRL-B` then `[0-9]`.
    
- **Detach:** `CTRL-B` then `d`. (Your commands keep running even if you close SSH!).
    
- **Reattach:** `tmux attach`.
    

#### **Screen (The Classic Choice)**

- **Start:** Type `screen`.
    
- **Detach:** `CTRL-A` then `d`.
    
- **Reattach:** `screen -r`.
    

---

### 📊 Comparison Table

| **Tool**              | **Best Used For...**                          | **Key Feature**                                     |
| --------------------- | --------------------------------------------- | --------------------------------------------------- |
| **`&` / `fg` / `bg`** | Quick, simple background tasks.               | Built into every shell; no extra software needed.   |
| **`tmux`**            | Complex sessions with multiple windows/panes. | Persists after SSH disconnect; highly customizable. |
| **`screen`**          | Basic persistent sessions.                    | Available on almost every legacy system.            |

### 🛠️ CTF Practical Scenario

Imagine you are running a long `nmap` scan on Bandit Level 16. You accidentally press `CTRL-C` and lose your progress.

1. **Solution:** Start a `tmux` session first.
    
2. Run your scan.
    
3. If your internet dies, just log back in later and run `tmux attach` to see the results.
    
