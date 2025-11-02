BANDIT LEVEL [LEVEL 0]

The goal of this level is for you to log into the game using SSH. The host to which you need to connect is bandit.labs.overthewire.org, on port 2220. The username is bandit0 and the password is bandit0.

COMMANDS USED:
ssh -->secure shell
ssh -p --> specify the port
ls-->list the files 
cat-->open the file


Steps I followed:

1. Connected to the server via SSH using the provided username and host:
   ssh bandit0@bandit.labs.overthewire.org -p 2220

2. Listed files in the home directory to see what was present:
   ls
   → Found a file named: readme

3. Opened the readme file to view its contents:
   cat readme

4. Retrieved the password from the file:
   ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If

What I learned:
- How to connect to a remote host using ssh.
- How to list files with ls.
- How to view file contents with cat.

BANDIT LEVEL [LEVEL 1]

# Bandit — Level 1 (Log)

Steps I followed:
1. Logged in using the password from Level 0:

   ssh bandit1@bandit.labs.overthewire.org -p 2220

2. Listed files in the directory:
   ls
   → Found a file named: -

3. Tried to open it with cat - but it didn’t work because "-" is treated as standard input.

4. Correct command used:
   cat ./-
   (Adding ./ tells the shell that "-" is a filename, not an option)

5. Retrieved the password for the next level:
   263JGJPfgU6LtdEvgfWU1XP5yac29mFx

What I learned:
- Files with names like "-" can confuse commands because they’re treated as options.
- To access such files, prefix them with "./" (example: cat ./-)
- Practiced using SSH, ls, and cat again.

BANDIT LEVEL [LEVEL 2]

# Bandit — Level 2 (Log)

Steps I followed:
1. Logged in using the password from Level 1:
   ssh bandit2@bandit.labs.overthewire.org -p 2220

2. Listed files in the directory:
   ls
   → Found a file named: spaces in this filename

3. Tried to open it directly but got an error because of spaces in the filename.

4. Correct command used:
   cat "spaces in this filename"
   or
   cat spaces\ in\ this\ filename

5. Retrieved the password for the next level:
   MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx

What I learned:
- When a filename contains spaces, use quotes (" ") or escape spaces with backslashes (\\).
- Practiced handling special filenames in Linux.

BANDIT LEVEL [LEVEL 3]

# Bandit — Level 3 (Log)

Steps I followed:

1. Logged in using the password from Level 2:
   ssh bandit3@bandit.labs.overthewire.org -p 2220

2. Listed files in the home directory:
   ls
   → Found a directory named: inhere

3. Changed into that directory:
   cd inhere

4. Listed files normally, but nothing appeared.
   Then used:
   ls -a
   → Found a hidden file named: ...Hiding-From-You

5. Displayed the contents of the hidden file:
   cat ...Hiding-From-You

6. Retrieved the password for the next level:
   2EW7BBsr6aMMoJ2HjW067dm8EgX26xNe

What I learned:
- Hidden files in Linux start with a dot (.)
- `ls -a` shows hidden files that are not visible by default.
- Some hidden files can have names starting with multiple dots (like `...Hiding-From-You`).
- Continued practicing navigation (`cd`) and reading files (`cat`).


BANDIT LEVEL [LEVEL 4]

# Bandit — Level 4 (Log)

Steps I followed:

1. Logged in using the password from Level 3:
   ssh bandit4@bandit.labs.overthewire.org -p 2220

2. Listed files in the directory:
   ls
   → Found a directory named: inhere

3. Changed into that directory:
   cd inhere

4. Listed all files:
   ls -a
   → Found multiple files with strange names like -file00, -file01, etc.

5. Tried opening some of them using cat, but most contained unreadable data.

