

# **DevOps001 "weekly Assignments" {week-1}**




------------------------

## Create a file, assign permissions (read, write, execute) to different user categories (owner, group, others), and practice changing permissions using chmod.

####  **Create a File**


```bash
touch file1.txt
```

You can check  with:

```bash
ls -l file1.txt
```

####  **Change Permissions Using `chmod`**

#####  **Add Execute Permission to Owner**

```bash
chmod u+x file1.txt
```


---

#####  **Give Read, Write to Group**

```bash
chmod g+rw file1.txt
```

Now group has read & write.

---

#####  **Remove All Permissions for Others**

```bash
chmod o-rwx file1.txt
```




![screenshot](screenshot/WhatsApp%20Image%202025-05-23%20at%2018.16.32_2d203a21.jpg)


------------------------------------------------


-------------------------------------------------

##  Execute basic Linux commands (e.g., ls, cd, mkdir, rm, touch) to manipulate files and directories, with an emphasis on understanding their usage.
####  Create a File

```bash
touch file2.txt
```

####  Create a Directory

```bash
mkdir himansh1
```

####  Change into a Directory

```bash
cd himansh1
```

####  Go Back to Parent Directory

```bash
cd ..
```

####  List Files

```bash
ls          # Basic list
ls -l       # Long format (permissions, owner, etc.)
```

####  Remove File or Directory

```bash
rm file2.txt              # Delete a file
rm -r himansh1            # Delete a directory
```

---------------------------------------------------

![Screenshot](screenshot/WhatsApp%20Image%202025-05-23%20at%2018.16.32_aa3721d4.jpg)

--------------------------------------------------


##  Using the terminal, practice navigating through directories, listing file contents, and moving files to different locations.

####  Create Structure

```bash
mkdir Himansh12
cd Himansh12
touch test.txt hello.txt
mkdir Rehan
```

####  Move and Rename Files

```bash
mv test.txt Rehan/            # Move file to doc
mv oldname.txt newname.txt    # Rename file
```

####  Copy Files and Directories

```bash
cp test.txt newname.txt           # Copy a file
cp -r dir1/ dir2/                 # Copy a directory
```


----------------------------------------------------------

![Screenshot](screenshot/WhatsApp%20Image%202025-05-23%20at%2018.16.33_0e9b941d.jpg)

----------------------------------------------------------

##  Create a new user and group, set their permissions, and explore user management commands like useradd, usermod, and userdel.

####  Create a User

```bash
sudo useradd new1
sudo passwd new1
```

####  Create a Group

```bash
sudo groupadd new
```

####  Add User to Group

```bash
sudo usermod -aG new new1
```

####  View Group Membership

```bash
groups new1
```

####  Delete User and Group

```bash
sudo userdel new1
sudo groupdel new
```

-----------------------------------------------------------------

![Screenshot](screenshot/WhatsApp%20Image%202025-05-23%20at%2018.16.33_d1ab1052.jpg)

-----------------------------------------------------------------

### Useful Commands

| Command       | Description                         |
| ------------- | ----------------------------------- |
| `pwd`         | Print current working directory     |
| `whoami`      | Display current user                |
| `man ls`      | Manual page for command             |
| `history`     | Show command history                |
| `clear`       | Clear terminal screen               |
| `df -h`       | Disk usage in human-readable format |
| `top`         | Show running processes              |
| `cat`         | Print file content                  |
| `nano file`   | Open file in nano editor            |
| `echo "text"` | Print message to terminal           |

---


---
