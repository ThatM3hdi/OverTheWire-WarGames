# OverTheWire Bandit - Level 21 → Level 22 Write-up

## Helpful Reading Material
- `man cron`

## Solution

### Steps: 
Go to `cron.d` directory, read the `cronjob` that is related to your target, find the script that it supposed run, modify the script and run it to find the password path, read the password. (you can always see more than what is necessary!)

### Commands:

**1- Step one**

```bash
cd /etc/cron.d
ls
```

**3- Step three**
```bash
cat cronjob_bandit23
```
find the script that your cronjob supposed to run

**4- Step four**
```bash
cat /usr/bin/cronjob_bandit23.sh
```
read the script, see the template for passwords file, and modify it

**5- Step five**
```bash
echo I am user bandit23 | md5sum | cut -d ' ' -f 1
```
run the modified script to find the password path

**6- Step six**
```bash
cat /tmp/8ca319486bfbbc3663ea0fbe81326349
```

## Funny note
I also somehow found the password of `Bandit24` using `Bandit22`.
try it.

Back to [Bandit](../README.md) | [OverTheWire-WarGames](../../README.md)