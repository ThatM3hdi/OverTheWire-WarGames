# OverTheWire Bandit - Level 15 → Level 16 Write-up

## Required Commands and Tools
Commands for quick reference:

| Command | Description | Useful Flags |
|-|-|-|
| `openssh` | OpenSSL command line program |  |
| `openssh s_client` | OpenSSL application commands | -connect |


## Helpful Reading Material
- [OpenSSL Cookbook - Testing with OpenSSL](https://www.feistyduck.com/library/openssl-cookbook/online/testing-with-openssl/index.html)
- `man openssl s_client`

## Solution

### Steps: 
Make a connection to `localhost` on port `30001` using `SSL/TLS` encryption, submit the current level password

### Commands:

**1- Step one**

```bash
openssl s_client -connect localhost:30001
```

**2- Step two**

put the current level password and press Enter

Back to [Bandit](../README.md) | [OverTheWire-WarGames](../../README.md)
