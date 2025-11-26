# Multiple Accounts

Guide to running TPM with multiple Minecraft accounts simultaneously.

## Overview

TPM supports running multiple Minecraft accounts from a single instance, allowing you to:
- Flip on multiple accounts simultaneously
- Diversify your flipping strategies
- Maximize profit opportunities
- Split risk across accounts

## Prerequisites

Before running multiple accounts:

- Multiple Minecraft accounts
- Sufficient VPS resources (see below)
- Separate Coflnet sessions (or shared, depending on setup)
- Discord webhooks for monitoring (recommended)

## Resource Requirements

### RAM Requirements

- **1 account**: 1GB RAM sufficient
- **2-3 accounts**: 2GB RAM recommended
- **4-5 accounts**: 4GB RAM recommended
- **6+ accounts**: 8GB RAM or multiple VPS instances

### CPU Requirements

- 1 vCPU adequate for 1-2 accounts
- 2 vCPU recommended for 3+ accounts

### Network

- Each account uses additional bandwidth
- Monitor bandwidth usage
- Most VPS plans include sufficient bandwidth

## Configuration

### Basic Multi-Account Setup

In your `config.js`, specify multiple accounts in the `igns` array:

```javascript
module.exports = {
    igns: ["Account1", "Account2", "Account3"],

    discordID: "your-backend-id",
    webhook: "your-webhook",
    session: "your-coflnet-password",

    // ... other settings apply to all accounts
}
```

### Account-Specific Settings

Some settings can be configured per-account:

```javascript
module.exports = {
    igns: ["MainAccount", "AltAccount1", "AltAccount2"],

    // Global settings
    webhook: "main-webhook",
    session: "coflnet-password",

    // Account-specific auto-rotation
    autoRotate: {
        "MainAccount": "r2:3f1",
        "AltAccount1": "r1:2f2",
        "AltAccount2": "r3:4f1"
    }
}
```

## Managing Multiple Accounts

### Authentication

- Auth cache can be cleared via `sudo rm -rf root/.minecraft/`
- This fixes most auth issues 

### Separate Discord Webhooks

Use different webhooks for each account to track them separately:

This requires running separate TPM instances, or configure a single webhook and differentiate by username in messages.

### Command Routing

TPM includes a prefix system for sending commands to specific bots:

```javascript
// In terminal
prefix_accountname: command
```

Example:
```
main: chat Hello from main account
alt1: chat Hello from alt 1
```

## Strategies for Multiple Accounts

### Strategy 1: Same Config, Different Thresholds

All accounts use the same config but with different profit thresholds:

**Setup:**
- All accounts load same config
- Adjust minprofit per account via `/cofl set minprofit`

**Use Case:**
- Different purse sizes
- Risk diversification
- Testing different thresholds

### Strategy 2: Different Configs

Each account uses a different config:

**Setup:**
- Load different configs per account in-game
- Each optimized for different item types

**Use Case:**
- Specialization (one for pets, one for armor, etc.)
- Different strategies
- Different markets

**Option 1: Single Webhook**

All accounts post to one webhook:
- Easier to monitor
- All notifications in one place
- Use account names to differentiate

**Option 2: Multiple Webhooks**

Each account has its own webhook:
- Organized by account
- Separate Discord channels
- Easier to track individual performance

### Console Monitoring

Use terminal multiplexer for monitoring:

```bash
# Using screen with multiple windows
screen -S tpm
# Ctrl+A, C to create new window
# Ctrl+A, " to list windows
# Ctrl+A, [number] to switch

# Using tmux
tmux new -s tpm
# Ctrl+B, C to create new window
# Ctrl+B, W to list windows
```

### Performance Tracking

Track metrics for each account:
- Purchases per day
- Total profit
- Success rate
- Average profit per flip

## Best Practices

### 1. Start Small

Begin with 1-2 accounts:
- Learn the system
- Optimize settings
- Then scale up

### 2. Monitor Resources

Watch VPS resources:
```bash
# Check memory
free -h

# Check CPU
top

# Check network
ifconfig
```

### 3. Stagger Account Start Times

Don't start all accounts simultaneously:
- Reduce initial load
- Avoid connection issues
- Spread resource usage

### 4. Use Different Strategies

Diversify your approach:
- Different profit thresholds
- Different item categories
- Different configs
- Different risk levels

### 5. Regular Monitoring

Check accounts regularly:
- Verify all running
- Check for errors
- Monitor profits
- Adjust settings

## Troubleshooting

### Out of Memory

**Symptoms:**
- Bot crashes
- Slow performance
- Error messages

**Solutions:**
```bash
# Check memory usage
free -h

# Reduce number of accounts
# Or upgrade VPS plan
```

### Accounts Disconnecting

**Symptoms:**
- Frequent disconnects
- Connection errors
- Bot restarts

**Solutions:**
- Check network stability
- Reduce concurrent accounts
- Upgrade VPS resources
- Check Hypixel connection

### Can't Track Which Account

**Symptoms:**
- Confusion about which account did what
- Mixed notifications

**Solutions:**
- Use separate Discord webhooks
- Check console output
- Use descriptive account names
- Implement better logging

### Some Accounts Not Receiving Flips

**Symptoms:**
- Uneven flip distribution
- Some accounts idle

**Solutions:**
- Verify all configs loaded
- Check individual filters
- Ensure Cofl connection active
- Contact VPS provider

## Next Steps

- Set up [Auto-Rotation](auto-rotation.md) for your accounts
- Review [VPS Setup](vps-setup.md) for resource requirements
- Optimize [Filters and Settings](../configuration/filters-and-settings.md)
- Monitor using [Troubleshooting Guide](../troubleshooting/common-issues.md)


Running multiple accounts can significantly increase profits, but requires proper configuration and monitoring!
