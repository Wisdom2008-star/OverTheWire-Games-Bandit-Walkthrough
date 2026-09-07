# Bandit Level 9 — Walkthrough

## Goal
Find the password in `data.txt` — it's mixed in with binary data, sitting next to a run of `=` characters.

## Steps

**1. Connect**
```
ssh bandit9@bandit.labs.overthewire.org -p 2220
```
<img src="https://github.com/Wisdom2008-star/OverTheWire-Games-Bandit-Walkthrough/blob/main/Images/Level%209.png">

**2. Check the file**
```
ls
file data.txt
```
`file` tells you this is "data," not plain text — that's why opening it with `cat` would just show garbled junk.

**3. Pull out readable text and filter for "="**
```
strings data.txt | grep "="
```
- `strings` — pulls out only the readable characters, skipping the binary noise
- `grep "="` — narrows it down to lines with `=` in them

**Note:** you'll usually get a few results, not just one. Look through them for the one that actually looks like a password sitting next to the `=` signs.

**4. Copy the password, then exit**
```
exit
```
<img src="https://github.com/Wisdom2008-star/OverTheWire-Games-Bandit-Walkthrough/blob/main/Images/level%209%20(2).png">

**5. Log into Level 10**
```
ssh bandit10@bandit.labs.overthewire.org -p 2220
```

## Takeaway
`strings` + `grep` is the combo for finding readable text buried in a binary file.
