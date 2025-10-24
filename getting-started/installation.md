# Installation

This guide walks you through installing TPM on your system.

## Installation Methods

The installation process varies depending on whether you're using standard TPM or TPM+, and whether you're running on a VPS or locally.

## For Standard TPM (VPS)

### Step 1: Set Up Your VPS

If you're using standard TPM, you'll need a VPS. See the [VPS Setup Guide](../advanced/vps-setup.md) for detailed instructions.

### Step 2: Install Node.js

TPM requires Node.js to run. Install Node.js on your VPS:

```bash
# Ubuntu/Debian
curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash -
sudo apt-get install -y nodejs

# Verify installation
node --version
npm --version
```

### Step 3: Download TPM

Contact the TPM team to get access to the TPM files. Once you have access:

```bash
# Create a directory for TPM
mkdir tpm
cd tpm

# Download/clone the TPM files
# (Instructions will be provided by TPM team)
```

### Step 4: Install Dependencies

```bash
npm install
```

### Step 5: Configure TPM

Create or edit your `config.js` file with your settings:

```javascript
module.exports = {
    igns: ["YourMinecraftUsername"],
    discordID: "your-discord-id",
    webhook: "your-discord-webhook-url",
    session: "your-coflnet-password",
    // Add other configuration options
}
```

See the [Config Structure](../configuration/config-structure.md) documentation for all available options.

### Step 6: Start TPM

```bash
node index.js
```

Your bot should now connect to Hypixel and start receiving flip notifications from Coflnet!

## For TPM+

TPM+ may have a different installation process. See the [TPM+ documentation](../tpm-plus/overview.md) for specific installation instructions.

## Configuration Files

TPM requires a configuration file (`config.js`) with the following key settings:

### Essential Configuration

```javascript
{
    // Minecraft Accounts
    igns: ["account1", "account2"],

    // Discord Integration
    webhook: "your-webhook-url",

    // Coflnet Authentication
    session: "your-coflnet-password",

    // Timing Settings
    delay: 250,
    waittime: 15,
    clickDelay: 100,

    // Flipping Settings
    percentOfTarget: {...},
    listHours: {...},
    relist: true
}
```

For a complete guide on configuration options, see:
- [Config Structure](../configuration/config-structure.md)
- [Filters and Settings](../configuration/filters-and-settings.md)

## Verifying Installation

After starting TPM, check for:

1. **Console Output**: Look for successful connection messages
2. **Discord Notifications**: You should receive a startup notification if webhooks are configured
3. **Minecraft Connection**: The bot should log into your Minecraft account and join Hypixel
4. **Coflnet Connection**: The bot should connect to the Coflnet WebSocket

## Common Installation Issues

### Node.js Version Issues

TPM requires Node.js 16 or higher. Check your version:

```bash
node --version
```

### Permission Errors

If you encounter permission errors on Linux:

```bash
sudo chown -R $USER:$USER /path/to/tpm
```

### Network Issues

Ensure your firewall allows outbound connections to:
- Hypixel servers (mc.hypixel.net)
- Coflnet servers
- Discord (if using webhooks)

## Screen/PM2 for Persistent Running

To keep TPM running even after closing your terminal:

### Using Screen

```bash
# Install screen
sudo apt-get install screen

# Start a new screen session
screen -S tpm

# Start TPM
node index.js

# Detach from screen: Ctrl+A, then D
# Reattach to screen: screen -r tpm
```

### Using PM2

```bash
# Install PM2
npm install -g pm2

# Start TPM with PM2
pm2 start index.js --name tpm

# View logs
pm2 logs tpm

# Stop TPM
pm2 stop tpm
```

## Next Steps

Now that TPM is installed:
1. Follow the [Quickstart Guide](quickstart.md) to configure your first flips
2. Learn about [Loading Configs](../guides/loading-configs.md)
3. Customize your [Filters and Settings](../configuration/filters-and-settings.md)

## Getting Help

If you encounter issues during installation:
- Check the [Troubleshooting Guide](../troubleshooting/common-issues.md)
- Contact TPM support through Discord
- Ensure all [Prerequisites](prerequisites.md) are met
