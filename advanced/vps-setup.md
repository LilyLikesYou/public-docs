# VPS Setup

Set up a Virtual Private Server for running TPM 24/7.

**Note:** TPM+ users don't need VPS - it's hosted by Coflnet.

## Providers

**Vultr** or **Linode** - $5/mo
- Alternatives: DigitalOcean, Hetzner, AWS Lightsail

**Requirements:**
- 1GB RAM (2GB for multiple accounts)
- 1 vCPU
- 25GB storage
- Ubuntu/Debian
- **Location: Chicago** (closest to Hypixel)

## Setup

### 1. Create Instance
1. Sign up with provider
2. Create Ubuntu/Debian instance
3. Choose $5-6/mo plan
4. Select **Chicago** datacenter
5. Add SSH key (recommended)

### 2. Connect
**Linux/macOS:**
```bash
ssh root@your-vps-ip
```

**Windows:** Use Termius

### 3. Install Node.js
```bash
sudo apt update && sudo apt upgrade -y
curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash -
sudo apt-get install -y nodejs
node --version  # Verify v18+
```

### 4. Install Tools
```bash
sudo apt install tmux git -y
```

### 5. Get TPM
```bash
mkdir -p ~/tpm && cd ~/tpm
# Download from GitHub releases or git clone
```

### 6. Configure
```bash
nano config.json5
```

See [Config Structure](../configuration/config-structure.md).

### 7. Test
```bash
node index.js
```

Should see: Bot → Hypixel → Coflnet → Ready

## Running 24/7

**Tmux:**
```bash
tmux
cd ~/tpm && node index.js
# Ctrl+B, then D to detach
tmux a  # Reattach
```

**PM2:**
```bash
npm install -g pm2
pm2 start index.js --name tpm
pm2 logs tpm
pm2 restart tpm
```

## Maintenance

**Check resources:**
```bash
free -h    # Memory
df -h      # Disk
top        # CPU
```

**Update:**
```bash
sudo apt update && sudo apt upgrade -y
```

## Security

1. Use SSH keys
2. Keep system updated
3. Backup config.json5 regularly

## Troubleshooting

**Won't start:** Check Node.js version and config syntax

**Disconnects:** Check `ping mc.hypixel.net` and RAM

**Can't connect:** Verify IP, check VPS running, port 22 open

---

**See also:** [Installation](../getting-started/installation.md) | [Multiple Accounts](multiple-accounts.md) | [Auto-Rotation](auto-rotation.md)
