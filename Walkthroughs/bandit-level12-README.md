# Bandit Level 12 — Walkthrough

## Goal
`data.txt` is a hexdump of a file compressed multiple times. Recover the original and read the password.

## Steps

**1. Connect**
```
ssh bandit12@bandit.labs.overthewire.org -p 2220
```

**2. Set up a workspace**
```
mkdir /tmp/work12
cd /tmp/work12
cp ~/data.txt .
```

**3. Reverse the hexdump into binary**
```
xxd -r data.txt > data.out
```

**4. Find out what kind of file you now have**
```
file data.out
```
It will report a compression type such as gzip, bzip2, or a tar archive.

**5. Decompress it, one layer at a time**

If `file` says gzip, rename it and unzip:
```
mv data.out data.gz
gunzip data.gz
```

If `file` says bzip2, rename it and unzip:
```
mv data data.bz2
bunzip2 data.bz2
```

If `file` says it's a tar archive, rename it and extract it:
```
mv data data.tar
tar -xf data.tar
```
After extracting a tar archive, run `ls` — it drops out a new file rather than replacing the old one, so check the folder to see what appeared.

**6. Repeat step 4 and 5**
After each decompression, run `file` again on whatever file you're left with, then follow whichever instruction above matches. Keep going — checking type, renaming, decompressing — until `file` reports something like "ASCII text." That means you've reached the bottom and there's nothing left to unwrap.

**7. Read the final file**
```
cat <final_filename>
```
This may print as "The password is [password]" rather than just the raw string.

**8. Exit**
```
exit
```

## Takeaway
It's the same three moves on repeat: check the type, rename to match, decompress. The number of layers and the order they come in can differ each time you attempt this level, so let `file` tell you what to do next rather than expecting a fixed pattern.
