### **1. `more` (The Reader)**

Use this to read long files one page at a time so they don't scroll off the screen.

- **Command:** `more filename.txt`
    
- **Spacebar:** Next page.
    
- **Enter:** Next line.
    
- **`q`**: Quit.
    

---

### **2. `vi` (The Editor)**

Use this to write or edit text files in the terminal.

- **Command:** `vi filename.txt`
    

**The 3 Keys You Must Know:**

| Key | Function |

| :--- | :--- |

| **`i`** | **Start typing** (Insert mode). |

| **`Esc`** | **Stop typing** (Go back to command mode). |

| **`:wq`** | **Save and Quit** (Write & Quit). |

**Quick Workflow:**

1. Type `vi file.sh`
    
2. Press **`i`** -> Write your code.
    
3. Press **`Esc`** -> Type **`:wq`** -> Press **Enter**.

### **3. `id` (The Identity Card)**

Use this to verify **who you are** and what **permissions** (groups) you have. This is the first command you type after hacking a system to see if you succeeded.

- **Command:** `id`
    
- **Output Example:**
    
    `uid=1000(kali) gid=1000(kali) groups=1000(kali),27(sudo)`
    

**What the codes mean:**

| Code | Meaning |

| :--- | :--- |

| **uid** | **User ID**. This is your specific ID. |

| **gid** | **Group ID**. This is your primary team. |

| **groups**| **Access List**. All the teams you belong to. |

> **Pro Tip:** If you see **`uid=0(root)`**, congratulations—you have full control of the system ("God Mode").