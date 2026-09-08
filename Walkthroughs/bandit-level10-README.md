# Bandit Level 10 — Walkthrough

## Goal
The password in `data.txt` is encoded in base64. Decode it.

## Steps

**1. Connect**
```
ssh bandit10@bandit.labs.overthewire.org -p 2220
```
<img src="https://github.com/Wisdom2008-star/OverTheWire-Games-Bandit-Walkthrough/blob/main/Images/level%2010.png">

**2. Check the file**
```
ls -la
cat data.txt
```
You'll see a jumble of letters, numbers, and `=` padding at the end — a classic sign of base64 encoding.

**3. Decode it**
```
base64 -d data.txt
```
- `base64` — the tool that handles base64 encoding/decoding
- `-d` — tells it to decode rather than encode

This prints the decoded password straight to your terminal — it may come out as a full sentence like "The password is [password]" rather than just the raw string on its own, so read the line carefully to pick out the actual password.

**4. Copy the password, then exit**
```
exit
```
<img src="https://github.com/Wisdom2008-star/OverTheWire-Games-Bandit-Walkthrough/blob/main/Images/level%2010%20(2).png">

**5. Log into Level 11**
```
ssh bandit11@bandit.labs.overthewire.org -p 2220
```

## Takeaway
Base64 text has a recognizable look — mixed-case letters and numbers, often ending in one or two `=` signs. `base64 -d` reverses it instantly.
