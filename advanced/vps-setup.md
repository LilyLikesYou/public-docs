# VPS Setup Guide

This guide explains how to set up a Virtual Private Server (VPS) for running standard TPM 24/7.

## When Do You Need a VPS?

**Standard TPM users**: A VPS is required to run TPM 24/7 without keeping your personal computer on.

**TPM+ users**: TPM+ can only he hosted via the CoflNet discord bot.

## What is a VPS?

A Virtual Private Server (VPS) is a virtualized server that runs in the cloud, providing:

- **24/7 Uptime**: Bot runs continuously without relying on your PC
- **Dedicated Resources**: Consistent performance
- **Remote Access**: Manage TPM from anywhere
- **Reliability**: Professional infrastructure

## Recommended VPS Providers

As mentioned in the user-provided setup guide, these providers are recommended:

### 1. Vultr
- Good performance
- Affordable pricing
- Multiple locations
- Easy setup

**Website**: vultr.com

### 2. Linode
- Excellent performance
- Reliable service
- Good support
- Competitive pricing

**Website**: linode.com

### Other Options
- DigitalOcean
- Hetzner
- AWS Lightsail

## Minimum Requirements

For running TPM:

- **CPU**: 1 vCPU (adequate for single account)
- **RAM**: 1GB minimum (2GB recommended for multiple accounts)
- **Storage**: 25GB SSD
- **OS**: Ubuntu or Debian
- **Network**: 1TB bandwidth/month

**Cost**: Typically $5-6/month for basic plans

## Setting Up Your VPS

### Step 1: Create VPS Instance

1. Sign up with your chosen provider
2. Create a new instance/droplet
3. Select **Ubuntu or Debian** as OS
4. Choose appropriate plan ($5-6/month is sufficient)
5. Select datacenter region (closer to Hypixel servers is better - CHICAGO)
6. Add SSH key for security
7. Create the instance

### Step 2: Connect to Your VPS

#### From Linux/macOS:

```bash
ssh root@your-vps-ip
```

#### From Windows:

1. Download Termius
2. Connect to your VPS IP on port 22
3. Login as root

Note: You can alsp use Termius on mobile via the app store.

### Step 3: Initial Server Setup

After connecting, secure and update your server:

```bash
# Update system
sudo apt update && sudo apt upgrade -y

# Configure firewall
sudo ufw allow OpenSSH
sudo ufw enable
```

### Step 4: Install Node.js

TPM requires Node.js (version 16 or higher):

```bash
# Install Node.js 18
curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash -
sudo apt-get install -y nodejs

# Verify installation
node --version
npm --version
```

You should see Node.js v18.x.x and npm version.

### Step 5: Install Required Tools

```bash
# Install tmux for background operation
sudo apt install tmux -y

# Install git (if needed)
sudo apt install git -y
```

### Step 6: Download TPM

```bash
# Create TPM directory
mkdir -p ~/tpm
cd ~/tpm

# Download TPM files (TODO: EXPAND)
- Via TPM-Loader file from Github releases
- By git cloning the repository
```

### Step 7: Install Dependencies

Navigate to the folder that conrainers TPM

```bash
npm install .
```

This installs all required Node.js packages for TPM.

OR, if you are using a loader
```bash
tmux
sudo chmod 777 ./tpm-loader
./tpm-loader
```

### Step 8: Configure TPM

Edit your `config.json5` file:

```bash
nano config.json5
```

Add your configuration (see [Config Structure](../configuration/config-structure.md)):

```json
{TODO: ADD EXTRA INFO}
```

Save and exit (Ctrl+X, then Y, then Enter).

### Step 9: Test TPM

Run TPM to ensure it works:

```bash
node index.js
```

You should see:
- Bot connecting to Minecraft
- Joining Hypixel
- Connecting to Coflnet
- "Ready to receive flips" or similar

If you see errors, check:
- Config.json5 syntax
- Account credentials
- Internet connectivity

Press Ctrl+C to stop.

## Running TPM 24/7

### Using Tmux (Recommended)

Tmux allows TPM to run even after you disconnect from SSH.

**Start TPM in Tmux:**

```bash
# Create a new screen session
tmux

# Start TPM
cd ~/tpm
node index.js

# Detach from screen: Ctrl+A, then D
```

**Useful screen commands:**

```bash
# List screens
tmux -ls

# Reattach to TPM screen
tmux a

# Kill a screen (the ego may die)
screen -X -S tpm quit
```

### Using PM2 (Alternative)

PM2 is a process manager that can auto-restart TPM:

```bash
# Install PM2
npm install -g pm2

# Start TPM with PM2
pm2 start index.js --name tpm

# View logs
pm2 logs tpm

# Stop TPM
pm2 stop tpm

# Restart TPM
pm2 restart tpm

# Auto-start on boot
pm2 startup
pm2 save
```

