---
description: Get up and running quickly with TPM and start automating your Minecraft server
icon: bolt
---

# Quickstart

Welcome to TPM! This quickstart guide will help you install and configure TPM to start automating your Minecraft server tasks.

### Prerequisites

Before you begin, make sure you have:

* A VPS or server running Ubuntu 20.04+ or similar Linux distribution ([VPS Setup Guide](vps-setup.md))
* Java 17 or higher installed
* Access to a Minecraft server (or server details for connection)
* Basic knowledge of command-line tools
* SSH access to your server

{% hint style="info" %}
**New to VPS?** Check out our comprehensive [VPS Setup Guide](vps-setup.md) first to get your server ready for TPM.
{% endhint %}

### Installation

#### Step 1: Install Java (if not already installed)

```bash
# Update package lists
sudo apt update

# Install Java 17
sudo apt install openjdk-17-jdk -y

# Verify installation
java -version
```

#### Step 2: Download TPM

```bash
# Create TPM directory
mkdir -p ~/tpm
cd ~/tpm

# Download the latest TPM release
# Replace with actual download URL from SkyCofl
wget https://github.com/skycofl/tpm/releases/latest/download/tpm.jar

# Verify the download
ls -lh tpm.jar
```

{% hint style="warning" %}
**Note**: Replace the download URL with the actual TPM download link from the official SkyCofl repository.
{% endhint %}

#### Step 3: Create Configuration File

Create a basic configuration file for TPM:

```bash
# Create config directory
mkdir -p ~/tpm/config

# Create configuration file
nano ~/tpm/config/config.yml
```

Add your basic configuration:

```yaml
# TPM Configuration File
server:
  # Your Minecraft server details
  host: "mc.example.com"
  port: 25565
  
automation:
  # Enable automation features
  enabled: true
  
  # Automation check interval (in seconds)
  interval: 60
  
logging:
  # Log level: DEBUG, INFO, WARN, ERROR
  level: INFO
  
  # Log file location
  file: logs/tpm.log
```

Save and exit (Ctrl+X, then Y, then Enter).

### Quick Setup

#### 1. Test TPM Installation

Run TPM to verify it's working:

```bash
cd ~/tpm
java -jar tpm.jar --version
```

You should see TPM's version information.

#### 2. Run TPM for the First Time

```bash
java -jar tpm.jar
```

TPM will start and display its initialization process. Watch for any errors in the output.

#### 3. Run TPM in Background (Screen)

For continuous operation, use screen:

```bash
# Start a new screen session
screen -S tpm

# Run TPM
cd ~/tpm
java -jar tpm.jar

# Detach from screen: Press Ctrl+A, then D
```

To return to the TPM session:

```bash
screen -r tpm
```

#### 4. Verify TPM is Running

Check that TPM is active and connected:

```bash
# View logs
tail -f ~/tpm/logs/tpm.log

# Check process
ps aux | grep tpm
```

### Basic Commands

Common TPM commands to get started:

```bash
# Start TPM
java -jar tpm.jar

# Start with custom config location
java -jar tpm.jar --config /path/to/config.yml

# Run in debug mode
java -jar tpm.jar --debug

# Check version
java -jar tpm.jar --version

# Display help
java -jar tpm.jar --help
```

### Next Steps

Now that you have TPM up and running, explore these features:

* [Configure Automation Features](../creating-content/formatting/) - Set up automated tasks
* [Understand TPM Terminology](../resources/glossary.md) - Learn key concepts
* [Explore Advanced Configuration](../creating-content/blocks/) - Customize TPM behavior
* [Browse Link Dictionary](../resources/link-dictionary.md) - Access important resources

### Common First Tasks

#### Enable Specific Automation Modules

Edit your config file to enable specific features:

```yaml
automation:
  enabled: true
  modules:
    - resource_gathering
    - inventory_management
    - auto_crafting
```

#### Connect to Minecraft Server

Ensure your Minecraft server details are correct in the config:

```yaml
server:
  host: "your-server.com"
  port: 25565
  username: "TPMBot"  # If authentication is needed
```

#### Set Up Logging

Configure detailed logging for troubleshooting:

```yaml
logging:
  level: DEBUG
  file: logs/tpm.log
  console: true
  rotate: true
  max_size: 10MB
```

### Getting Help

If you run into any issues:

* Check our [VPS Setup Guide](vps-setup.md) for server-related issues
* Review the [Troubleshooting Guide](git-sync/troubleshooting.md) for common problems
* Visit the [Glossary](../resources/glossary.md) to understand TPM terminology
* Check the [Link Dictionary](../resources/link-dictionary.md) for helpful resources
* Join the SkyCofl community forum
* [Contact support](../help/)

{% hint style="success" %}
**Ready to dive deeper?** Check out our [comprehensive user guide](../creating-content/formatting/) for detailed information on all TPM automation features.
{% endhint %}

## Troubleshooting

### TPM Won't Start

* Verify Java is installed: `java -version`
* Check configuration file syntax
* Review log files for errors: `cat ~/tpm/logs/tpm.log`

### Can't Connect to Minecraft Server

* Verify server address and port in config.yml
* Check network connectivity: `ping your-server.com`
* Ensure firewall allows outbound connections

### Permission Errors

* Check file permissions: `ls -l ~/tpm/`
* Ensure TPM has write access to logs directory
* Run with appropriate user privileges

For more detailed troubleshooting, see our [Help & Support](../help/) section.
