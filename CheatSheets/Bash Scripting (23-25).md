# **"You need to learn BASH Scripting RIGHT NOW!! // EP 1"** by **NetworkChuck** | [Lien](https://youtu.be/SPwyp2NG-bE)

#### **1. What is Bash?**

- **Definition:** Bash stands for **"Bourne Again Shell"**. It was created in 1989 as an improved version of the original shell from 1970.
    
- **Purpose:** It is the command-line interface used to interact with the Linux operating system, acting as a wrapper around the Linux kernel.
    
- **Importance:** Learning Bash allows you to automate tasks (like hacking networks or creating cloud VMs), making you more efficient and valuable in IT roles.
    

#### **2. Writing Your First Script**

- **Tools:** The video recommends using a Linux environment (like a Linode cloud VM) and the text editor **Nano** to write scripts.
    
- **The Shebang:** Every Bash script should start with `#!/bin/bash` (called a "shebang"). This line tells the computer's interpreter that the file is a Bash script.
    
- **The "Hi Mom" Script:** The tutorial walks through creating a simple script named `himom.sh` that automates a conversation using the `echo` command to print text and the `sleep` command to create pauses between lines.
    

#### **3. Running the Script**

- **Method 1:** You can run a script by typing `bash` followed by the filename (e.g., `bash himom.sh`).
    
- **Method 2:** You can run it directly using `./` followed by the filename (e.g., `./himom.sh`). However, this often leads to a "Permission denied" error initially.
    

#### **4. Understanding Permissions**

- **The Problem:** By default, new files may not have "executable" permissions, meaning the system doesn't trust them to run as programs.
    
- **The Fix:** You can view permissions using the command `ls -l`. To allow the script to run, use the command `chmod +x filename.sh` to add the executable (`x`) permission.
    

#### **5. Key Commands Learned**

- `which shell`: Verifies you are using the Bash shell.
    
- `echo [text]`: Prints text to the screen.
    
- `nano [filename]`: Opens a file in the text editor.
    
- `chmod +x [filename]`: Makes a file executable.
    
- `ls -l`: Lists files with their detailed permissions.

---
# **"BASH scripting will change your life"** by **NetworkChuck** [Lien](https://youtu.be/7qd5sqazD7k)

#### **1. The Goal: `bestdayever.sh`**

- The project for this video is creating a "Bash Butler" script named `bestdayever.sh`.
    
- The script is designed to greet you, compliment you, and provide useful system information every morning.
    

#### **2. Variables**

- **Concept:** A variable is a container for storing data that can change. Instead of hard-coding a name like "Chuck" everywhere, you define it once.
    
- **Syntax:** `name="Patricia"` (No spaces around the equals sign).
    
- **Usage:** You access the variable using the dollar sign: `echo "Good morning $name"`.
    
- **Benefit:** Changing the variable at the top of the script updates it everywhere else instantly.
    

#### **3. Interactive Input (`read`)**

- **Concept:** Instead of defining the name inside the script, you can ask the user to type it in while the script is running.
    
- **Command:** `read name`
    
- **How it works:** The script pauses, waits for the user to type something and press Enter, and stores that text in the `$name` variable.
    

#### **4. Positional Arguments**

- **Concept:** You can pass data into the script _at the exact moment_ you run it, without stopping to ask the user.
    
- **Syntax:** `$1` represents the first word typed after the script name, `$2` is the second, and so on.
    
- **Example:**
    
    - Script: `name=$1` and `compliment=$2`
        
    - Execution: `./bestdayever.sh Abby Eyes`
        
    - Result: The script automatically sets `$name` to "Abby" and `$compliment` to "Eyes".
        

#### **5. Command Substitution**

- **Concept:** You can store the _output_ of a Linux command inside a variable to use it later.
    
- **Syntax:** `variable=$(command)`
    
- **Examples used in the video:**
    
    - `user=$(whoami)`: Stores the current username.
        
    - `day=$(date)`: Stores the current date and time.
        
    - `whereami=$(pwd)`: Stores the current directory.
        
- **Result:** The script can now say things like: _"You are logged in as root and today is Tuesday."_

___

# **"this BASH script will make you a MILLIONAIRE"** by **NetworkChuck** [Lien](https://youtu.be/19nN9vgcgmU)

#### **1. The Goal: `getrichquick.sh`**

- The project is to create a script that asks for your name and age, and then "calculates" the exact age you will become a millionaire.
    
- The calculation uses a random number generator to make the result different every time.
    

#### **2. The `$RANDOM` Variable**

- **Concept:** Linux has a built-in variable called `$RANDOM` that automatically generates a random number between 0 and 32,767 every time you use it.
    
