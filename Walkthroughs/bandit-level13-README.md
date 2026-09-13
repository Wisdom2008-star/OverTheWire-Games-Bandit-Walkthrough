# Bandit Level 13 — Walkthrough

## Goal
Use a private SSH key to log in as `bandit14` — no password needed.

## Steps

**1. Connect**
```
ssh bandit13@bandit.labs.overthewire.org -p 2220
```
<img src="https://github.com/Wisdom2008-star/OverTheWire-Games-Bandit-Walkthrough/blob/main/Images/Level%2013.png">

**2. List files — there's a private key**
```
ls -la
```
Shows `sshkey.private`. You can also `cat HINT` if present — it warns that logging into another level via `localhost` is now blocked on this server, and then exit.

<img src="https://github.com/Wisdom2008-star/OverTheWire-Games-Bandit-Walkthrough/blob/main/Images/Level%2013%20(2).png">

**3. Don't try `ssh -i sshkey.private bandit14@localhost` from inside bandit13**
This used to work but now gets rejected with "Connecting from/to localhost is blocked." Instead, the key needs to be used from your own machine, connecting to bandit14 directly.

**4. On your own machine (not the bandit13 session), copy the key down**
```
scp -P 2220 bandit13@bandit.labs.overthewire.org:/home/bandit13/sshkey.private ./bandit14key
```
Enter bandit13's password when prompted.
<img src="https://github.com/Wisdom2008-star/OverTheWire-Games-Bandit-Walkthrough/blob/main/Images/Level%2013%20(5).png">

**5. Fix the key's permissions**
SSH keys need to be locked down so only you can read them. On Windows PowerShell:
```
icacls bandit14key /inheritance:r
icacls bandit14key /grant:r "$($env:USERNAME):(R)"
```
<img src="https://github.com/Wisdom2008-star/OverTheWire-Games-Bandit-Walkthrough/blob/main/Images/Level%2013%20(6).png">

On Linux/macOS, the equivalent is `chmod 600 bandit14key`.

**6. Log in as bandit14 using the key**
```
ssh -i bandit14key -p 2220 bandit14@bandit.labs.overthewire.org
```
No password needed — this should drop you straight into the bandit14 prompt.
<img src="https://github.com/Wisdom2008-star/OverTheWire-Games-Bandit-Walkthrough/blob/main/Images/Level%2013%20(4).png">

**7. Read the password**
```
cat /etc/bandit_pass/bandit14
```
<img src="https://github.com/Wisdom2008-star/OverTheWire-Games-Bandit-Walkthrough/blob/main/Images/Level%2013%20(7).png">

**8. Exit**
```
exit
```
<img src="https://github.com/Wisdom2008-star/OverTheWire-Games-Bandit-Walkthrough/blob/main/Images/Level%2013%20(8).png">

## Takeaway
The old approach — using the key straight from inside bandit13 to jump into bandit14 via `localhost` — no longer works on this server. Download the key to your own machine first, then connect to bandit14 directly from there.
