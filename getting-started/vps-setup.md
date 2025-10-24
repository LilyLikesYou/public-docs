---
description: Complete guide to setting up a Virtual Private Server (VPS) for running TPM
icon: server
---

# VPS Setup Guide

This guide will walk you through setting up a Virtual Private Server (VPS) to run TPM, the SkyCofl Minecraft automation tool. A VPS provides a reliable, always-on environment for your Minecraft automation tasks.

## What is a VPS?

A Virtual Private Server (VPS) is a virtualized server that runs in the cloud. Unlike shared hosting, a VPS gives you dedicated resources (CPU, RAM, storage) and full control over the server environment. This makes it ideal for running automation tools like TPM that need to be available 24/7.

### Why Use a VPS for TPM?

* **24/7 Uptime** - Your automation scripts run continuously without relying on your personal computer
* **Dedicated Resources** - Consistent performance without interference from other users
* **Remote Access** - Manage TPM from anywhere with an internet connection
* **Scalability** - Easily upgrade resources as your needs grow
* **Reliability** - Professional-grade infrastructure with backup systems

## Prerequisites

Before setting up your VPS, you'll need:

* A VPS provider account (we recommend DigitalOcean, Linode, or Vultr)
* Basic familiarity with command-line interfaces
* An SSH client (built into macOS/Linux, use PuTTY for Windows)
* Your Minecraft server details for TPM configuration

## Choosing a VPS Provider

### Recommended Providers

1. **DigitalOcean** - User-friendly interface, good documentation, $5/month starter plans
2. **Linode** - Excellent performance, competitive pricing, strong community
3. **Vultr** - Global server locations, affordable options
4. **Hetzner** - Great value for European users
5. **AWS Lightsail** - Good if you're already using AWS services

### Minimum Requirements for TPM

* **CPU**: 1 vCPU (2 vCPUs recommended for better performance)
* **RAM**: 1GB minimum (2GB recommended)
* **Storage**: 25GB SSD
* **Operating System**: Ubuntu 22.04 LTS or Ubuntu 20.04 LTS
* **Network**: 1TB bandwidth per month

{% hint style="info" %}
**Budget Tip**: Most providers offer $5-6/month plans that meet the minimum requirements. Start with a basic plan and upgrade if needed.
{% endhint %}

## Step 1: Create Your VPS

### DigitalOcean Example