- **Problem:** This range is too large for an age calculation (you don't want to become a millionaire at 30,000 years old).
    

#### **3. Arithmetic Expressions (Doing Math)**

- **Syntax:** To do math in Bash, you use double parentheses with a dollar sign: `$(( math ))`.
    
- **Example:** `echo $(( 2 + 2 ))` will print `4`.
    
- **Note:** Bash only handles whole numbers (integers), not decimals. `10 / 3` will give `3`, not `3.33`.
    

#### **4. The Modulo Operator (`%`)**

- **Concept:** To limit the size of the random number, the video introduces the Modulo operator, which gives the **remainder** of a division problem.
    
- **Usage:** `$(( $RANDOM % 10 ))` divides the random number by 10 and gives the remainder. This guarantees a result between **0 and 9**.
    
- **Application:** The script adds a random number (limited to a range like 0-14) to your current age to predict your "millionaire age."
    
    - Logic: `getrich=$(( ($RANDOM % 15) + $age ))`
        

#### **5. Environment Variables**

- **Child Processes:** By default, variables you create in your terminal are **not** visible to scripts you run (scripts are "children" of the shell).
    
- **`export`:** To fix this, you use the command `export variable_name`. This makes the variable an **Environment Variable**, accessible to all child processes/scripts.
    
- **Persistence (`.bashrc`):**
    
    - Variables disappear when you close the terminal.
        
    - To make them permanent, you add the export command to the `.bashrc` file in your home directory.
        
    - `.bashrc` is a hidden file that runs every time you open a new shell window.

---

# **"this BASH script will KILL you."** by **NetworkChuck** [Lien](https://youtu.be/Fq6gqi9Ubog)
#### **1. The Goal: `eldenring.sh`**

- The project is to build a text-based version of the difficult video game _Elden Ring_.
    
- The game involves choosing a character class and fighting bosses (Beasts) by picking numbers. If you guess wrong, the script prints "You Died."
    

#### **2. Conditionals (If Statements)**

- **Concept:** Conditionals allow the script to change its behavior based on whether something is True or False.
    
- **Syntax:**
    
    - Starts with `if` and ends with `fi` (if backwards).
        
    - Uses double brackets `[[ ]]` for the test condition.
        
    - Example:
        
        Bash
        
        ```
        if [[ $coffee == "y" ]]; then
            echo "You are awesome"
        else
            echo "Leave right now"
        fi
        ```
        
- **`elif` (Else If):** Used to check multiple conditions in a row (e.g., If A is true, do X. If not, check if B is true...).
    

#### **3. Logical Operators**

- **`||` (OR):** The condition is true if _either_ side is true.
    
    - Used in the video to add a "cheat code." If the user guesses the number _OR_ types "coffee", they win.
        
- **`&&` (AND):** The condition is true only if _both_ sides are true.
    
    - Used to make battles harder (e.g., You must guess the number _AND_ your attack power must be high enough).
        

#### **4. Nested Ifs**

- **Concept:** Placing one `if` statement inside another.
    
- **Usage:** The script checks if you beat the boss. If you did, it _then_ checks if you are the "root" user. If you aren't root, you die anyway (simulating the game's difficulty).
    

#### **5. Case Statements**

- **Concept:** A cleaner way to handle multiple choices than writing a dozen `if/elif` statements.
    
- **Usage:** Used for selecting the starting character class (Samurai, Prisoner, Prophet).
    
- **Syntax:**
    
    Bash
    
    ```
    case $class in
        1) type="Samurai" ;;
        2) type="Prisoner" ;;
        *) echo "Invalid option" ;;
    esac
    ```
    
- **Benefit:** It acts like a "switcher," assigning different stats (HP, Attack) based on the single number the user selects.

---

# This video, titled **"a BASH script PUSH-UP counter "** by **NetworkChuck** [Lien](https://youtu.be/nW9M0MQinfg )

#### **1. The Goal: `pushups.sh`**

- The project is to build a script that forces you to do exercise (push-ups or squats) by asking for input repeatedly until you reach a specific goal (e.g., 10 reps).
    

#### **2. While Loops**

- **Concept:** A loop that continues running _while_ a specific condition is True.
    
- **Syntax:**
    
    Bash
    
    ```
    while [[ $x -le 10 ]]; do
        read -p "Press enter to do a pushup"
        (( x++ ))
    done
    ```
    
- **Infinite Loops:** The video warns about `while true`, which runs forever unless you force it to stop (often used for background services or monitoring).
    

#### **3. Until Loops**

- **Concept:** The exact opposite of a While loop. It runs _until_ a condition becomes True (meaning it loops as long as the condition is False).
    
- **Syntax:**
    
    Bash
    
    ```
    until [[ $order == "coffee" ]]; do
        echo "Would you like coffee or tea?"
        read order
    done
    ```
    
- **Example:** A "coffee order" script that keeps asking "What do you want?" _until_ you finally type "coffee". If you type "tea" or "water", the condition (`order == coffee`) remains False, so the loop runs again.
    

#### **4. For Loops**

- **Concept:** Instead of waiting for a condition, a For loop runs once for every item in a list.
    
- **Syntax:** `for variable in list; do ... done`
    
- **Powerful Use Cases:**
    
    - **Range:** `for x in {1..10}` runs the loop 10 times.
        
    - **Pinging Domains:** You can make a list of websites (Google, Bing, Facebook) and have the script ping each one in sequence to see if they are up.
        
    - **Reading Files:** You can loop through lines in a text file. The video demonstrates this by reading a `cities.txt` file and checking the weather for each city using `wttr.in`.
        

#### **5. Controlling Loops (`break` and `continue`)**

- **`break`:** Specific command to immediately **exit** the loop.
    
    - _Example:_ A script that pings a server repeatedly; as soon as the server comes online, it `breaks` the loop to notify you.
        
- **`continue`:** Specific command to **skip** the rest of the current iteration and start the next one.
    
    - _Example:_ An "elevator" script that counts floors 1 to 20 but uses `continue` when it hits 13 to skip that superstitious number.