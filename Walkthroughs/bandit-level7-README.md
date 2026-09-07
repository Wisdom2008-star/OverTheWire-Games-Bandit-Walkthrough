# Bandit Level 7 — Walkthrough

## Goal
Find the password in `data.txt` — it sits right next to the word "millionth."

## Steps

**1. Connect**
```
ssh bandit7@bandit.labs.overthewire.org -p 2220
```

**2. Check what's in the home directory**
```
ls -la
```
You'll see a file called `data.txt`. Opening it directly with `cat` would dump a huge wall of text, since the password is buried among thousands of lines.

**3. Search for the keyword instead**
```
grep millionth data.txt
```
`grep` scans the file line by line and only prints lines containing the word you searched for — in this case, "millionth." The line it returns will have the word next to the password.

**4. Copy the password, then exit**
```
exit
```

**5. Log into Level 8**
```
ssh bandit8@bandit.labs.overthewire.org -p 2220
```

## Takeaway
When you're hunting for something specific in a huge file, `grep` saves you from scrolling through it manually — search for a known keyword and let it find the line for you.
