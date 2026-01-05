# OverTheWire Bandit - Level 12 → Level 13 Write-up

## Required Commands and Tools
Commands for quick reference:

| Command | Description | Useful Flags |
|-|-|-|
| `xxd` | make a hex dump or do the reverse | -r |
| `bunzip2` | file compressor |  |
| `gunzip` | file compressor |  |
| `tar` | archiving utility | -x, -f |
| `mktemp` | create a temporary file or directory | -d |

## Solution

### Steps: 
revert the hexdump, decompress it in different ways

### Commands:
**1- Step one**
```bash
ls
file data.txt
```
data.txt is `ASCII text` file but it's not human readable (it said in the [level Goal](https://overthewire.org/wargames/bandit/bandit13.html) that its a hexdump)

**2- Step two**
Make a temporary directory to access to make files && copy `data.txt` in there.
```bash
mktemp -d
cd /tmp/tmp.XXXXXX #Replace with your actual temp directory name
cp ~/data.txt .
```

**3- Step three**
revert the hexdump using `xxd -r` and redirect the result to `data1.txt` for better understanding of the process

```bash
xxd -r data.txt > data1.txt
```

**4- Step four**
repeatedly decompression

```bash
file data1.txt # gzip compressed
cp data1.txt data2.gz
gunzip data2.gz
```

```bash
file data2 # bzip compressed
cp data2 data3.bz
bunzip2 data3.bz
```

```bash
file data3 # gzip compressed 
cp data3 data4.gz
gunzip data4.gz
```

```bash
file data4 # tar archive
cp data4 data5.tar
tar -xf data5.tar
```

```bash 
file data5.bin # tar archive
cp data5.bin data6.tar
tar -xf data6.tar
```

```bash
file data6.bin # bzip compressed
cp data6.bin data7.bz
bunzip2 data7.bz
```

```bash
file data7 # tar archive
cp data7 data8.tar
tar -xf data8.tar
```
 
```bash
file data8.bin # gzip compressed
cp data8 data9.gz
gunzip data9.gz
```

**5- Step five**
The password is here!
```bash
file data9 # ASCII text
cat data9
```

Back to [Bandit](../README.md) | [OverTheWire-WarGames](../../README.md)
