# Bandit Level 8 — Walkthrough

## Goal
Find the one line in `data.txt` that appears only once — every other line is repeated.

## Steps

**1. Connect**
```
ssh bandit8@bandit.labs.overthewire.org -p 2220
```

**2. Check the file**
```
ls -la
```
You'll see `data.txt`, a large file full of repeated lines with one unique line hidden among them.

**3. Sort, then filter for uniques**
```
sort data.txt | uniq -u
```
- `sort data.txt` — arranges all lines alphabetically. This matters because `uniq` only catches duplicates that are next to each other, so sorting groups matching lines together first.
- `| uniq -u` — the pipe (`|`) feeds the sorted output into `uniq`, and `-u` tells it to print only lines that have no duplicates at all.

**4. Copy the password, then exit**
```
exit
```

**5. Log into Level 9**
```
ssh bandit9@bandit.labs.overthewire.org -p 2220
```

## Takeaway
`uniq` only detects duplicates sitting next to each other — always `sort` first, then pipe into `uniq -u` to isolate the one-off line.