## Monitoring Your Bot

### Via Discord

If you configured webhooks, monitor through Discord notifications.

### Via Console

```bash
# Reattach to screen
tmux -r tpm

# Or view PM2 logs
pm2 logs tpm
```

## Maintenance

### Regular Updates

Keep your system updated:

```bash
# Update system packages
sudo apt update && sudo apt upgrade -y

# Update TPM (if updates available)
cd ~/tpm
git pull  # if using git
npm install . # update dependencies
```

### Monitoring Resources

```bash
# Check memory usage
free -h

# Check disk space
df -h

# Check CPU usage
top
```

### Restart TPM

```bash
# If using tmux
tmux -X -S tpm quit
tmux -S tpm
node index.js
# Ctrl+A, then D

# If using PM2
pm2 restart
```

## Troubleshooting

### TPM Won't Start

**Check Node.js version:**
```bash
node --version  # Should be 16+
```

**Check config syntax:**
```bash
node -c config.json5 # Check for syntax errors
```

**View error logs:**
- Check console output
- Look for error messages

### Bot Disconnects Frequently

**Check internet connection:**
```bash
ping mc.hypixel.net
```

**Check memory:**
```bash
free -h
```

May need to upgrade VPS plan.

### Can't Connect to VPS

- Verify IP address
- Check VPS is running in provider dashboard
- Ensure firewall allows SSH (port 22)
- Try provider's web console

### Out of Memory

If TPM crashes with memory errors:

```bash
# Check available memory
free -h

# Consider upgrading VPS plan
# Or optimize config to reduce memory usage
```

## Security Best Practices

### Essential Security

1. **Use SSH Keys**: More secure than passwords
2. **Keep Updated**: Regular apt updates
3. **Enable Firewall**: UFW blocks unauthorized access
4. **Strong Passwords**: If using password auth
5. **Backup Configs**: Save config.json5 regularly

### Disable Password Authentication

After setting up SSH keys:

```bash
sudo nano /etc/ssh/sshd_config
```

Set:
```
PasswordAuthentication no
```

Restart SSH:
```bash
sudo systemctl restart sshd
```

### Regular Backups

Backup your configuration:

```bash
# Create backup directory
mkdir -p ~/backups

# Backup config
cp ~/tpm/config.js ~/backups/config-$(date +%Y%m%d).js

# Download to local machine (from your PC):
scp root@vps-ip:~/tpm/config.js ./config-backup.js
```

## Multiple Accounts

If running multiple accounts:

### Resource Requirements

- 1 account: 1GB RAM sufficient
- 2-3 accounts: 2GB RAM recommended
- 4+ accounts: 4GB RAM or multiple VPS instances

### Configuration

```javascript
module.exports = {
    igns: ["Account1", "Account2", "Account3"],
    // ... rest of config
}
```

Each account runs as separate bot instance automatically.

## VPS Cost Comparison

| Provider | Basic Plan | RAM | CPU | Storage |
|----------|-----------|-----|-----|---------|
| Vultr | $5/mo | 1GB | 1 vCPU | 25GB |
| Linode | $5/mo | 1GB | 1 vCPU | 25GB |
| DigitalOcean | $6/mo | 1GB | 1 vCPU | 25GB |
| Hetzner | €4/mo | 2GB | 1 vCPU | 20GB |

## Tips for VPS Usage

### 1. Choose Location Wisely

- Chicago recommended (closer to Hypixel)
- Lower latency = faster flip buying

### 2. Monitor Costs

- Watch bandwidth usage
- Upgrade only when needed
- Most users: $5/mo plan is sufficient

### 3. Keep Configs Secure

- Never share config.json5 (contains session password)
- Use environment variables for sensitive data
- Regular backups

### 4. Document Your Setup

Keep notes on:
- VPS provider and IP
- Login credentials (securely)
- Configuration changes
- Issues and solutions

## Next Steps

After VPS setup:

1. **Configure TPM**: Review [Config Structure](../configuration/config-structure.md)
2. **Load Config**: Follow [Loading Configs](../guides/loading-configs.md)
3. **Optimize Settings**: Read [Filters and Settings](../configuration/filters-and-settings.md)
4. **Set Up Rotation**: Check [Auto-Rotation](auto-rotation.md)

## Getting Help

VPS issues?
- Check provider documentation
- Ask in TPM Discord
- Review [Troubleshooting Guide](../troubleshooting/common-issues.md)

TPM issues?
- Check TPM documentation
- Contact TPM support
- Ask config provider

With your VPS properly set up, TPM can run 24/7 and flip continuously!
