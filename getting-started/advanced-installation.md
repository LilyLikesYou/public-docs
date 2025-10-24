---
description: >-
  Advanced installation options and configuration for TPM
icon: gear
---

# Advanced Installation

This guide covers advanced installation methods and configuration options for TPM beyond the basic [Quickstart](quickstart.md) guide.

## Installation Methods

### Method 1: Direct Download (Recommended)

The simplest way to install TPM is to download the latest release directly:

```bash
# Create TPM directory
mkdir -p ~/tpm && cd ~/tpm

# Download latest release
wget https://github.com/skycofl/tpm/releases/latest/download/tpm.jar

# Verify the download
ls -lh tpm.jar
```

### Method 2: Git Clone (For Developers)

If you want to contribute to TPM or use development versions:

```bash
# Clone the repository
git clone https://github.com/skycofl/tpm.git
cd tpm

# Build from source (if applicable)
./gradlew build

# Or use Maven
mvn clean package
```

### Method 3: Package Managers (If Available)

Some systems may offer TPM through package managers:

```bash
# Example: Using a hypothetical package manager
# apt install tpm-skycofl

# Or using snap
# snap install tpm
```

{% hint style="warning" %}
**Note**: Replace URLs with actual TPM download locations from the official SkyCofl repository.
{% endhint %}

## System Requirements

### Minimum Requirements

* **OS**: Ubuntu 20.04 LTS or newer (or equivalent Linux distribution)
* **Java**: OpenJDK 17 or higher
* **RAM**: 1GB available memory
* **CPU**: 1 vCPU
* **Storage**: 500MB free space
* **Network**: Stable internet connection

### Recommended Requirements

* **OS**: Ubuntu 22.04 LTS
* **Java**: OpenJDK 17 or OpenJDK 21
* **RAM**: 2GB available memory
* **CPU**: 2 vCPUs
* **Storage**: 2GB free space
* **Network**: Low-latency connection to Minecraft server

## Configuration

### Basic Configuration File

Create a configuration file at `~/tpm/config/config.yml`:

```yaml
# TPM Configuration File
# Server connection settings
server:
  host: "mc.example.com"
  port: 25565

# Automation settings
automation:
  enabled: true
  interval: 60  # Check interval in seconds
  
  # Enable specific modules
  modules:
    resource_gathering: true
    inventory_management: true
    auto_crafting: false

# Logging configuration
logging:
  level: INFO  # DEBUG, INFO, WARN, ERROR
  file: logs/tpm.log
  console: true
  max_file_size: 10MB
  max_files: 5

# Performance settings
performance:
  threads: 2
  memory_limit: 1024M
```

## Next Steps

After installation:

* [Configure TPM features](../creating-content/formatting/)
* [Set up a VPS](vps-setup.md) for 24/7 operation
* [Read the glossary](../resources/glossary.md) to understand terminology
* [Join the community](../help/) for support

{% hint style="success" %}
**Installation Complete!** You're ready to start using TPM. Check the [Quickstart Guide](quickstart.md) for your first steps.
{% endhint %}
