
### 1. Purpose of `diff`

In CTFs, `diff` is often used to find a "needle in a haystack"—such as a single unique password hidden in a new version of a large file.

- **Syntax:** `diff [file1] [file2]`
    
- **The Logic:** The command compares the files line by line. It tells you what needs to be changed in the first file to make it match the second.
    

---

### 2. How to Read `diff` Output

When you run the command, you will see symbols that indicate the differences:

- **`<` (Less-than):** This line is only in the **first** file.
    
- **`>` (Greater-than):** This line is only in the **second** file.
    
- **`---` (Dashes):** Separates the content of the two files.
    
- **Letters (`a`, `c`, `d`):**
    
    - `a`: Added.
        
    - `c`: Changed.
        
    - `d`: Deleted.
        

---

### 3. Key Flags for CTFs

- **`-u` (Unified Format):** Shows the differences with a few lines of context around them, making it much easier to read.
    
- **`-y` (Side-by-Side):** Displays the files in two columns so you can visually compare them.
    
- **`-q` (Brief):** Only tells you if the files are different or identical without showing the content.
    
- **`-w`:** Ignores all white space (useful if the flag is hidden by extra spaces).
    

---
