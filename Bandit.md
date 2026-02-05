Level 0 :

<img width="1285" height="134" alt="Pasted image 20260124151441" src="https://github.com/user-attachments/assets/9fb92a71-0786-4b57-a17e-da552726f0dc" />

Level 1 :

<img width="349" height="137" alt="Pasted image 20260124153451" src="https://github.com/user-attachments/assets/8036e220-002e-48e7-8ca7-51c1d5f109ec" />

to display the content of a hyphenated file name

A **hyphenated file** simply refers to a file that uses hyphens (dashes) to separate words in its filename instead of spaces or underscores

Level 3 :

<img width="377" height="92" alt="Pasted image 20260124154302" src="https://github.com/user-attachments/assets/2c0ac71f-9e0b-405f-83ce-c5b201b6a132" />

Level 4 :

<img width="476" height="235" alt="Pasted image 20260124160608" src="https://github.com/user-attachments/assets/01b30a00-b954-43be-ac82-6d2d9df83b3e" />

<img width="542" height="305" alt="Pasted image 20260124160704" src="https://github.com/user-attachments/assets/4fa5ec8a-0cb6-4d16-a15a-c6c693ffdb22" />

Level 5 :

<img width="952" height="163" alt="Pasted image 20260124161751" src="https://github.com/user-attachments/assets/66a7c9be-3d5c-4356-b9e4-823a0d5d9be0" />

<img width="1077" height="573" alt="Pasted image 20260124161853" src="https://github.com/user-attachments/assets/67a992b6-9d52-4c01-9c07-de7d3ae3435f" />

<img width="578" height="274" alt="Pasted image 20260124161927" src="https://github.com/user-attachments/assets/97db3c10-cdb9-46ec-8f80-df5bc61ef232" />

Level 6 :

<img width="946" height="431" alt="Pasted image 20260124205000" src="https://github.com/user-attachments/assets/8fa6fd15-507f-4cdb-a47d-6a10cb214f52" />

<img width="368" height="44" alt="Pasted image 20260124205039" src="https://github.com/user-attachments/assets/76e360b4-3ef5-4a5f-8cdb-c6eb76f6f0d0" />

Level 7 :

<img width="413" height="140" alt="Pasted image 20260124212509" src="https://github.com/user-attachments/assets/573bb77f-1f7b-4e04-881e-429df9687ced" />

***The true power of Linux is the " | " (pipe), which takes the output of the left command and gives it to the right command.*

Level 8 :

<img width="371" height="144" alt="Pasted image 20260125095508" src="https://github.com/user-attachments/assets/3e5b3c54-6bb4-4b06-8018-72a09b24cef3" />

Level 9 :

<img width="382" height="335" alt="Pasted image 20260125095809" src="https://github.com/user-attachments/assets/fbad531c-7091-40fe-aa55-bbc73eb2491a" />

Level 10 :

<img width="641" height="177" alt="Pasted image 20260125100525" src="https://github.com/user-attachments/assets/2082242a-8613-4895-81bb-f689491ba081" />

The password was encoded so we decode it with -d option in base64 commande .

Level 11 :

<img width="400" height="315" alt="Pasted image 20260125101811" src="https://github.com/user-attachments/assets/2eff9eb6-6d68-4be8-acca-525a6e680248" />

Level 12 :

We can make a directory in /tmp by this commend

<img width="383" height="36" alt="Pasted image 20260125131349" src="https://github.com/user-attachments/assets/ffc85e86-38f6-4b46-bc7a-d8b0a127e1f7" />

Or by (In working directory we have more permissions to make file modify ...)

<img width="891" height="143" alt="Pasted image 20260125131659" src="https://github.com/user-attachments/assets/ace33c40-97e6-4695-90b1-e3cfb99963be" />

<img width="638" height="22" alt="Pasted image 20260126175058" src="https://github.com/user-attachments/assets/b1b3006b-cb1b-4030-a29d-b49763c94df7" />

after that we need a command to see what is the the type of file :

The command : file name_file

The file is hexdump so we need to reverse it and save it on a file :

<img width="958" height="261" alt="Pasted image 20260126175513" src="https://github.com/user-attachments/assets/756c18a3-1e9f-4924-b7cd-2988db29e18b" />

After that we see the file compressed with gzip  so we need to decompressed but before that we need to change the extension to gz :

<img width="959" height="173" alt="Pasted image 20260126175756" src="https://github.com/user-attachments/assets/a878c036-051f-4934-9388-1eaecf7eb142" />

The same this with the bzip2 compressed file :

<img width="944" height="152" alt="Pasted image 20260126180327" src="https://github.com/user-attachments/assets/16e57bb5-7265-4ad9-8323-489565ca1cc7" />

