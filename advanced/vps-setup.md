# VPS Setup Guide

Set up a Virtual Private Server for running standard TPM 24/7.

**Note:** TPM+ users don't need a VPS - it's hosted by Coflnet Discord bot.

## Recommended Providers

**Vultr** (vultr.com) or **Linode** (linode.com) - $5/mo
- Alternatives: DigitalOcean, Hetzner, AWS Lightsail

**Requirements:**
- 1GB RAM (2GB for multiple accounts)
- 1 vCPU
- 25GB storage
- Ubuntu/Debian OS
- **Location: Chicago** (closest to Hypixel)

## Setup Steps

### 1. Create VPS Instance
1. Sign up with provider
2. Create new instance with Ubuntu/Debian
3. Choose $5-6/mo plan
4. Select **Chicago** datacenter
5. Add SSH key (recommended)
6. Create instance

### 2. Connect via SSH
**Linux/macOS:**
```bash
ssh root@your-vps-ip
```

**Windows:** Use Termius app

### 3. Initial Setup
```bash
# Update system
sudo apt update && sudo apt upgrade -y

# Configure firewall
sudo ufw allow OpenSSH
sudo ufw enable
```

### 4. Install Node.js
```bash
curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash -
sudo apt-get install -y nodejs
node --version  # Verify v18+
```

### 5. Install Tools
```bash
sudo apt install tmux git -y
```

### 6. Get TPM
```bash
mkdir -p ~/tpm && cd ~/tpm
# Download TPM files from TPM team
# Via TPM-Loader from Github releases or git clone
```

### 7. Install Dependencies
**Standard installation:**
```bash
npm install .
```

**Using loader:**
```bash
tmux
sudo chmod 777 ./tpm-loader
./tpm-loader
```

### 8. Configure
```bash
nano config.json5
```
See [Config Structure](../configuration/config-structure.md) for details.

### 9. Test Run
```bash
node index.js
```
Should see: Bot → Hypixel → Coflnet → Ready. Press Ctrl+C to stop.

## Running 24/7

### Tmux (Recommended)
```bash
# Start
tmux
cd ~/tpm && node index.js
# Detach: Ctrl+B, then D

# Reattach
tmux a

# Kill session
tmux kill-session -t 0
```

### PM2 (Alternative)
```bash
npm install -g pm2
pm2 start index.js --name tpm
pm2 logs tpm
pm2 restart tpm
```

## Monitoring & Maintenance

**Check resources:**
```bash
free -h    # Memory
df -h      # Disk
top        # CPU
```

**Update system:**
```bash
sudo apt update && sudo apt upgrade -y
cd ~/tpm && npm install .
```

**Restart bot:**
```bash
# Tmux: kill session then restart
# PM2: pm2 restart tpm
```

## Multiple Accounts

**Requirements:**
- 1 account: 1GB RAM
- 2-3 accounts: 2GB RAM
- 4+ accounts: 4GB RAM or multiple VPS

**Config:**
```javascript
igns: ["Account1", "Account2", "Account3"]
```

## Security

1. Use SSH keys
2. Keep system updated
3. Enable UFW firewall
4. Backup config.json5 regularly:
```bash
cp ~/tpm/config.json5 ~/backups/config-$(date +%Y%m%d).json5
```

## Troubleshooting

**Bot won't start:** Check Node.js version (`node --version`) and config.json5 syntax

**Disconnects:** Check `ping mc.hypixel.net` and `free -h` (may need RAM upgrade)

**Can't connect:** Verify IP, check VPS running in dashboard, ensure port 22 open

See [Common Issues](../troubleshooting/common-issues.md) for more help.

---

**Next:** [Config Structure](../configuration/config-structure.md) | [Loading Configs](../guides/loading-configs.md) | [Auto-Rotation](auto-rotation.md)
