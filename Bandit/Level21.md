# OverTheWire Bandit - Level 20 → Level 21 Write-up

## Required Commands and Tools
Commands for quick reference:

| Command | Description | Useful Flags |
|-|-|-|
| `nc` | arbitrary TCP and UDP connections and listens | -l, -p |

## Helpful Reading Material
- [foreground and background jobs](https://linux1st.com/1035-create-monitor-and-kill-processes.html)

## Solution

### Steps: 
Make a "daemon" (listener) and use it to send password to binary file

### Commands:

```bash
echo "CURRENT-LEVEL-PASSWORD" | nc -l -p 12345&

./suconnect 12345
```

Back to [Bandit](../README.md) | [OverTheWire-WarGames](../../README.md)