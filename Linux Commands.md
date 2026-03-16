# Linux Basic Commands — Teaching Notes

## 1. Introduction

Linux provides a powerful **Command Line Interface (CLI)** that allows users to interact with the operating system efficiently. These commands help in managing files, directories, processes, users, and system operations.

---

# 1. Navigation Commands

## `pwd` — Print Working Directory

Displays the current directory path.

```bash
pwd
```

Example Output:

```
/home/vishnu/Documents
```

---

## `cd` — Change Directory

Used to move between directories.

```bash
cd /home/vishnu
cd ..
cd ~
```

Explanation:

|Command|Meaning|
|---|---|
|`cd directory`|Move to directory|
|`cd ..`|Move one level up|
|`cd ~`|Go to home directory|

---

## `ls` — List Directory Contents

Displays files and directories.

```bash
ls
ls -l
ls -a
ls -lh
```

Options:

|Option|Description|
|---|---|
|`-l`|Long format listing|
|`-a`|Show hidden files|
|`-lh`|Human readable file sizes|

---

# 2. File Management Commands

## `touch`

Creates an empty file.

```bash
touch file.txt
```

Multiple files:

```bash
touch file1 file2 file3
```

---

## `cp` — Copy Files

```bash
cp file1 file2
cp file.txt /home/vishnu/
cp -r dir1 dir2
```

Options:

|Option|Meaning|
|---|---|
|`-r`|Copy directories recursively|

---

## `mv` — Move or Rename Files

```bash
mv file1 file2
mv file.txt /home/vishnu/
```

Example:

```
mv oldname.txt newname.txt
```

---

## `rm` — Remove Files

```bash
rm file.txt
rm -r directory
rm -rf directory
```

Options:

|Option|Description|
|---|---|
|`-r`|Remove directories|
|`-f`|Force deletion|

⚠ Warning: `rm -rf` permanently deletes files.

---

# 3. Directory Management

## `mkdir` — Create Directory

```bash
mkdir test
mkdir -p dir1/dir2/dir3
```

`-p` creates parent directories automatically.

---

## `rmdir` — Remove Empty Directory

```bash
rmdir test
```

Works only if directory is empty.

---

# 4. File Viewing Commands

## `cat`

Displays file contents.

```bash
cat file.txt
```

Combine files:

```bash
cat file1 file2
```

---

## `head`

Displays first lines of a file.

```bash
head file.txt
head -n 20 file.txt
```

Default: first **10 lines**

---

## `tail`

Displays last lines of a file.

```bash
tail file.txt
tail -f logfile.txt
```

`-f` monitors file in real-time.

---

# 5. Searching Commands

## `grep`

Searches text patterns in files.

```bash
grep "error" file.txt
grep -i "hello" file.txt
grep -r "main" .
```

Options:

|Option|Meaning|
|---|---|
|`-i`|Case insensitive|
|`-r`|Recursive search|

---

## `find`

Search for files in directory hierarchy.

```bash
find . -name file.txt
find /home -type f
find . -size +10M
```

Examples:

```
find . -name "*.txt"
```

---

## `locate`

Fast file searching using database.

```bash
locate file.txt
```

Update database:

```bash
sudo updatedb
```

---

# 6. Sorting and Comparison

## `sort`

Sort lines in files.

```bash
sort file.txt
sort -r file.txt
sort -n numbers.txt
```

Options:

|Option|Meaning|
|---|---|
|`-r`|Reverse order|
|`-n`|Numeric sorting|

---

## `diff`

Compares two files.

```bash
diff file1 file2
```

Shows differences between files.

---

# 7. File Information

## `file`

Displays file type.

```bash
file test.txt
```

Example output:

```
test.txt: ASCII text
```

---

# 8. Linking Files

## Hard Link

```bash
ln file1 link1
```

Characteristics:

- Same inode
    
- Cannot cross file systems
    

---

## Symbolic Link (Soft Link)

```bash
ln -s file1 link1
```

Characteristics:

- Shortcut to file
    
- Can link across filesystems
    

---

# 9. Compression Commands

## `gzip`

Compress file.

```bash
gzip file.txt
```

Result:

```
file.txt.gz
```

---

## `gunzip`

Decompress file.

```bash
gunzip file.txt.gz
```

---

## `zip`

Create compressed archive.

```bash
zip archive.zip file1 file2
```

---

## `unzip`

Extract zip file.

```bash
unzip archive.zip
```

---

# 10. Tar Command

Used for archiving files.

Create archive:

```bash
tar -cvf archive.tar files/
```

Extract archive:

```bash
tar -xvf archive.tar
```

Compressed tar:

```bash
tar -czvf archive.tar.gz files
tar -xzvf archive.tar.gz
```

Options:

|Option|Meaning|
|---|---|
|`-c`|Create archive|
|`-x`|Extract archive|
|`-v`|Verbose|
|`-f`|File name|
|`-z`|Gzip compression|

---

# 11. User Information Commands

## `who`

Shows logged-in users.

```bash
who
```

---

## `whoami`

Displays current username.

```bash
whoami
```

---

# 12. Process Management

## `ps`

Displays running processes.

```bash
ps
ps aux
```

---

## `kill`

Terminates process.

```bash
kill PID
kill -9 PID
```

Example:

```
kill 1234
```

---

# 13. Output Commands

## `echo`

Prints text or variables.

```bash
echo "Hello Linux"
echo $HOME
```

---

# 14. Manual Pages

## `man`

Displays command documentation.

```bash
man ls
man grep
```

Navigation in man page:

|Key|Action|
|---|---|
|`q`|Quit|
|`/`|Search|
|`n`|Next match|

---

# 15. Makefile

A **Makefile** automates compilation tasks.

Example Makefile:

```makefile
all:
	gcc main.c -o program
```

Run:

```bash
make
```

---

# Summary

Linux commands allow users to:

- Navigate directories
    
- Manage files
    
- Search data
    
- Compress archives
    
- Monitor processes
    
- Automate tasks
    

Mastering these commands significantly improves productivity in Linux environments.

---