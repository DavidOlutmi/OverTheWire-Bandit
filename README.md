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
-  Use a file to identify the human-readable (ASCII) file.

-  Use find to locate a file with the correct size.

-  Display the file content with cat.

🔧 Commands Used
-  cd inhere
-  ls -alps
-  find. type f | xargs file
-  cat ./-file07

 ☁️ Output Explanation
-  The only file matching the given criteria contained the password.

<br>
Level 5 → 6
🎯 Objective
-  Find the password in the only human-readable file in the inhere directory. It's 1033 bytes in size, human readable,  and not executable.

🧠 Approach
-  Use a file to identify the human-readable (ASCII) file.

-  Use find to locate a file with the correct size.

-  Display the file content with cat.

🔧 Commands Used
-  cd inhere
-  ls -alps
-  find. -type f -size 1033c! -executable
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
Level 7 → 8
🎯 Objective:
- The password for the next level is stored in the file data.txt next to the word millionth

🧠 Approach:
- Use the Strings and grep command to find the line in the file that begins with "millionth"/

🔧 Commands Used:
- ls
- cat data.txt
- strings data.txt | grep "millionth"

☁️ Output Explanation
-  Only the line matching the given criteria contained the password

<br>
Level 8 → 9
🎯 Objective:
-  Find the only line in the data file that occurs only once.

🧠 Approach:
- Use sort to group duplicate lines.
- Pipe to uniq -u to display the unique line (the one that appears only once).

🔧 Commands Used:
- ls
- cat data.txt         
- sort data.txt | uniq -u
  
☁️ Output Explanation:
The file contained many repeated lines. By sorting and using uniq -u, we isolated the single unique line, which contained the password for the next level.

<br>
Level 9 → 10
🎯 Objective:
-  Find the only human-readable line that is preceded by multiple "="

🧠 Approach:
- Use strings and the grep command to find the line with the most "="
  
🔧 Commands Used:
- ls
- cat data.txt         
- strings data.txt | grep "="
  
☁️ Output Explanation:
The file contained many unreadable lines; the best way was to ignore all other lines and focus on the lines with the "="

<br>
Level 10 → 11
🎯 Objective:
-  The password for the next level is stored in the file data.txt, which contains base64 encoded data

🧠 Approach:
- Use the base64 command to decode the string
  
🔧 Commands Used:
-  base64 -d data.txt
  
☁️ Output Explanation:
The file contains only one line of base64 text that needs to be decoded.


<br>
Level 11 → 12
🎯 Objective:
-  The password for the next level is stored in the file data.txt, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions

🧠 Approach:
- Use a website called CyberCraft to decipher the text. 

<br>
Level 12 → 13
🎯 Objective:
-  

🧠 Approach:
- 
  
🔧 Commands Used:
-  
  
☁️ Output Explanation:
The file contains only one line of base64 text that needs to be decoded.
  


