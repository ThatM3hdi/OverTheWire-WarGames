# OverTheWire Bandit - Level 12 → Level 13 Write-up

## Required Commands and Tools
Commands for quick reference:

| Command | Description | Useful Flags |
|-|-|-|
| `xxd` | make a hex dump or do the reverse | -r |
| `bunzip` | file compressor |  |
| `gunzip` | file compressor |  |
| `tar` | archiving utility | -x, -f |
| `mktemp` | create a temporary file or directory | -d |

## Solution

**Steps:** revert the hexdump, decompress it in deffrend ways

**Commands:**
```bash
ls
file data.txt
```
data.txt is and `ASCII text` file but it's not human readable (in the [level Goal](https://overthewire.org/wargames/bandit/bandit13.html) we can see that its a hexdump)

```bash
mktemp -d
cd TEMPDIRECTORY
cp ~/data.txt .
```
we're making a temporary directory so we can have access to make files and copy `data.txt` in there 

```bash
xxd -r data.txt > data1.txt
```
reverting the hexdump using `xdd -r` and redirecting the result to `data1.txt` so we can have better undrestading of the process

```bash
file data1.txt
cp data1.txt data2.gz
gunzip data2.gz
```
the file type is `gzip` so we copy it and rename it to `data2.gz` and we decompress it usning `gunzip`

```bash
file data2
cp data2 data3.bz
bunzip2 data3.bz
```
the file type is `bzip` so we copy it and rename it to `data3.bz` and we decompress it usning `bunzip2`

```bash
file data3
cp data3 data4.gz
gunzip data4.gz
```
the file type is `gzip` so we copy it and rename it to `data4.gz` and we decompress it usning `gunzip`

```bash
file data4
cp data4 data5.tar
tar -xf data5.tar
```
the file type is `tar archive` so we copy it and rename it to `data5.tar` and we unarchive it usning `tar -xf`

```bash
file data5.bin
cp data5.bin data6.tar
tar -xf data6.tar
```
the file type is `tar archive` so we copy it and rename it to `data6.tar` and we unarchive it usning `tar -xf`

```bash
file data6.bin
cp data6.bin data7.bz
bunzip2 data7.bz
```
the file type is `bzip` so we copy it and rename it to `data7.bz` and we decompress it usning `bunzip2`

```bash
file data7
cp data7 data8.tar
tar -xf data8.tar
```
the file type is `tar archive` so we copy it and rename it to `data8.tar` and we unarchive it usning `tar -xf`

```bash
file data8.bin
cp data8 data9.gz
gunzip data9.gz
```
the file type is `gzip` so we copy it and rename it to `data9.gz` and we decompress it usning `gunzip`

```bash
file data9
cat data9
```
the file type is `ASCII text` so we can read it!


Back to [Bandit](../README.md) | [OverTheWire-WarGames](../../README.md)
