
---

### 1. `find`: The Metadata Surgeon

**Why it's needed:** CTF creators hide flags in files with specific attributes (e.g., a file that is exactly 1337 bytes or a file only "root" can read).

- **Deep Syntax:** `find [path] -type [f/d] -size [size] -perm [mode] -exec [command] {} +`
    
- **CTF Power-user Flags:**
    
    - `-perm -4000`: Finds **SUID** files (used for privilege escalation).
        
    - `-mmin -10`: Finds files modified in the last 10 minutes (useful if a script is generating flags).
        
    - `-size 100c`: The `c` stands for bytes. Essential for "exact size" challenges.
        
- **Pro Tip:** Redirect errors to avoid "Permission Denied" spam: `find / -name flag.txt 2>/dev/null`.
    

### 2. `grep`: The Pattern Sniper

**Why it's needed:** To pull a specific string out of a mountain of "noise" or binary data.

- **Deep Syntax:** `grep [options] "pattern" [file]`
    
- **CTF Power-user Flags:**
    
    - `-a`: Process a **binary** file as if it were text (stops "Binary file matches" messages).
        
    - `-o`: **Only** show the matching part of the line (perfect for extracting just the flag).
        
    - `-P`: Use Perl-Compatible Regular Expressions (PCRE) for advanced patterns.
        
- **Pro Tip:** Use `grep -rEi "flag|ctf|key" .` to search for multiple keywords at once.
    

### 3. `strings`: The Binary Peeker

**Why it's needed:** Executables (ELF/EXE) look like garbage when opened in a text editor. `strings` scans for printable characters.

- **Deep Syntax:** `strings -n [min-len] -t [format] -e [encoding] [file]`
    
- **CTF Power-user Flags:**
    
    - `-t d`: Shows the **decimal offset**. Tells you exactly where in the file the string is located.
        
    - `-e l`: Searches for **16-bit little-endian** strings. Standard `strings` misses these in many Windows/modern binaries.
        
- **Pro Tip:** Always run `strings` on a mystery binary before running the binary itself.
    

### 4. `sort` & `uniq`: The Frequency Analysts

**Why it's needed:** Often used in "Steganography" or "Log Analysis" to find a single unique entry among millions of duplicates.

- **Deep Syntax:** `sort [file] | uniq -c | sort -n`
    
- **The Logic:** `sort` groups identical lines together $\rightarrow$ `uniq -c` counts them $\rightarrow$ `sort -n` puts the smallest counts at the top.
    
- **CTF Power-user Flags:**
    
    - `uniq -u`: Only prints lines that are **unique** (occur exactly once).
        

### 5. `base64`: The Obfuscation Solver

**Why it's needed:** Base64 is the most common way flags are "hidden" in web or network traffic.

- **Deep Syntax:** `echo "encoded_string" | base64 -d`
    
- **CTF Power-user Flags:**
    
    - `-i`: Ignore non-alphabet characters (useful if the string has weird line breaks).
        
- **Pro Tip:** If a string contains `+`, `/`, and ends with `=`, it's 99% Base64.
    

### 6. `tr`: The Character Transformer

**Why it's needed:** For shifting ciphers (ROT13) or cleaning up data formats.

- **Deep Syntax:** `tr [find_set] [replace_set]`
    
- **CTF Power-user Flags:**
    
    - `-d`: **Delete** specific characters (e.g., `tr -d '\n'` to make a multiline string a single line).
        
    - `-s`: **Squeeze** repeats (changes "aaaa" to "a").
        
- **Pro Tip:** ROT13 is solved with `tr 'A-Za-z' 'N-ZA-Mn-za-m'`.
    

### 7. `tar` / `gzip` / `bzip2`: The Archive Extractors

**Why it's needed:** CTF flags are often buried in multiple layers of compression.

- **Deep Syntax:**
    
    - `tar -xvf [file]`: **x**tract, **v**erbose, **f**ile.
        
    - `zcat [file.gz]`: View the content of a compressed file without unzipping it.
        
- **Pro Tip:** If you see a file with no extension, run the command `file [filename]` to see if it's actually a compressed archive.
    

### 8. `xxd`: The Hex Master

**Why it's needed:** To view or edit the raw bytes of a file.

- **Deep Syntax:** `xxd [options] [input] [output]`
    
- **CTF Power-user Flags:**
    
    - `-p`: **Plain** output (no addresses, no ASCII). Best for piping into other tools.
        
    - `-r -p`: **Reverse Plain**. Converts a hex string back into a binary file.
        
- **Pro Tip:** Use `xxd` to check the "Magic Bytes" at the start of a file to see its true identity.
    

---

### Comparison of Usage

|**If you have a...**|**Use this first...**|**Then pipe to...**|
|---|---|---|
|**Binary file**|`strings`|`grep`|
|**Massive Log**|`sort`|`uniq -c`|
|**Hex String**|`xxd -r -p`|`file`|
|**Directory of files**|`find`|`exec grep`|
|**Obfuscated Text**|`tr`|`base64 -d`|
