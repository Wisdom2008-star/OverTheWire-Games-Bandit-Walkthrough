# Bandit Level 4 — Walkthrough

## Goal
Find the one human-readable file among several in the `inhere` directory.

## Steps

**1. Connect**
```
ssh bandit4@bandit.labs.overthewire.org -p 2220
```

**2. Move into the directory and list files**
```
cd inhere
ls -la
```
You'll see a bunch of files named like `-file00`, `-file01`, `-file02`, etc. Opening each one blind with `cat` would take forever, and some may contain junk/binary data.

**3. Check file types instead of guessing**
```
file ./-file*
```
The `./` in front stops the shell from reading `-file*` as a command flag (same issue as Level 1). The `file` command inspects each one and tells you what type of content it holds — most will say "data," but one will say "ASCII text."

**4. Read the ASCII one**
```
cat ./-file07
```
(swap in whichever number `file` flagged as ASCII text for you — it varies between resets)

**5. Copy the password, then exit**
```
exit
```

**6. Log into Level 5**
```
ssh bandit5@bandit.labs.overthewire.org -p 2220
```

## Takeaway
When you're sorting through a pile of unfamiliar files, use `file` to check what's actually inside before wasting time opening each one.
