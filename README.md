# OverTheWire-Bandit
This is an ongoing walkthrough and personal learning log for the OverTheWire: Bandit wargame. This project documents my progress as I build foundational skills toward becoming a SOC Analyst and later pivot into Security Engineering.

⚙️ Tools Used
-  SSH
-  Linux Command Line
-  Basic Bash Utilities:
    cat, ls, file, find, grep, base64, xxd, strings, sort, uniq, tar, gzip, bzip2, etc.

📚 Table of Contents
Level 0 → 1

Level 1 → 2

Level 2 → 3

Level 3 → 4

Level 4 → 5

Level 5 → 6

Level 6 → 7

Level 7 → 8

Level 8 → 9

Level 9 → 10

<br>
<br>

Level 0 → 1
🎯 Objective:
-  Connect to the game using SSH and find the password in a file named readme.

🧠 Approach:
-  SSH into the server with the provided credentials and read the file.

🔧 Commands Used:
-  ssh bandit0@bandit.labs.overthewire.org -p 2220
-  cat readme
  
☁️ Output Explanation:
-  The file readme contained the password for the next level.

<br>
Level 1 → 2
🎯 Objective:
-  Find the password stored in a file named -.

🧠 Approach:
-  Use ./- to avoid confusion with stdin.

🔧 Commands Used:
-  cat ./-
  
☁️ Output Explanation:
-  The command displayed the password inside the file named -.

<br>
Level 2 → 3
🎯 Objective:
-  Find the password stored in a file with spaces in its name.

🧠 Approach:
-  Escape the spaces in the filename using \ or wrap the name in quotes.

🔧 Commands Used:
-  ls -alps
-  cat "spaces in this filename"
☁️ Output Explanation
-  The password was stored in a file with spaces in its name, and cat displayed it.

<br>

Level 3 → 4
🎯 Objective
-  Find the password stored in a hidden file in the inhere directory.

🧠 Approach
-  Enter the inhere directory and list all files, including hidden ones.

🔧 Commands Used
-  cd inhere
-  ls -alps
-  cat .hidden
☁️ Output Explanation
-  .hidden is a hidden file containing the password.

<br>
Level 4 → 5
🎯 Objective
-  Find the password in the only human-readable file in the inhere directory.

🧠 Approach
-  Use file to identify the human-readable (ASCII) file.

-  Use find to locate a file with the correct size.

-  Display the file content with cat.

🔧 Commands Used
-  cd inhere
-  ls -alps
-  find . type f | xargs file
-  cat ./-file07

 ☁️ Output Explanation
-  The only file matching the given criteria contained the password.

<br>
Level 5 → 6
🎯 Objective
-  Find the password in the only human-readable file in the inhere directory. It's 1033 bytes in size, human readable,  and not executable.

🧠 Approach
-  Use file to identify the human-readable (ASCII) file.

-  Use find to locate a file with the correct size.

-  Display the file content with cat.

🔧 Commands Used
-  cd inhere
-  ls -alps
-  find . -type f -size 1033c ! -executable
-  cat .maybehere07/.file2
  
☁️ Output Explanation
-  The only file matching the given criteria contained the password

<br>
Level 6 → 7
🎯 Objective
-  Find the password in a file with properties owned by user bandit7, owned by group bandit6, 33 bytes in size.

🧠 Approach

-  Use find to locate a file with the correct size, owner, and group.

-  Display the file content with cat.

🔧 Commands Used
-  ls -alps
- find / -type f -user bandit7 -group bandit6 -size 33c
- cat /var/lib/dpkg/info/bandit7.password
  
☁️ Output Explanation
-  The only file matching the given criteria contained the password

<br>
Level 6 → 7
🎯 Objective:
-  Find the password in a file with properties owned by user bandit7, owned by group bandit6, 33 bytes in size.

🧠 Approach:

-  Use find to locate a file with the correct size, owner, and group.

-  Display the file content with cat.

🔧 Commands Used:
-  ls -alps
- find / -type f -user bandit7 -group bandit6 -size 33c
- cat /var/lib/dpkg/info/bandit7.password
  
☁️ Output Explanation
-  The only file matching the given criteria contained the password
