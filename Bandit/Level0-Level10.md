# OverTheWire Bandit - Levels 0 to 10 Write-up

## Introduction
This write-up summarizes solutions for Bandit levels 0-10 from OverTheWire. These beginner levels teach basic Linux commands and file handling. Solutions are spoiler-free (no passwords).

**Note:** Connect via `ssh banditX@bandit.labs.overthewire.org -p 2220` (X = level).

## Required Commands and Tools
Commands for quick reference:

| Command | Description | Useful Flags |
|-|-|-|
| `ssh` | remote login to another server | -p |
| `ls` | list files | -l, -t, -r, -h, -a |
| `cd` | change directories ||
| `cat` | print file ||
| `grep` | sreach for match patterns ||
| `find` | search files | -user, -group, -size |
| `sort` | sort lines | -g |
| `uniq` | unique lines | -c |
| `strings` | extract strings ||

## Helpful Reading Material
- [Usage of dash (-) in place of a filename](https://www.google.com/search?client=firefox-b-lm&channel=entpr&q=Usage+of+dash+%28-%29+in+place+of+a+filename)
- [Escape characters in filename](https://www.google.com/search?client=firefox-b-lm&channel=entpr&q=Escape+characters+in+filename)
- [Use streams, pipes, and redirects](https://linux1st.com/1034-use-streams-pipes-and-redirects.html)

## Solutions

### Level 0 → 1
**Steps:** List files, read it.
**Commands:**
```bash
ls
cat readme
```

### Level 1 → 2
**Steps:** List, read the file with path.
**Commands:**
```bash
ls
cat ./-
```

### Level 2 → 3
**Steps:** List, quote/escape name.
**Commands:**
```bash
ls
cat "spaces in this filename"
```

### Level 3 → 4
**Steps:** Go to directory, list all, read.
**Commands:**
```bash
cd inhere
ls -a
cat .hidden
```

### Level 4 → 5
**Steps:** Go to directory, extract strings.
**Commands:**
```bash
cd inhere
strings -file*
```

### Level 5 → 6
**Steps:** Find by size.
**Commands:**
```bash
cd inhere
find . -size 1033c
```

### Level 6 → 7
**Steps:** search /, redirect errors.
**Commands:**
```bash
find / -user bandit7 -group bandit6 -size 33c 2>/dev/null
```

### Level 7 → 8
**Steps:** Search pattern.
**Commands:**
```bash
grep millionth data.txt
```

### Level 8 → 9
**Steps:** Sort, count, sort by count.
**Commands:**
```bash
sort data.txt | uniq -c | sort -g
```

### Level 9 → 10
**Steps:** read, filter.
**Commands:**
```bash
strings data.txt | grep ===
```

Back to [Bandit](../README.md) | [OverTheWire-WarGames](../../README.md)
