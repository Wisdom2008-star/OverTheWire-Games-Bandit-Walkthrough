# Bandit Level 0 — Walkthrough

## Goal
Connect to the server as `bandit0` and find the password for `bandit1`.

## Login Info
- Username: `bandit0`
- Password: `bandit0`
- Host: `bandit.labs.overthewire.org`
- Port: `2220`

## Steps

**1. Connect via SSH**
```
ssh bandit0@bandit.labs.overthewire.org -p 2220
```
Type `yes` if asked about host authenticity. Then enter the password (`bandit0`) — nothing will show as you type, that's normal.

**2. List files**
```
ls -la
```
You'll see a file called `readme`.

**3. Read it**
```
cat readme
```
This prints the password for Level 1. Copy it somewhere safe.

**4. Exit**
```
exit
```

**5. Log into Level 1**
```
ssh bandit1@bandit.labs.overthewire.org -p 2220
```

## Quick Fixes
- Connection issues → make sure you included `-p 2220`
- Password not showing → normal, just type and hit Enter
- Permission denied → check for extra spaces when you copy the password

## Takeaway
The core loop: **connect → explore → find password → move on**. You'll repeat this pattern for the rest of the game.


<img src="https://github.com/Wisdom2008-star/OverTheWire-Games-Bandit-Walkthrough/blob/main/Images/Level%200%20to%201.png">
<img src="https://github.com/Wisdom2008-star/OverTheWire-Games-Bandit-Walkthrough/blob/main/Images/Level%200%20to%201%20(2).png">
