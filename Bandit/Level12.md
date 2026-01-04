# OverTheWire Bandit - Level 11 → Level 12 Write-up

## Required Commands and Tools
Commands for quick reference:

| Command | Description | Useful Flags |
|-|-|-|
| `base64` | encode/decode data and print to standard output | -d |

## Helpful Reading Material
- [Rot13 on Wikipedia](https://en.wikipedia.org/wiki/ROT13)

## Solution

The transformation can be done using a lookup table.
**Steps:** List files, Decode it, read it.

**Commands:**
```bash
cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
```

Back to [Bandit](../README.md) | [OverTheWire-WarGames](../../README.md)