After that we see another type of file it is tar archive so we do the same steps but instead of decompression we extract the file :

<img width="479" height="122" alt="Pasted image 20260126180951" src="https://github.com/user-attachments/assets/9421e04d-91fa-4f55-b2fa-980bf216dffb" />

And we do the same steps until we find an ASCII file that contain the password

Level 13 :

In bandit we can't connect from local host

<img width="944" height="451" alt="Pasted image 20260127120936" src="https://github.com/user-attachments/assets/93452d36-a348-451d-bfe9-144eccd17a27" />

So we need to copy the privet key in our Kali Linux and connect externally

<img width="935" height="298" alt="Pasted image 20260127121303" src="https://github.com/user-attachments/assets/f2b7b07b-fb92-4d03-904e-a92f5cd11dd0" />

we use this command to connect with the private key but before we need to let the private key read it only by our user :

Run this command in your terminal:

```
chmod 600 sshkey.private

```

### Why `600`?

* **6**: You (owner) can **Read** and **Write**.
* **0**: The group can do **nothing**.
* **0**: Others can do **nothing**.

```
ssh -i sshkey.private -p 2220 user@host 

```

After that we have permission read the file :

<img width="440" height="65" alt="Pasted image 20260127203816" src="https://github.com/user-attachments/assets/41310028-a9dc-4897-9128-8036742a557b" />

Level 14&15 :

In the first we can use telnet or nc to connect to the port because it is unencrypted after that we enter the password for our current level but in the second we need to use the  openssl s_client command to connect to the SSL/TLS "handshake" and we enter the password

Level 16 :

We use this command to see the port open in this range

<img width="620" height="242" alt="Pasted image 20260128094315" src="https://github.com/user-attachments/assets/b4ca7268-03ff-438d-b7c1-5dbc8e872d59" />

After that we test to connect with port  we this command

```
openssl s_client -connect localhost:port -quiet

```

until the a port give us a credential that is a private key :

<img width="617" height="419" alt="Pasted image 20260129152849" src="https://github.com/user-attachments/assets/4e8d4a88-ed93-4ae6-a5ee-c132bc656bc7" />

So we copy it and nano it in a file and we change the permission


<img width="367" height="116" alt="Pasted image 20260129153022" src="https://github.com/user-attachments/assets/0cbdb84c-59b9-4031-9368-0629a443812b" />


<img width="623" height="368" alt="Pasted image 20260129153052" src="https://github.com/user-attachments/assets/37de4673-eaa4-4e52-bc53-11360731fcbb" />

And now we have permission to view the password of our current level :

<img width="742" height="302" alt="Pasted image 20260129153239" src="https://github.com/user-attachments/assets/b9c76fb7-4c69-4107-be43-537937d49502" />

Level 18 :

### 🛠️ Common CTF Trick: The "Login Block"

If you log into a Bandit level and the connection immediately closes, a script in `.bashrc` or `.profile` might be exiting your session automatically. You can sometimes bypass this by forcing SSH to run a different shell: #commands

```
ssh banditX@localhost -t "/bin/sh"

```

<img width="590" height="291" alt="Pasted image 20260129175118" src="https://github.com/user-attachments/assets/1db6cf68-b0aa-42fe-a8f6-c6d21fcf342b" />

And we cat it

Level 19 :

##### Guide : [[Setuid binary]]

<img width="506" height="124" alt="Pasted image 20260130155017" src="https://github.com/user-attachments/assets/671de462-bb86-4923-a10f-0dc93f48c94a" />

<img width="380" height="38" alt="Pasted image 20260130155637" src="https://github.com/user-attachments/assets/3d94b8ff-1a40-4762-ab64-68dff40cce3d" />

Level 20 :

The mistake that i do that i was trying to connect to a port that is already be used so i need to chose a port the isn't be used and listening not connecting because the other command that is trying to connect :

<img width="949" height="68" alt="Pasted image 20260131161139" src="https://github.com/user-attachments/assets/7e3abdef-f69d-43f5-a31c-c934d59c4f71" />

So the first step to get the flag is to now what port are not used :

<img width="578" height="217" alt="Pasted image 20260131161300" src="https://github.com/user-attachments/assets/daac327b-53d9-4b34-821d-3d7a9808e813" />

After that we start listening to the port by netcat and connecting after that we send the password of the current level and we get the one of the next level :

<img width="394" height="100" alt="Pasted image 20260131161514" src="https://github.com/user-attachments/assets/014e5002-dc7a-46eb-a1ea-a4fb94503e09" />

<img width="334" height="52" alt="Pasted image 20260131161551" src="https://github.com/user-attachments/assets/25b08d3e-69e3-4363-9437-e1f3f98b0c61" />

Level 22 :

