# Installation

## TPM+ Users

TPM+ is hosted by Coflnet - no installation required. See [TPM+ Overview](../tpm-plus/overview.md).

## Standard TPM (VPS)

### 1. Setup VPS
Get a VPS with 1GB RAM, 1 CPU core. See [VPS Setup Guide](../advanced/vps-setup.md).

### 2. Install Node.js
```bash
sudo apt-get install -y nodejs
```

### 3. Get TPM
Visit this [GitHub releases page](https://github.com/IcyHenryT/TPM-Loader/releases/)
Pick the version which fits your chosen OS (in most cases linux if using a VPS)

```bash
mkdir tpm
cd tpm
curl -o TPM-loader-linux https://github.com/IcyHenryT/TPM-Loader/releases/download/1.0.2/TPM-loader-linux
```

### 4. Start TPM
```bash
chmod 777 ./TPM-loader-linux
./TPM-loader-linux
```
Then, press `CTRL+C` twice.

### 5. Configure
Edit `config.json5` using `nano config.json5`
```json
{
    ign: ["YourMinecraftUsername"],
    webhook: "your-discord-webhook-url"
}
```

Get configs from [Config Hub Discord](https://discord.gg/cfghub).

### Keep Running (Optional)
**Tmux:**
```bash
sudo apt-get install tmux
tmux  # Start session
./TPM-loader-linux
# Ctrl+B, then D to detach
# tmux a to reattach
```

**PM2:**
```bash
npm install -g pm2
pm2 start ./TPM-loader-linux --name tpm
pm2 logs tpm
```

## Troubleshooting

**Node.js version:** Requires v16+
```bash
node --version
```

**Permissions:**
```bash
sudo chown -R $USER:$USER /root/tpm/TPM-loader-linux
```

**Authentication cache issues:**
```bash
sudo rm -rf /root/.minecraft/
```

---

**Next:** [Quickstart Guide](quickstart.md) | [Config Structure](../configuration/config-structure.md) | [Troubleshooting](../troubleshooting/common-issues.md)
