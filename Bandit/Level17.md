# OverTheWire Bandit - Level 16 → Level 17 Write-up

## Required Commands and Tools
Commands for quick reference:

| Command | Description | Useful Flags |
|-|-|-|
| `nmap` | port scanner | -sV, -T4, -p, -v, -quiet |

## Helpful Reading Material
- [Port scanner on Wikipedia](https://en.wikipedia.org/wiki/Port_scanner)

## Solution

### Steps: 
Scan for open ports in range 31000 to 32000 on `localhost` for a ssh service ,make a connection to `localhost` the port you found using `SSL/TLS` encryption, submit the current level password, Copy the `RSA PRIVATE KEY` to a file, change file mode bits using `chmod`, Use the key to SSH into the next level, get the password

### Commands:

**1- Step one**

Do a version scan on localhost from port 31000 to 32000
```bash
nmap -v -T4 -sV localhost -p 31000-32000
```

**2- Step two**

Connect to localhost on the port you found (the `SERVICE` that you should look for is `ssl/unknown`) using `s_client`
```bash
openssl s_client -quiet -connect localhost:3XXXX
```

**3- Step three**

put the current level password and press Enter

**you get a privet key foe next level (Not exactly a password)**

Back to [Bandit](../README.md) | [OverTheWire-WarGames](../../README.md)

**4- Step four**

copy the content of `sshkey.private` and paste it into a temporary file on your computer.

```bash
touch bandit-level17-private.key
nano bandit-level17-private.key
```

**5- Step five**

change the file mode bits to 600 (ssh won't accept any private key that has more open access that)
```bash
chmod 600 bandit-level17-private.key
```
**6- Step six**

make connection via `ssh` and you're authorizing with `RSA PRIVATE KEY` instead of password
```bash
ssh -i bandit-level17-private.key bandit17@bandit.labs.overthewire.org -p 2220
```

**7- Step seven**

The password is here!
```bash
cat /etc/bandit_pass/bandit17
```

Back to [Bandit](../README.md) | [OverTheWire-WarGames](../../README.md)