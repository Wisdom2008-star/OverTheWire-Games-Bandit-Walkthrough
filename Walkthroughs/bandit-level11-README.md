# Bandit Level 11 — Walkthrough

## Goal
The password in `data.txt` is scrambled using ROT13 (each letter rotated 13 places through the alphabet). Decode it.

## Steps

**1. Connect**
```
ssh bandit11@bandit.labs.overthewire.org -p 2220
```
<img src="https://github.com/Wisdom2008-star/OverTheWire-Games-Bandit-Walkthrough/blob/main/Images/Level%2011.png">

**2. Check the file**
```
ls -la
cat data.txt
```
The text looks like real words but scrambled — a sign it's a simple letter-substitution cipher rather than encoding like base64.

**3. (Optional) Check what `tr` does**
```
man tr
```
This opens the manual for `tr`, which shows it's a tool for translating or deleting characters — it takes a set of characters to replace and a set to replace them with, swapping each one for its matching position in the second set. Useful to run if you want to understand the command before using it. Press `q` to exit the manual page.

**4. Decode it with `tr`**
```
cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
```
- `cat data.txt` — prints the file
- `| tr 'A-Za-z' 'N-ZA-Mn-za-m'` — pipes that output into `tr`, which swaps each letter for the one 13 places ahead (wrapping back to the start when it hits the end). Since ROT13 is symmetric, applying it a second time would decode back to the original — you're using the same shift to undo the cipher.

This may print as a full sentence like "The password is [password]" rather than just the raw string — read the line carefully to pick out the actual password.

**5. Copy the password, then exit**
```
exit
```
<img src="https://github.com/Wisdom2008-star/OverTheWire-Games-Bandit-Walkthrough/blob/main/Images/Level%2011%20(2).png">

**6. Log into Level 12**
```
ssh bandit12@bandit.labs.overthewire.org -p 2220
```

## Takeaway
ROT13 is its own reverse — running the same shift twice gets you back to plain text. `tr` is a quick one-liner for this without needing a dedicated decoder.