<img width="738" height="391" alt="Pasted image 20260201095901" src="https://github.com/user-attachments/assets/d0e5be4c-e570-4ae4-9ffd-b65ec278664f" />

<img width="507" height="58" alt="Pasted image 20260201100217" src="https://github.com/user-attachments/assets/ac3b2b38-646a-4593-89d5-f918b06b828c" />

Level 23 :

<img width="734" height="453" alt="Pasted image 20260201101506" src="https://github.com/user-attachments/assets/660516e8-b6ce-47f0-afdb-f7dfe2bdbed6" />

So i need to find a command that give me the same output as whoami in user bandit23 :

<img width="731" height="281" alt="Pasted image 20260201101636" src="https://github.com/user-attachments/assets/71a0581e-c89a-4503-8551-b7650d55c6c1" />

Level 23 :

<img width="721" height="439" alt="Pasted image 20260202102847" src="https://github.com/user-attachments/assets/548c4275-d31a-4efd-88d0-d9d692a4863a" />

##### Explication :

### **Line-by-Line Explanation**

1. **`myname=$(whoami)`**
* Since the cron job runs as `bandit24`, this variable becomes `bandit24`.


2. **`cd /var/spool/"$myname"/foo`**
* The script moves into the directory: **/var/spool/bandit24/foo**.
* *Note:* This is the "drop zone" where you need to put your payload.


3. **`for i in * .*;`**
* It starts a loop that looks at **every single file** in that directory, including hidden ones (starting with `.`).


4. **`owner="$(stat --format "%U" "./$i")"`**
* It checks who owns the file currently being looked at.


5. **`if [ "${owner}" = "bandit23" ]`**
* **The Vulnerability:** It checks if the file is owned by **YOU** (`bandit23`).
* If you (bandit23) put a script in there, this condition becomes `TRUE`.


6. **`timeout -s 9 60 "./$i"`**
* **The Execution:** If you own the file, the script (running as `bandit24`) executes your file!.
* It gives it a 60-second time limit before killing it.


7. **`rm -rf "./$i"`**
* **The Cleanup:** Immediately after trying to run the file, it **deletes it**.
* This happens whether the script ran successfully or not.



---

### **How to beat this level**

You (bandit23) cannot read the password for bandit24 directly. However, since **bandit24** is running this script, anything executed by this script runs with **bandit24's permissions**.

1. **Create a script** in a temporary folder (e.g., `/tmp/myscript.sh`) that copies the password to a place you can read.
* *Example command to put inside:* `cat /etc/bandit_pass/bandit24 > /tmp/password123`


2. **Make it executable:** `chmod 777 /tmp/myscript.sh`.
3. **Make it readable/writable:** Make sure the output file (`/tmp/password123`) is writable by everyone so the bandit24 user can write to it.
4. **Copy it to the spool:** Copy your script into `/var/spool/bandit24/foo`.
5. **Wait:** Within 60 seconds, the cron job will run your script, copy the password, and then delete your script.
6. **Read the password:** Check `/tmp/password123`.

Level 24 :

The first this i do is creating q script in /tmp/ to have the permission after that i execute it

<img width="413" height="112" alt="Pasted image 20260202111029" src="https://github.com/user-attachments/assets/21df0557-8f5e-4df9-8f29-263d6f864b51" />

Level 25 :

### **The Problem**

The shell for user `bandit26` is not `/bin/bash` but a custom script that disconnects you immediately after showing you some ASCII art text. If you try to connect normally, the window closes right away.

### **The Solution Step-by-Step**

#### **1. Shrink your terminal**

This is the crucial step. The script uses the `more` command to display the text. `more` only stops (pauses) if the text is **longer** than the height of your window.

* Before running the SSH command, resize your terminal window so it is very small (about 5 or 6 lines high).

#### **2. Connect**

Start the connection using the SSH key you found in the previous level (in `bandit25`):

Bash

```
ssh -i bandit26.sshkey bandit26@localhost

```

*(If you are on your Kali machine and not on the bandit25 server, connect to bandit25 first).*

#### **3. Trap "more"**

Because your window is tiny, the text will not be able to display entirely.

* You will see `--More--` at the bottom of the screen. The script is now paused, waiting for you to press Space.
* **DO NOT PRESS SPACE.**

#### **4. Launch `vi**`

The `more` command has a hidden feature: if you press **`v`**, it launches the text editor **`vi`** on the file currently being read.

* Press the **`v`** key. You are now inside the `vi` editor.

#### **5. The Escape (Jailbreak)**

Once inside `vi`, you can execute system commands.

* Type `:set shell=/bin/bash` and press **Enter**.
*(This sets the default shell of `vi` to Bash).*
* Type `:shell` and press **Enter**.
*(This launches the shell you just configured).*

