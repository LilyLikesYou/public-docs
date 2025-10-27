# Installation

## TPM+ Users

TPM+ is hosted by Coflnet - no installation required. See [TPM+ Overview](../tpm-plus/overview.md).

## Standard TPM (VPS)

### 1. Setup VPS
Get a VPS with 1GB RAM, 1 CPU core. See [VPS Setup Guide](../advanced/vps-setup.md).

### 2. Install Node.js
```bash
curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash -
sudo apt-get install -y nodejs
```

### 3. Get TPM Files
Contact TPM team for access, then:
```bash
mkdir tpm && cd tpm
# Download/clone TPM files (link from TPM team)
npm install
```

### 4. Configure
Edit `config.json5`:
```javascript
module.exports = {
    igns: ["YourMinecraftUsername"],
    webhook: "your-discord-webhook-url",
    session: "your-coflnet-password",
    // See Config Structure docs for more options
}
```

Get configs from [Config Hub Discord](https://discord.gg/cfghub).

### 5. Start TPM
```bash
node index.js
```

### Keep Running (Optional)
**Tmux:**
```bash
sudo apt-get install tmux
tmux  # Start session
node index.js
# Ctrl+B, then D to detach
# tmux a to reattach
```

**PM2:**
```bash
npm install -g pm2
pm2 start index.js --name tpm
pm2 logs tpm
```

## Troubleshooting

**Node.js version:** Requires v16+
```bash
node --version
```

**Permissions:**
```bash
sudo chown -R $USER:$USER /path/to/tpm
```

**Authentication cache issues:**
```bash
sudo rm -rf /root/.minecraft/
```

---

**Next:** [Quickstart Guide](quickstart.md) | [Config Structure](../configuration/config-structure.md) | [Troubleshooting](../troubleshooting/common-issues.md)
