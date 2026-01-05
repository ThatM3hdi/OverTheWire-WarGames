# OverTheWire Bandit - Level 13 → Level 14 Write-up

## Required Commands and Tools
Commands for quick reference:

| Command | Description | Useful Flags |
|-|-|-|
| `ssh` | remote login to another server | -i |
| `chmod` | change file mode bits | |
## Helpful Reading Material
- [SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

## Solution

### Steps: 
List files, Copy the `sshkey.private` to a file, change file mode bits using `chmod`, Use the key to SSH into the next level

### Commands:

**1- Step one**

```bash
ls  
cat sshkey.private 
```
**2- Step two**

copy the content of `sshkey.private` and paste it into a temporary file on your computer.

```bash
touch bandit-level14-private.key
nano bandit-level14-private.key
```

**3- Step three**

change the file mode bits to 600 (ssh won't accept any private key that has more open access that)
```bash
chmod 600 bandit-level14-private.key
```
**4- Step four**

make connection via `ssh` and you're authorizing with `private key` instead of password
```bash
ssh -i bandit-level14-private.key bandit14@bandit.labs.overthewire.org -p 2220
```

**5- Step five**

The password is here!
```bash
cat /etc/bandit_pass/bandit14
```

Back to [Bandit](../README.md) | [OverTheWire-WarGames](../../README.md)
