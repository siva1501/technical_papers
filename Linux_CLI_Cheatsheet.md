# Linux CLI Cheatsheet

## 1. Basic Commands

| Command | Description | Example |
|---|---|---|
| `pwd` | Show current directory | `pwd` |
| `whoami` | Show current username | `whoami` |
| `date` | Display current date and time | `date` |
| `cal` | Display calendar | `cal` |
| `clear` | Clear terminal screen | `clear` |
| `history` | Show previously executed commands | `history` |
| `uname` | Display system information | `uname -a` |
| `hostname` | Display computer name | `hostname` |

## 2. Directory Commands

| Command | Description | Example |
|---|---|---|
| `ls` | List files and directories | `ls` |
| `ls -l` | Show detailed file information | `ls -l` |
| `ls -a` | Show hidden files | `ls -a` |
| `ls -lh` | Show file sizes in readable format | `ls -lh` |
| `cd` | Go to home directory | `cd` |
| `cd ..` | Move to parent directory | `cd ..` |
| `cd ~` | Move to home directory | `cd ~` |
| `cd /` | Move to root directory | `cd /` |
| `cd -` | Return to previous directory | `cd -` |

## 3. Creating Files and Directories

| Command | Description | Example |
|---|---|---|
| `mkdir` | Create a directory | `mkdir projects` |
| `mkdir -p` | Create nested directories | `mkdir -p projects/python/files` |
| `touch` | Create an empty file | `touch main.py` |
| `cat` | Display file contents | `cat main.py` |
| `nano` | Open a file in the Nano editor | `nano main.py` |

## 4. Copying, Moving and Removing

| Command | Description | Example |
|---|---|---|
| `cp` | Copy a file | `cp file.txt backup.txt` |
| `cp -r` | Copy a directory recursively | `cp -r project backup` |
| `mv` | Move a file or directory | `mv file.txt documents/` |
| `mv` | Rename a file | `mv old.txt new.txt` |
| `rm` | Remove a file | `rm file.txt` |
| `rm -r` | Remove a directory and its contents | `rm -r folder` |
| `rmdir` | Remove an empty directory | `rmdir folder` |

**Important:** Be careful when using `rm`. Deleted files may not be recoverable.

## 5. Reading File Contents

| Command | Description | Example |
|---|---|---|
| `cat` | Display the complete file | `cat file.txt` |
| `less` | Read a file page by page | `less file.txt` |
| `head` | Display the first 10 lines | `head file.txt` |
| `head -n 5` | Display the first 5 lines | `head -n 5 file.txt` |
| `tail` | Display the last 10 lines | `tail file.txt` |
| `tail -n 5` | Display the last 5 lines | `tail -n 5 file.txt` |
| `tail -f` | Follow file updates in real time | `tail -f app.log` |
| `wc` | Count lines, words and characters | `wc file.txt` |
| `wc -l` | Count lines | `wc -l file.txt` |
| `wc -w` | Count words | `wc -w file.txt` |
| `wc -c` | Count bytes | `wc -c file.txt` |

## 6. Searching Commands

| Command | Description | Example |
|---|---|---|
| `find` | Find files and directories | `find . -name "main.py"` |
| `grep` | Search for text inside files | `grep "Python" file.txt` |
| `grep -i` | Search without case sensitivity | `grep -i "python" file.txt` |
| `grep -n` | Display matching line numbers | `grep -n "Python" file.txt` |
| `grep -r` | Search recursively in directories | `grep -r "Python" .` |
| `which` | Find the location of a command | `which python` |
| `whereis` | Find binary, source and manual locations | `whereis python` |

## 7. File Permissions

| Command | Description | Example |
|---|---|---|
| `ls -l` | View file permissions | `ls -l` |
| `chmod` | Change file permissions | `chmod 755 file.sh` |
| `chmod +x` | Make a file executable | `chmod +x script.sh` |
| `chown` | Change file ownership | `sudo chown user file.txt` |
| `chgrp` | Change group ownership | `sudo chgrp users file.txt` |

### Permission Values

| Permission | Value | Meaning |
|---|---|---|
| Read | 4 | Read file contents |
| Write | 2 | Modify file contents |
| Execute | 1 | Execute a file |

Example:

`chmod 755 script.sh`

- Owner: Read, Write, Execute (7)
- Group: Read, Execute (5)
- Others: Read, Execute (5)

