# Bandit Level 6 — Walkthrough

## Goal
Find a file somewhere on the entire filesystem that matches three clues: owned by user `bandit7`, owned by group `bandit6`, and 33 bytes in size.

## Steps

**1. Connect**
```
ssh bandit6@bandit.labs.overthewire.org -p 2220
```

**2. Check the home directory first**
```
ls -la
```
It's empty this time — the file we want isn't here. The hint says it could be anywhere on the server, so we need to search the whole filesystem.

**3. Search from the root, using all three clues**
```
find / -user bandit7 -group bandit6 -size 33c 2>/dev/null
```
Breaking that down:
- `find /` — start searching from the very top of the filesystem, covering everything
- `-user bandit7` — only match files owned by the user `bandit7`
- `-group bandit6` — only match files owned by the group `bandit6`
- `-size 33c` — only match files exactly 33 bytes (`c` = bytes)
- `2>/dev/null` — redirects error messages (like "Permission denied," which you'll get a lot of searching from `/`) to nowhere, so your terminal only shows the results that actually matter

**4. Read the matching file**
```
cat /var/lib/dpkg/info/bandit7.password
```
(path will vary — use whatever `find` prints out)

**5. Copy the password, then exit**
```
exit
```

**6. Log into Level 7**
```
ssh bandit7@bandit.labs.overthewire.org -p 2220
```

## Takeaway
Searching the entire filesystem generates a flood of "Permission denied" noise. Piping errors to `/dev/null` with `2>/dev/null` keeps your results clean so the actual match doesn't get buried.
