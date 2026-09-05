# Bandit Level 2 — Walkthrough

## Goal
Find the password stored in a file with spaces in its name.

## Steps

**1. Connect**
```
ssh bandit2@bandit.labs.overthewire.org -p 2220
```

**2. List files**
```
ls -la
```
You'll see a file called `spaces in this filename`.

**3. Read it**
```
cat "spaces in this filename"
```
Quoting the name keeps the shell from treating each space as a separator between arguments — without quotes, the shell thinks you're passing `cat` three separate files: `spaces`, `in`, `this`, `filename`, and fails because none of those exist on their own.

**Every way you can type this command:**
- Double quotes:
  ```
  cat "spaces in this filename"
  ```
- Single quotes:
  ```
  cat 'spaces in this filename'
  ```
- Backslash before each space:
  ```
  cat spaces\ in\ this\ filename
  ```
- Wildcard, since there's only one file matching this pattern:
  ```
  cat spaces*filename
  ```
- Tab-completion (safest option) — type `cat sp` then press Tab, and the shell fills in the rest, including the escaped spaces, for you:
  ```
  cat spaces\ in\ this\ filename
  ```
  (this is what tab-completion produces automatically once you hit Tab and Enter)

**Common mistakes that cause errors here:**
- Using single quotes vs double quotes inconsistently — both work fine here, just don't mix an opening `'` with a closing `"`.
- Typing extra or missing spaces inside the quotes — the filename has to match exactly, so `"spaces  in this filename"` (two spaces) won't work.
- Copy-pasting the filename from a source that silently changes regular spaces into different-looking whitespace characters — if quoting still fails, try tab-completion instead of typing/pasting.

**4. Copy the password, then exit**
```
exit
```

**5. Log into Level 3**
```
ssh bandit3@bandit.labs.overthewire.org -p 2220
```

## Takeaway
Wrap filenames with spaces (or special characters) in quotes, or escape each space with `\`, so the shell treats them as one name instead of several. When in doubt, let tab-completion do it for you.
