# Mount a Share

```bash
sudo mkdir -p /mnt/n
sudo mount -t drvfs '\\mrbig.nexxar.com\nexxar' /mnt/n
```

Or in **one line:** 

```bash
sudo mkdir -p /mnt/n && sudo mount -t drvfs '\\mrbig.nexxar.com\nexxar' /mnt/n
```

# Show running process

```bash
lsof -i :5173
```

or

```bash
ps aux | grep vite
```