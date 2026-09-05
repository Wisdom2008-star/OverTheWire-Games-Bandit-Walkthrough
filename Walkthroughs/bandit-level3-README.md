# Bandit Level 3 — Walkthrough

## Goal
Find a hidden file inside the `inhere` directory.

## Steps

**1. Connect**
```
ssh bandit3@bandit.labs.overthewire.org -p 2220
```

**2. Move into the directory**
```
cd inhere
```

**3. List files, including hidden ones**
```
ls -la
```
A plain `ls` won't show anything — files starting with a dot (`.`) are hidden by default. The `-a` flag reveals them. You'll see a file called `...Hiding-From-You`.

**4. Read it**
```
cat "...Hiding-From-You"
```
Quotes aren't strictly required here since there are no spaces, but they don't hurt.

**5. Copy the password, then exit**
```
exit
```

**6. Log into Level 4**
```
ssh bandit4@bandit.labs.overthewire.org -p 2220
```

## Takeaway
Anything starting with a dot is hidden from a normal `ls` — always add `-a` when you're hunting for a file and can't find it.
