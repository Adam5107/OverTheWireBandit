### The Ultimate "Search & Rescue" Tool for Linux

The `find` command is like a high-powered search engine for your computer's files. Unlike a simple search, it can filter by **name, size, age, ownership, and permissions.**

---

## 1. The Anatomy of a Search

Every `find` command follows this logical structure:

`find` **[Where to look]** **[What to look for]** **[What to do with it]**

- **Where:** The directory path (e.g., `/home`, `.`, `/var`).
    
- **Criteria:** The "filters" (e.g., name, size).
    
- **Action:** (Optional) What happens to the results (e.g., delete, list, or execute).
    

---

## 2. Essential Search Recipes

Here are the most common ways you will use `find` every day.

### A. Searching by Name

- **Exact match:** `find . -name "config.txt"`
    
- **Case-insensitive:** `find . -iname "CONFIG.txt"`
    
- **Using Wildcards:** `find /var/log -name "*.log"` (Finds all files ending in .log)
    

### B. Searching by Type

Tell Linux if you want a file or a folder.

- **Files only:** `find . -type f`
    
- **Directories only:** `find . -type d`
    

### C. Searching by Size (The "Byte" Precision)

- **Exactly 100 bytes:** `find . -size 100c`
    
- **Larger than 10MB:** `find . -size +10M`
    
- **Empty files:** `find . -empty`
    

### D. Searching by Time

- **Modified in the last 24 hours:** `find . -mtime 0`
    
- **Modified more than 10 days ago:** `find . -mtime +10`
    

---

## 3. The Power Move: "Find and Act"

Finding files is great, but **acting** on them automatically is where the real power lies.

|**Action**|**Command Example**|**What it does**|
|---|---|---|
|**List Details**|`find . -name "*.sh" -ls`|Shows sizes, dates, and permissions.|
|**Delete**|`find . -name "temp_*" -delete`|Instantly removes matches (Use carefully!).|
|**Execute**|`find . -name "*.txt" -exec chmod 644 {} \;`|Changes permissions for all found files.|

> [!IMPORTANT]
> 
> **Safety Tip:** Always run your `find` command **without** `-delete` or `-exec` first to see the list of files and make sure you aren't deleting something important!

---

## 4. Helpful Summary Table

|**Goal**|**Flag to Use**|**Example**|
|---|---|---|
|**Name**|`-name` or `-iname`|`-name "flag.txt"`|
|**Type**|`-type`|`f` (file), `d` (directory)|
|**Size**|`-size`|`+100c` (more than 100 bytes)|
|**Depth**|`-maxdepth`|`-maxdepth 1` (don't go into subfolders)|
|**User**|`-user`|`-user root`|

---

## 5. Pro Tip: Combining Everything

You can stack these flags to be incredibly specific:

`find /home -type f -name "*.png" -size +1M`

> _"Search in /home for **files** that are **PNGs** and are **larger than 1MB**."_

---
