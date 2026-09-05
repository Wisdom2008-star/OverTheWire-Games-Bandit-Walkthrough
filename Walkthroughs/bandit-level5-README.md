# Bandit Level 5 — Walkthrough

## Goal
Find one specific file buried inside the `inhere` directory, matching three clues: human-readable, 1033 bytes in size, and not executable.

## Steps

**1. Connect**
```
ssh bandit5@bandit.labs.overthewire.org -p 2220
```

**2. Look at what you're dealing with**
```
cd inhere
ls -la
```
You'll find a maze of subdirectories (`maybehere00`, `maybehere01`, etc.), each with more files inside. Digging through manually would take forever — this is a job for `find`.

**3. Search using all three clues at once**
```
find inhere -type f -size 1033c ! -executable
```
Breaking that down:
- `find inhere` — search starts inside the `inhere` folder, digging through all subfolders
- `-type f` — only match regular files (skip directories)
- `-size 1033c` — match files that are exactly 1033 bytes (`c` = bytes)
- `! -executable` — exclude anything with executable permissions

This should return exactly one file path — that path is your answer, printed by `find` itself. You don't have to guess which `maybehere` folder it's in or open files one by one; because `find inhere` searches recursively (into every subfolder, no matter how deep), it checks all the `maybehereXX` directories for you and only prints the single file that matches all three conditions (right size, right type, not executable). Whatever path shows up on your screen after running the command — that's the file.

**4. Read the file**
```
cat inhere/maybehere07/.file2
```
(path will vary — use whatever `find` handed you)

**5. Copy the password, then exit**
```
exit
```

**6. Log into Level 6**
```
ssh bandit6@bandit.labs.overthewire.org -p 2220
```

## Takeaway
`find` lets you search by size, type, and permissions all at once — much faster than manually digging through nested folders.