## 8. User and Group Commands

| Command | Description | Example |
|---|---|---|
| `whoami` | Show current user | `whoami` |
| `id` | Display user and group IDs | `id` |
| `groups` | Display groups of current user | `groups` |
| `sudo` | Execute a command with elevated privileges | `sudo apt update` |
| `su` | Switch user | `su username` |
| `passwd` | Change password | `passwd` |

## 9. System Information

| Command | Description | Example |
|---|---|---|
| `free -h` | Display memory usage | `free -h` |
| `df -h` | Display disk space usage | `df -h` |
| `du -sh` | Display directory size | `du -sh folder` |
| `top` | Display running processes | `top` |
| `ps` | Display running processes | `ps aux` |
| `kill` | Stop a process using its PID | `kill 1234` |
| `uptime` | Display system running time | `uptime` |
| `lscpu` | Display CPU information | `lscpu` |
| `lsblk` | Display block devices | `lsblk` |

## 10. Networking Commands

| Command | Description | Example |
|---|---|---|
| `ip a` | Display network interfaces and IP addresses | `ip a` |
| `ping` | Test network connectivity | `ping google.com` |
| `curl` | Transfer data from or to a URL | `curl https://example.com` |
| `wget` | Download files from the internet | `wget https://example.com/file.zip` |
| `hostname -I` | Display system IP addresses | `hostname -I` |

## 11. Package Management (Ubuntu)

| Command | Description |
|---|---|
| `sudo apt update` | Update package lists |
| `sudo apt upgrade` | Upgrade installed packages |
| `sudo apt install package_name` | Install a package |
| `sudo apt remove package_name` | Remove a package |
| `sudo apt purge package_name` | Remove a package and its configuration files |
| `sudo apt autoremove` | Remove unnecessary packages |
| `apt list --installed` | List installed packages |
| `apt search package_name` | Search for a package |

## 12. Redirection and Pipes

| Operator | Description | Example |
|---|---|---|
| `>` | Redirect output and overwrite a file | `echo "Hello" > file.txt` |
| `>>` | Append output to a file | `echo "Hello" >> file.txt` |
| `<` | Take input from a file | `sort < names.txt` |
| `|` | Pass output to another command | `ls -l \| grep ".py"` |
| `2>` | Redirect error output | `command 2> error.txt` |
| `&>` | Redirect standard output and errors | `command &> output.txt` |

## 13. Useful Text Processing Commands

| Command | Description | Example |
|---|---|---|
| `echo` | Print text | `echo "Hello World"` |
| `sort` | Sort lines alphabetically | `sort names.txt` |
| `sort -r` | Sort in reverse order | `sort -r names.txt` |
| `uniq` | Remove adjacent duplicate lines | `uniq names.txt` |
| `cut` | Extract specific fields | `cut -d "," -f 1 data.csv` |
| `sed` | Search and replace text | `sed 's/old/new/g' file.txt` |
| `tr` | Translate or delete characters | `echo "hello" \| tr 'a-z' 'A-Z'` |

## 14. Keyboard Shortcuts

| Shortcut | Description |
|---|---|
| `Ctrl + C` | Stop the running command |
| `Ctrl + Z` | Suspend the running process |
| `Ctrl + D` | Exit the terminal or send EOF |
| `Ctrl + L` | Clear the terminal screen |
| `Ctrl + A` | Move cursor to the beginning of the line |
| `Ctrl + E` | Move cursor to the end of the line |
| `Ctrl + U` | Delete text before the cursor |
| `Ctrl + K` | Delete text after the cursor |
| `Ctrl + R` | Search command history |
| `Tab` | Auto-complete commands and file names |
| `↑` | Access previous command |
| `↓` | Access next command |

## 15. Important CLI Concepts

| Concept | Meaning |
|---|---|
| Terminal | Application used to interact with the shell |
| Shell | Program that interprets commands |
| CLI | Command Line Interface |
| Root directory `/` | Starting point of the Linux filesystem |
| Home directory `~` | Current user's personal directory |
| Absolute path | Complete path starting from `/` |
| Relative path | Path based on the current directory |
| Hidden file | File whose name starts with `.` |
| Process | A running program |
| PID | Process ID |
| Permission | Controls who can read, write or execute files |
| Environment variable | Variable that stores system or user configuration |