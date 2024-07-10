# Lab-1
### 1:Create a user account with the following attributes:
- Username: BB
- Fullname/comment: Basant Ehab
- Password: xxxxx
  
```bash
sudo useradd -c "Basant Ehab" BB
sudo passwd BB

```

### 2: Create a user account with the following attributes:
- Username: baduser
- Fullname/comment: Bad User
- Password: baduser

```bash
sudo useradd -c "Bad User" baduser
sudo passwd baduser 
```

### 3: Create a supplementary (Secondary) group called pgroup with group ID of 30000.


```bash
sudo groupadd -g 30000 pgroup
```

###  4: Create a supplementary group called badgroup.

```bash
sudo groupadd badgroup
```

###  5: Add the user 'islam' to the 'pgroup' group as a supplementary group.

```bash
sudo usermod -aG pgroup islam
```

###  6: Modify the password of the user 'islam' to 'password'.

```bash
sudo passwd islam
```

###  7: Modify 'islam' account so the password expires after 30 days.

```bash
sudo chage -M 30 islam
```

###  8: Lock the user account 'baduser' so they can't log in.

```bash
sudo usermod -L baduser
```

###  9: Delete the user account 'baduser'.

```bash
sudo userdel -r baduser
```

###  10: Delete the supplementary group called 'badgroup'.

```bash
sudo groupdel badgroup
```

###  11: Create a folder called 'myteam' in your home directory and change its permissions to read-only for the owner.

```bash
mkdir myteam
chmod 400 myteam
```

###  12: Log out and log in as another user. Try to access the folder 'myteam' using the `cd` command. Explain the result.

```bash
sudo su BB
$ cd myteam
# sh: 1: cd: can't cd to myteam
The error message sh: 1: cd: can't cd to myteam indicates that the myteam directory does not exist or the user BB does not have the necessary permissions to access it.
```

###  13: Change the permissions of 'oldpasswd' file to give owner read and write permissions, group write and execute permissions, and execute permission only for others using `chmod` in two different ways.

```bash
chmod u=rw,g=wx,o=x oldpasswd
# Or
chmod 751 oldpasswd
```

###  14: What are the maximum default permissions for a file and a directory when just created?

- File: 666 (rw-rw-rw-)
- Directory: 777 (rwxrwxrwx)

###  15: What are the minimum permissions needed for the following actions:
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

###  16: Create a file with permission 444. Try to edit and remove it. Note the outcomes.

```bash
touch file.txt
chmod 444 file.txt
# Editing: You can't edit the file.
# Removing: You can't remove the file.
```

###  17: What is the difference between the "x" permission for a file and for a directory?

**Solution:**
- For a file, "x" permission allows executing the file as a program.
- For a directory, "x" permission allows accessing (entering) the directory and its contents.

###  18: Using `vi`, write your CV in the file 'mycv'. Include your name, age, school, college, experience, etc. Then perform the following actions without using arrows:
- Show all line numbers
- Search for the word 'age'
- Move to line 5
- Delete the current line and line 5

```bash
vi mycv
:set number
/age
5G
dd5Gdd
```

###  19: List the available shells in your system.
List the environment variables in your current shell.
List all environment variables for the Bash shell.

```bash
cat /etc/shells
printenv
env
```

###  20: What are the commands to list the value of a specific variable?
Display your current shell name.
State the initialization files for `sh`, `ksh`, and `bash`.

```bash
echo $VARIABLE_NAME
echo $SHELL
/etc/profile (sh), /etc/profile, ~/.profile (ksh), /etc/bashrc, ~/.bashrc (bash)
```

###  21: Edit your profile to display the date at login and change your prompt permanently.

```bash
# Edit ~/.bashrc or ~/.bash_profile to include desired changes.
# Example: Add `date` command for date display and customize PS1 for prompt.
```

###  22: Execute the command `echo \`, and explain the purpose of `\`. What is the prompt `>` and how can you change it to `:`?

```bash
echo \
# The `\` is an escape character used to escape special characters.
# The prompt `>` is the secondary prompt (PS2) in Bash, used in multiline commands. Change it with `PS2=':'`.
```
### 23: Create a Bash shell alias named `ls` for the `ls -l` command.

```bash
alias ls='ls -l'
```
