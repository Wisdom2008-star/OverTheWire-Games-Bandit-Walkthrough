# Bandit Level 14 — Walkthrough

## Goal
Submit bandit14's own password to a listening port on localhost to get the bandit15 password.

## Steps

**1. Connect**
```
ssh bandit14@bandit.labs.overthewire.org -p 2220
```
Use bandit14's password (from Level 13) to log in.
<img src="https://github.com/Wisdom2008-star/OverTheWire-Games-Bandit-Walkthrough/blob/main/Images/Level%2014.png">

**2. Check for anything unusual**
```
ls -la
```
Nothing extra here — no hint file needed for this level.

**3. Connect to the listening port**
```
nc localhost 30000
```

**4. Submit bandit14's password**
Type (or paste) bandit14's password into the connection and press Enter.

**5. Read the response**
If correct, it replies "Correct!" followed by the bandit15 password.

**6. Exit**
```
exit
```
<img src="https://github.com/Wisdom2008-star/OverTheWire-Games-Bandit-Walkthrough/blob/main/Images/Level%2014%20(2).png">

## Takeaway
This level isn't about finding a file — it's about talking to a service on a port using `nc` (netcat) and sending it the right piece of data.
