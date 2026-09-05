# Bandit Level 1 — Walkthrough

## Goal
Find the password stored in a file called `-`.

## Steps

**1. Connect**
```
ssh bandit1@bandit.labs.overthewire.org -p 2220
```

**2. List files**
```
ls -la
```
You'll see a file literally named `-`.

**3. Try to read it normally (it won't work)**
```
cat -
```
The shell reads `-` as a flag, not a filename, so it just hangs.

**4. Read it the right way**
```
cat ./-
```
or
```
cat < -
```
Both tell the shell "this is a file, not an option."

**5. Copy the password, then exit**
```
exit
```

**6. Log into Level 2**
```
ssh bandit2@bandit.labs.overthewire.org -p 2220
```

## Takeaway
Filenames that look like flags need `./` or `<` in front of them so the shell doesn't misread them.

<img src="https://github.com/Wisdom2008-star/OverTheWire-Games-Bandit-Walkthrough/blob/1dedb95d0b9bed165c37bce1ae6c89a521eeda1b/Images/Level%201.png">
<img src="https://github.com/Wisdom2008-star/OverTheWire-Games-Bandit-Walkthrough/blob/91ccf055c2b4e0210b2cd54acc52bcb24f12a624/Images/level%201%20(2).png">
