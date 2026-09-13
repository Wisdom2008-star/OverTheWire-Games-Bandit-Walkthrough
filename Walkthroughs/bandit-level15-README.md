# Bandit Level 15 — Walkthrough

## Goal
Submit bandit15's own password to an SSL-encrypted port on localhost to get the bandit16 password.

## Steps

**1. Connect**
```
ssh bandit15@bandit.labs.overthewire.org -p 2220
```
Use bandit15's password (from Level 14) to log in.

**2. Check for anything unusual**
```
ls -la
```
You may see a leftover `.bandit14.password` file — that's just a copy of the password you already have, not part of this level.

**3. Connect to the port using SSL**
Plain `nc` won't work here since the port expects an encrypted connection:
```
openssl s_client -connect localhost:30001
```

**4. Submit bandit15's password**
Once connected, type (or paste) bandit15's password and press Enter.

**5. Read the response**
If correct, it replies "Correct!" followed by the bandit16 password.

**6. Exit**
```
exit
```

## Takeaway
Same idea as Level 14 — send a password to a port — but this port requires SSL/TLS, so `openssl s_client` stands in for `nc`.