1. **Sign up** for a DigitalOcean account at [digitalocean.com](https://www.digitalocean.com)
2. Click **Create** → **Droplets**
3. Choose **Ubuntu 22.04 LTS** as your operating system
4. Select a plan (Basic $6/month plan is sufficient to start)
5. Choose a datacenter region closest to your Minecraft server
6. Select **SSH Key** authentication (more secure than password)
7. Give your droplet a hostname (e.g., "tpm-server")
8. Click **Create Droplet**

### Other Providers

The process is similar across providers:
- Choose Ubuntu 22.04 LTS as the OS
- Select appropriate resources (1-2GB RAM minimum)
- Configure SSH key authentication
- Note your server's IP address after creation

## Step 2: Connect to Your VPS

### From Linux/macOS

Open a terminal and connect via SSH:

```bash
ssh root@your-server-ip
```

Replace `your-server-ip` with your VPS's actual IP address.

### From Windows

1. Download and install [PuTTY](https://www.putty.org/)
2. Open PuTTY
3. Enter your server IP in the "Host Name" field
4. Port: 22
5. Click "Open"
6. Login as: `root`
7. Enter your password when prompted

{% hint style="success" %}
**First Time Connection**: You'll see a security warning about the server's fingerprint. This is normal - type "yes" to continue.
{% endhint %}

## Step 3: Initial Server Setup

Once connected, secure your server with these essential steps:

### Update System Packages

```bash
# Update package lists
sudo apt update

# Upgrade installed packages
sudo apt upgrade -y
```

### Create a Non-Root User

Running applications as root is a security risk. Create a dedicated user for TPM:

```bash
# Create a new user (replace 'tpmuser' with your preferred username)
adduser tpmuser

# Add user to sudo group
usermod -aG sudo tpmuser
```

### Configure Firewall

```bash
# Enable UFW firewall
sudo ufw allow OpenSSH
sudo ufw enable

# Allow additional ports if needed for Minecraft
# sudo ufw allow 25565/tcp  # Minecraft default port
```

### Set Up SSH Key Authentication (if not done during creation)

For better security, use SSH keys instead of passwords:

```bash
# On your local machine (not the VPS), generate SSH key if you don't have one
ssh-keygen -t ed25519 -C "your_email@example.com"

# Copy your public key to the VPS
ssh-copy-id tpmuser@your-server-ip
```

## Step 4: Install Java

TPM requires Java to run. Install OpenJDK:

```bash
# Install Java 17 (recommended for Minecraft 1.18+)
sudo apt install openjdk-17-jdk -y

# Verify installation
java -version
```

{% hint style="info" %}
**Java Version**: If you're running an older Minecraft version, you might need Java 8 or Java 11. Check TPM's specific requirements.
{% endhint %}

## Step 5: Install Required Dependencies

Install additional tools TPM might need:

```bash
# Install essential build tools
sudo apt install build-essential -y

# Install git for version control
sudo apt install git -y

# Install screen or tmux for running TPM in the background
sudo apt install screen -y

# Install curl and wget for downloading files
sudo apt install curl wget -y
```

## Step 6: Download and Install TPM

Switch to your TPM user and download TPM:

```bash
# Switch to the TPM user
su - tpmuser

# Create a directory for TPM
mkdir ~/tpm
cd ~/tpm

# Download TPM (replace with actual download URL)
# wget https://example.com/tpm/latest/tpm.jar

# Make TPM executable if needed
# chmod +x tpm.jar
```

{% hint style="warning" %}
**Important**: Replace the download URL with the actual TPM download link from the official SkyCofl repository or website.
{% endhint %}

## Step 7: Configure TPM

Create a configuration file for TPM:

```bash
# Create config directory
mkdir -p ~/tpm/config

# Edit the configuration file
nano ~/tpm/config/tpm.conf
```

Add your basic configuration (example):

```yaml
# TPM Configuration
minecraft:
  server_address: "your-minecraft-server.com"
  port: 25565
  
automation:
  enabled: true
  interval: 60  # seconds

logging:
  level: "INFO"
  file: "logs/tpm.log"
```

Save and exit (Ctrl+X, then Y, then Enter in nano).

## Step 8: Run TPM

### Run TPM in the Foreground (for testing)

```bash
cd ~/tpm
java -jar tpm.jar
```

### Run TPM in the Background with Screen

For production use, run TPM in a screen session so it continues running when you disconnect:

```bash
# Start a new screen session
screen -S tpm

# Run TPM
cd ~/tpm
java -jar tpm.jar

# Detach from screen: Press Ctrl+A, then D
```

To reattach to the screen session later:

```bash
screen -r tpm
```

### Create a Systemd Service (Advanced)

For automatic startup on boot, create a systemd service:

```bash
sudo nano /etc/systemd/system/tpm.service
```

Add this content:

```ini
[Unit]
Description=TPM Minecraft Automation
After=network.target

[Service]
Type=simple
User=tpmuser
WorkingDirectory=/home/tpmuser/tpm
ExecStart=/usr/bin/java -jar /home/tpmuser/tpm/tpm.jar
Restart=on-failure
RestartSec=10

[Install]
WantedBy=multi-user.target
```

Enable and start the service:

```bash
sudo systemctl enable tpm
sudo systemctl start tpm
sudo systemctl status tpm
```

## Step 9: Monitor and Maintain Your VPS

### Check TPM Status

```bash
# If using screen
screen -r tpm

# If using systemd
sudo systemctl status tpm
sudo journalctl -u tpm -f  # View logs
```

### Regular Maintenance Tasks

```bash
# Update system packages weekly
sudo apt update && sudo apt upgrade -y

# Check disk space
df -h

# Check memory usage
free -h

# View TPM logs
tail -f ~/tpm/logs/tpm.log
```

### Backup Your Configuration

Regularly backup your TPM configuration:

```bash
# Create backup directory
mkdir -p ~/backups

# Backup TPM config
tar -czf ~/backups/tpm-config-$(date +%Y%m%d).tar.gz ~/tpm/config/
```

## Troubleshooting

### Can't Connect to VPS

1. Verify the IP address is correct
2. Check if the VPS is running in your provider's dashboard
3. Ensure your firewall allows SSH connections
4. Try accessing via the provider's web console

### TPM Won't Start

1. Check Java is installed: `java -version`
2. Verify TPM file exists and has correct permissions
3. Check configuration file syntax
4. Review error logs: `cat ~/tpm/logs/tpm.log`

### Out of Memory

1. Check memory usage: `free -h`
2. Increase JVM memory allocation: `java -Xmx1G -jar tpm.jar`
3. Consider upgrading your VPS plan

### Connection to Minecraft Server Fails

1. Verify Minecraft server address and port in config
2. Check firewall rules allow outbound connections
3. Test connection manually: `telnet minecraft-server.com 25565`

## Security Best Practices

### Essential Security Measures

1. **Keep System Updated**: Run `apt update && apt upgrade` regularly
2. **Use SSH Keys**: Disable password authentication
3. **Enable Firewall**: Only allow necessary ports
4. **Regular Backups**: Backup configurations and data
5. **Monitor Logs**: Check for suspicious activity
6. **Use Strong Passwords**: If password auth is necessary

### Disable Password Authentication (Recommended)

After setting up SSH keys:

```bash
sudo nano /etc/ssh/sshd_config
```

Find and change:
```
PasswordAuthentication no
```

Restart SSH:
```bash
sudo systemctl restart sshd
```

## Next Steps

Now that your VPS is set up and running TPM:

* [Configure TPM Features](../creating-content/formatting/)
* [Set Up Automation Scripts](../creating-content/blocks/)
* [Monitor TPM Performance](../help/)
* [Join the Community](../help/support.md)

## Additional Resources

* [VPS Provider Comparisons](#)
* [Linux Command Line Basics](#)
* [SSH Key Management](#)
* [Minecraft Server Setup](#)

{% hint style="success" %}
**Congratulations!** Your VPS is now set up and running TPM. Check the [Quickstart Guide](quickstart.md) for next steps in configuring TPM's automation features.
{% endhint %}