<img width="420" height="136" alt="Pasted image 20260202142519" src="https://github.com/user-attachments/assets/354e89c1-2fff-4ffb-a125-4de63b451674" />

Level 27 :

<img width="626" height="196" alt="Pasted image 20260202142746" src="https://github.com/user-attachments/assets/b33956b0-7a36-48e7-8efb-b695977f3f99" />

Level 28 :

<img width="755" height="314" alt="Pasted image 20260202182244" src="https://github.com/user-attachments/assets/a960631a-7513-4a8f-927f-441a4e3f3ef2" />

<img width="545" height="220" alt="Pasted image 20260202182313" src="https://github.com/user-attachments/assets/7248840c-2b19-46f0-aec7-78baf6abecb7" />

Level 29 :

<img width="733" height="292" alt="Pasted image 20260202182819" src="https://github.com/user-attachments/assets/8bb981cb-7f10-4901-8666-7dd5e7f4f8b3" />

<img width="391" height="352" alt="Pasted image 20260202182840" src="https://github.com/user-attachments/assets/e8a3bb3d-aad4-4ee5-81a7-3a5d21dae334" />

The password is hided so we try to see the other versions of this note to see if the ode was righted by mistake

<img width="762" height="321" alt="Pasted image 20260202183017" src="https://github.com/user-attachments/assets/e0c156ff-388f-4566-a794-9a56f4cb1edf" />

Level 30 :

<img width="680" height="289" alt="Pasted image 20260203094632" src="https://github.com/user-attachments/assets/4820ce69-0b44-43d8-a3dc-c4f726a2397f" />

<img width="533" height="311" alt="Pasted image 20260203094731" src="https://github.com/user-attachments/assets/443fb985-d690-49f2-8040-188017bc4510" />

Level 31 :

<img width="587" height="377" alt="Pasted image 20260203101507" src="https://github.com/user-attachments/assets/bb6216de-b1a0-4dad-858e-4c8f8fa5dcf5" />

Level 32 :

<img width="524" height="482" alt="Pasted image 20260203105110" src="https://github.com/user-attachments/assets/6951d460-ab49-4ecc-a98f-01a4a14f3256" />

So here we have a git ignore that that filter certain files such that they are not pushed

So we will use a command that force to add a file with the txt extension

<img width="626" height="379" alt="Pasted image 20260203105600" src="https://github.com/user-attachments/assets/1dcc5f3f-83ef-4ae6-b468-e79871d5fecc" />

<img width="586" height="263" alt="Pasted image 20260203105630" src="https://github.com/user-attachments/assets/a7949d11-e662-447c-b73a-bb94445f903c" />

Every time you save a snapshot (commit) in Git, it stamps it with the author's **Name** and **Email**. Since this is the first time you are running Git on this machine, you haven't configured this "Identity Card" yet

<img width="574" height="475" alt="Pasted image 20260203105757" src="https://github.com/user-attachments/assets/b734e7de-f6ea-4b01-9053-3aef15df2447" />

Level 33 :

### **The Problem: The Uppercase Shell**

When you log in, you are trapped in a special shell. Whatever you type is instantly converted to **UPPERCASE** before being executed.

* If you type `ls`, the shell runs `LS`.
* Since Linux commands are case-sensitive (`ls` is not `LS`), every command returns an error like: `sh: 1: LS: not found`.

### **The Solution**

You need to trick the shell into running a command that spawns a *new* standard shell. We do this using a shell variable.

**Step 1: The Magic Command**

Type the following character sequence and press Enter:

Bash

```
$0

```

**Step 2: Verify**

You will see a normal prompt (usually just `$`).

Try typing `ls` or `id`. If it works without errors, you have escaped!

### **How it works**

* **`$0`** is a special variable in Linux that holds the **name of the current program** (the shell itself).
* Usually, the underlying shell is `sh` or `bash`.
* When you type `$0`, the shell expands the variable *first*. It sees `sh` (which is lowercase).
* It then executes `sh`.
* This launches a **new** shell instance inside the restricted one. This new shell does not have the "force uppercase" script running, so you are free.

<img width="360" height="64" alt="Pasted image 20260203113005" src="https://github.com/user-attachments/assets/533ac382-a131-4997-a454-7d21f3849efd" />

<img width="707" height="152" alt="Pasted image 20260203113040" src="https://github.com/user-attachments/assets/f3a30260-a8e2-40f4-b30c-4613da58e57c" />

There is a simple method that is :

<img width="301" height="101" alt="Pasted image 20260203113146" src="https://github.com/user-attachments/assets/ae0cf0af-8434-47cb-a627-c024056d88d8" />

Level 34 :

<img width="959" height="547" alt="Pasted image 20260203114658" src="https://github.com/user-attachments/assets/e95ac9a9-db67-4124-bcab-934b489eb979" />
