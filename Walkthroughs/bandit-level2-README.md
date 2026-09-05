# Bandit Level 2 — Walkthrough

## A note on PowerShell
You're launching SSH from PowerShell, but once connected you're inside a Linux shell on the remote server — that's where every command below actually runs. So no translation needed; these are the exact commands to type, whether you started from PowerShell, macOS Terminal, or anything else.

## Goal
Find the password stored in a file with spaces in its name.

## Steps

**1. Connect**
```
ssh bandit2@bandit.labs.overthewire.org -p 2220
```
<img src="https://github.com/Wisdom2008-star/OverTheWire-Games-Bandit-Walkthrough/blob/0f8274756bab890ad0a7921d5659c010aefe3db1/Images/Level%202.png">

**2. List files**
```
ls
```
This file doesn't start with a dot, so you don't need `-la` to see it. You'll see a file called `--spaces in this filename--`. Note the double dashes on **both ends**, not just spaces in the middle — that leading `--` matters and is the actual source of most people's trouble on this level.

**3. Read it**
```
cat -- "--spaces in this filename--"
```
Two things are happening here:
- The `--` right after `cat` tells the command "stop treating anything after this as a flag — everything from here is a filename." Without it, `cat` sees the leading `--` on the filename and tries to interpret it as options, the same trap as Level 1.
- The quotes around the name handle the spaces, so the shell treats it as one filename instead of several separate arguments.

**Other ways to type this command:**
- Single quotes instead of double:
  ```
  cat -- '--spaces in this filename--'
  ```
- Backslash before each space (and each dash doesn't need escaping, but the leading `--` still needs the `--` separator before it):
  ```
  cat -- --spaces\ in\ this\ filename--
  ```
- Tab-completion (safest option) — type `cat -- --sp` then press Tab, and the shell fills in the rest for you:
  ```
  cat -- --spaces\ in\ this\ filename--
  ```

**Common mistakes that cause errors here:**
- Forgetting the `--` before the filename — `cat "--spaces in this filename--"` alone will fail or throw an "invalid option" error, because `cat` still sees the leading dashes as flags even inside quotes.
- Mixing quote types — don't open with `'` and close with `"`.
- Typing extra or missing spaces inside the quotes — the filename has to match exactly.
- Copy-pasting from a source that silently swaps regular spaces for different whitespace characters — if quoting still fails, use tab-completion instead.

**4. Copy the password, then exit**
```
exit
```
<img src="https://github.com/Wisdom2008-star/OverTheWire-Games-Bandit-Walkthrough/blob/5ffc2be198a95f8ad61a5ee046a25bc99773fd7f/Images/level%202%20(2).png">

**5. Log into Level 3**
```
ssh bandit3@bandit.labs.overthewire.org -p 2220
```

## Takeaway
Two separate problems, one filename: dashes at the start get read as command flags (fix with `--`), and spaces in the middle get read as separators between arguments (fix with quotes or backslashes). This file has both, which is exactly why it trips people up.