6. To find the one with human-readable text, used:
   file ./*
   → This command showed which file contained ASCII text.

7. Found the correct file (for example, -file07).

8. Displayed its contents:
   cat ./-file07

9. Retrieved the password for the next level:
   4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw

What I learned:
- How to use the `file` command to identify file types.
- How to handle filenames that start with a dash by using `./` before them.
- Continued improving file navigation and content inspection in Linux.

BANDIT LEVEL [LEVEL 5]

BANDIT LEVEL [LEVEL 5]

# Bandit — Level 5 (Log)

Steps I followed:

1. Logged in using the password from Level 4:

   ssh bandit5@bandit.labs.overthewire.org -p 2220

2. Listed files in my home directory:
   ls -la
   → Found a directory named: inhere

3. Changed into that directory:
   cd inhere

4. Listed contents:
   ls -la
   → Found several directories (maybehere00, maybehere01, ...)

5. Searched for the file with exact byte-size requirement:
   find . -type f -size 1033c 2>/dev/null
   → Returned: ./maybehere07/.file2

6. Verified the file is human-readable:
   file ./maybehere07/.file2
   → Output: ASCII text

7. Displayed the file content to get the password:
   cat ./maybehere07/.file2

What I learned:
- `find . -type f -size 1033c` finds files exactly 1033 bytes long.
- `file` confirms human-readable files.
- `ls -l` verifies permissions and exact size.

Next step:
- Use the password found to login:
  ssh bandit6@bandit.labs.overthewire.org -p 2220


BANDIT LEVEL [LEVEL 6]

# Bandit — Level 6 (Log)

Steps I followed:

1. Logged in using the password from Level 5:

   ssh bandit6@bandit.labs.overthewire.org -p 2220
   
2. Searched the whole filesystem for the file meeting criteria:
   find / -type f -user bandit7 -group bandit6 -size 33c 2>/dev/null
   → Returned a path (example): /var/lib/whatever/somefile

3. Verified file ownership, group, and size:
   ls -l /path/to/somefile
   → Example: -rw-r--r-- 1 bandit7 bandit6 33 Nov  1 12:34 /path/to/somefile

4. Displayed the file content to get the password:
   cat /path/to/somefile
   → (This printed the 33-byte password for level 7 — pasted privately)

What I learned:
- `find / -type f -user bandit7 -group bandit6 -size 33c` finds files owned by bandit7:bandit6 of exact 33 bytes.
Next step:
- Use the password found to login:
  ssh bandit7@bandit.labs.overthewire.org -p 2220

BANDIT LEVEL [LEVEL 7]

# Bandit — Level 7 (Log)

Steps I followed:

1. Logged in using the password from Level 6:
   ssh bandit7@bandit.labs.overthewire.org -p 2220
   # enter the password obtained from Level 6

2. Listed files in my home directory:
   ls -la
   → Found file: data.txt

3. Searched inside the file for the keyword "millionth":
   grep millionth data.txt
   → Returned: millionth <PASSWORD>

What I learned:
- `grep pattern filename` finds the pattern in the file quickly.
- The password is located next to the word "millionth" in data.txt.

Next step:
- Use the password found to login:
  ssh bandit8@bandit.labs.overthewire.org -p 2220

BANDIT LEVEL [LEVEL 8]

# Bandit — Level 8 (Log)

Steps I followed:

1. Logged in using the password from Level 7:
   ssh bandit8@bandit.labs.overthewire.org -p 2220
   # enter the password obtained from Level 7

2. Listed files in my home directory:
   ls -la
   → Found file: data.txt

3. Searched for the line that appears only once in the file:
   sort data.txt | uniq -u
   → This printed the unique line (the password)

What I learned:
- `sort data.txt | uniq -u` finds lines that appear exactly once.

Next step:
- Use the password found to login:
  ssh bandit9@bandit.labs.overthewire.org -p 2220


BANDIT LEVEL [LEVEL 9]

# Bandit — Level 9 (Log)

Steps I followed:

1. Logged in using the password from Level 8:

   ssh bandit9@bandit.labs.overthewire.org -p 2220

2. Listed files in my home directory:
   ls -la
   → Found file: data.txt

3. Extracted human-readable strings from the binary file:
   strings data.txt

4. Filtered for the line preceded by '=' characters:
   strings data.txt | grep '='
   → This showed lines containing '='; the password is the readable string following the '=' signs

What I learned:
- `file` identifies that data.txt is not plain text.
- `strings` extracts readable text from binary files.
- `grep '='` helps find the password line which is preceded by '='.

Next step:
- Use the password found to login:
  ssh bandit10@bandit.labs.overthewire.org -p 2220
















