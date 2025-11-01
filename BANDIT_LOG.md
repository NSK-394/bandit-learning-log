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











