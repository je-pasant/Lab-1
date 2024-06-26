# Lab-1
### Task 1: Create a User Account

**Question:**
Create a user account with the following attributes:
- Username: xxxx
- Fullname/comment: xxx xxx
- Password: xxxxx

**Solution:**
```bash
sudo useradd -m -c "xxx xxx" -p $(openssl passwd -1 xxxxx) xxxx
```

### Task 2: Create Another User Account

**Question:**
Create a user account with the following attributes:
- Username: baduser
- Fullname/comment: Bad User
- Password: baduser

**Solution:**
```bash
sudo useradd -m -c "Bad User" -p $(openssl passwd -1 baduser) baduser
```

### Task 3: Create Supplementary Group

**Question:**
Create a supplementary (Secondary) group called pgroup with group ID of 30000.

**Solution:**
```bash
sudo groupadd -g 30000 pgroup
```

### Task 4: Create Another Supplementary Group

**Question:**
Create a supplementary group called badgroup.

**Solution:**
```bash
sudo groupadd badgroup
```

### Task 5: Add User to Supplementary Group

**Question:**
Add the user 'islam' to the 'pgroup' group as a supplementary group.

**Solution:**
```bash
sudo usermod -aG pgroup islam
```

### Task 6: Modify User's Password

**Question:**
Modify the password of the user 'islam' to 'password'.

**Solution:**
```bash
sudo passwd islam
```

### Task 7: Set Password Expiry

**Question:**
Modify 'islam' account so the password expires after 30 days.

**Solution:**
```bash
sudo chage -M 30 islam
```

### Task 8: Lock User Account

**Question:**
Lock the user account 'baduser' so they can't log in.

**Solution:**
```bash
sudo usermod -L baduser
```

### Task 9: Delete User Account

**Question:**
Delete the user account 'baduser'.

**Solution:**
```bash
sudo userdel -r baduser
```

### Task 10: Delete Supplementary Group

**Question:**
Delete the supplementary group called 'badgroup'.

**Solution:**
```bash
sudo groupdel badgroup
```

### Task 11: Create and Configure Folder

**Question:**
Create a folder called 'myteam' in your home directory and change its permissions to read-only for the owner.

**Solution:**
```bash
mkdir ~/myteam
chmod 400 ~/myteam
```

### Task 12: Permissions and Access Control

**Question:**
Log out and log in as another user. Try to access the folder 'myteam' using the `cd` command. Explain the result.

**Solution:**
```bash
cd ~/myteam
# You should receive a permission denied error if permissions are set correctly.
```

### Task 13: File Permissions Modification

**Question:**
Change the permissions of 'oldpasswd' file to give owner read and write permissions, group write and execute permissions, and execute permission only for others using `chmod` in two different ways.

**Solution:**
```bash
chmod u=rw,g=wx,o=x oldpasswd
# Or
chmod 751 oldpasswd
```

### Task 14: Default Permissions

**Question:**
What are the maximum default permissions for a file and a directory when just created?

**Solution:**
- File: 666 (rw-rw-rw-)
- Directory: 777 (rwxrwxrwx)

### Task 15: Minimum Permissions Required

**Question:**
What are the minimum permissions needed for the following actions:
- Copy a directory (source directory and target parent directory permissions)
- Copy a file (source file and target parent directory permissions)
- Delete a file
- Change to a directory
- List a directory content (`ls` command)
- View a file content (`more`/`cat` command)
- Modify a file content

**Solution:**
- Copy a directory: Source (rx) and Target parent (wx)
- Copy a file: Source (r) and Target parent (wx)
- Delete a file: Write permission on the file and parent directory
- Change to a directory: Execute permission on the directory
- List directory content: Read permission on the directory
- View file content: Read permission on the file
- Modify file content: Write permission on the file

### Task 16: File Creation and Editing

**Question:**
Create a file with permission 444. Try to edit and remove it. Note the outcomes.

**Solution:**
```bash
touch file.txt
chmod 444 file.txt
# Editing: You can't edit the file.
# Removing: You can't remove the file.
```

### Task 17: File and Directory Permissions

**Question:**
What is the difference between the "x" permission for a file and for a directory?

**Solution:**
- For a file, "x" permission allows executing the file as a program.
- For a directory, "x" permission allows accessing (entering) the directory and its contents.

### Task 18: Vi Editor Usage

**Question:**
Using `vi`, write your CV in the file 'mycv'. Include your name, age, school, college, experience, etc. Then perform the following actions without using arrows:
- Show all line numbers
- Search for the word 'age'
- Move to line 5
- Delete the current line and line 5

**Solution:**
```bash
vi mycv
:set number
/age
5G
dd5Gdd
```

### Task 19: Shell Operations

**Question:**
List the available shells in your system.
List the environment variables in your current shell.
List all environment variables for the Bash shell.

**Solution:**
```bash
cat /etc/shells
printenv
env
```

### Task 20: Shell Configuration

**Question:**
What are the commands to list the value of a specific variable?
Display your current shell name.
State the initialization files for `sh`, `ksh`, and `bash`.

**Solution:**
```bash
echo $VARIABLE_NAME
echo $SHELL
/etc/profile (sh), /etc/profile, ~/.profile (ksh), /etc/bashrc, ~/.bashrc (bash)
```

### Task 21: Shell Customization

**Question:**
Edit your profile to display the date at login and change your prompt permanently.

**Solution:**
```bash
# Edit ~/.bashrc or ~/.bash_profile to include desired changes.
# Example: Add `date` command for date display and customize PS1 for prompt.
```

### Task 22: Escape Character Usage

**Question:**
Execute the command `echo \`, and explain the purpose of `\`. What is the prompt `>` and how can you change it to `:`?

**Solution:**
```bash
echo \
# The `\` is an escape character used to escape special characters.
# The prompt `>` is the secondary prompt (PS2) in Bash, used in multiline commands. Change it with `PS2=':'`.

### Task 23: Bash Alias

**Question:**
Create a Bash shell alias named `ls` for the `ls -l` command.

**Solution:**
```bash
alias ls='ls -l'
```
