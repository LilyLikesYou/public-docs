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

**Token Authentication** (length > 16 characters):
```javascript
igns: [
    "verylong token here12345",
    "another token string67890"
]
```

**Microsoft Authentication** (username/email):
```javascript
igns: [
    "username1",
    "username2@email.com"
]
```

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

### Strategy 3: Rotation Strategy

Accounts rotate on/off to avoid detection:

**Setup:**
```javascript
autoRotate: {
    "Account1": "r2:3f1",  // Rest 2h, flip 3h, friend 1h
    "Account2": "r1:2f2",  // Rest 1h, flip 2h, friend 2h
    "Account3": "r3:4f1"   // Rest 3h, flip 4h, friend 1h
}
```

**Use Case:**
- Avoiding detection
- Splitting uptime
- Reducing risk

### Strategy 4: Main + Backup

One main account with backup accounts:

**Setup:**
- Main account: aggressive settings, high volume
- Backup accounts: conservative, lower volume

**Use Case:**
- Risk management
- Main account for primary profits
- Backups for safety

## Monitoring Multiple Accounts

### Discord Notifications

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
- Check each account's `/cofl status`
- Verify all configs loaded
- Check individual filters
- Ensure Cofl connection active

## Advanced Multi-Account Setup

### Load Balancing

Distribute flips across accounts:

```javascript
// Configure different maxprice per account
// Account 1: focus on cheap items (< 50M)
// Account 2: focus on medium items (50-200M)
// Account 3: focus on expensive items (> 200M)
```

### Specialized Accounts

Each account specializes:
- **Account 1**: Pets only
- **Account 2**: Weapons/Armor
- **Account 3**: Materials/Resources

### Rotation Scheduling

Complex rotation schedules:

```javascript
autoRotate: {
    "Account1": "r0:6f2",   // Active 6h, friend 2h, no rest
    "Account2": "r4:4f0",   // Rest 4h, active 4h, no friend
    "Account3": "r2:3f3"    // Balanced rotation
}
```

## Cost Considerations

### Single VPS vs Multiple

**Single VPS (Recommended for 2-4 accounts):**
- More cost-effective
- Easier to manage
- Shared resources

**Multiple VPS (For 5+ accounts):**
- Better performance
- More reliable
- Higher cost

### Example Costs

- 1-2 accounts: $5-6/mo VPS
- 3-4 accounts: $10-12/mo VPS
- 5-6 accounts: $20/mo VPS or 2x $10/mo VPS
- 6+ accounts: Multiple VPS instances

## Security Considerations

### Account Safety

- Don't run too many accounts from one IP
- Use rotation to appear more natural
- Monitor for unusual patterns
- Follow Hypixel rules

### Configuration Security

- Keep config.js secure
- Each account should have strong credentials
- Regular backups
- Don't share account details

## Example Multi-Account Config

```javascript
module.exports = {
    // Three accounts
    igns: ["MainFlipAccount", "AltAccount1", "AltAccount2"],

    // Discord
    discordID: "backend-id",
    webhook: "main-webhook-url",

    // Authentication
    session: "coflnet-password",

    // Global settings
    delay: 250,
    bedSpam: true,

    // Flipping config
    percentOfTarget: {
        "0-10000000": 0.95,
        "10000000-999999999": 0.97
    },

    // Auto-rotation (each account has different schedule)
    autoRotate: {
        "MainFlipAccount": "r2:4f1",
        "AltAccount1": "r1:3f2",
        "AltAccount2": "r3:3f1"
    },

    // Other settings
    relist: true,
    useCookie: true,
    angryCoopPrevention: true
}
```

## Next Steps

- Set up [Auto-Rotation](auto-rotation.md) for your accounts
- Review [VPS Setup](vps-setup.md) for resource requirements
- Optimize [Filters and Settings](../configuration/filters-and-settings.md)
- Monitor using [Troubleshooting Guide](../troubleshooting/common-issues.md)

## Summary

**Multi-Account Checklist:**
- [ ] Sufficient VPS resources
- [ ] Multiple Minecraft accounts
- [ ] Configure igns array
- [ ] Set up monitoring (webhooks)
- [ ] Load configs per account
- [ ] Test each account
- [ ] Implement rotation (if desired)
- [ ] Monitor performance
- [ ] Optimize settings per account

Running multiple accounts can significantly increase profits, but requires proper configuration and monitoring!
