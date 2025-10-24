# Auto-Rotation

Guide to using TPM's auto-rotation feature for scheduling account on/off times.

## What is Auto-Rotation?

Auto-rotation automatically schedules when your accounts are active (flipping) or inactive (resting). This helps:
- Avoid detection by appearing more natural
- Manage multiple accounts with different schedules
- Reduce wear on accounts
- Optimize flipping times

## Why Use Auto-Rotation?

### Benefits

1. **Natural Behavior**: Accounts aren't online 24/7
2. **Risk Reduction**: Less suspicious activity patterns
3. **Account Health**: Gives accounts "rest" periods
4. **Time Management**: Auto-switch between flipping and resting
5. **Strategy Diversity**: Different accounts can have different schedules

### When to Use

- Running accounts 24/7 concerns you
- Want to rotate accounts through different time periods
- Managing multiple accounts with different strategies
- Trying to minimize detection risk

## Configuration

### Basic Syntax

In your `config.js`:

```javascript
module.exports = {
    igns: ["Account1", "Account2"],

    autoRotate: {
        "Account1": "r2:3f1",
        "Account2": "r1:4f0"
    }

    // ... other settings
}
```

### Rotation String Format

Format: `"r[hours]:f[hours]f[hours]"`

- `r[hours]` = Rest time (offline)
- `f[hours]` = Flip time (active)
- Can chain multiple periods

**Examples:**

```javascript
"r2:3f1"   // Rest 2h, flip 3h, friend visit 1h
"r1:4f0"   // Rest 1h, flip 4h, no friend visit
"r0:6f2"   // No rest, flip 6h, friend visit 2h
"r3:3f1"   // Rest 3h, flip 3h, friend visit 1h
```

### Components

#### Rest Period (r)

**Format**: `r[hours]`

Account is offline/idle during this time.

**Examples:**
- `r1` = Rest for 1 hour
- `r2` = Rest for 2 hours
- `r0` = No rest period

#### Flip Period (f)

**Format**: `f[hours]`

Account is actively flipping during this time.

**Examples:**
- `f3` = Flip for 3 hours
- `f4` = Flip for 4 hours
- `f6` = Flip for 6 hours

#### Friend Visit (optional)

The second `f` component can represent friend island visits (for special features).

**Examples:**
- `f1` = Visit friend for 1 hour
- `f2` = Visit friend for 2 hours
- `f0` = No friend visit

## Examples

### Example 1: Conservative Rotation

```javascript
autoRotate: {
    "MainAccount": "r4:4f0"  // Rest 4h, flip 4h, no friend
}
```

**Schedule:**
- 4 hours offline
- 4 hours flipping
- Repeats

**Total**: 8-hour cycle, 50% uptime

**Use Case**: Very conservative, appears natural

### Example 2: Aggressive Rotation

```javascript
autoRotate: {
    "Account1": "r1:6f1"  // Rest 1h, flip 6h, friend 1h
}
```

**Schedule:**
- 1 hour offline
- 6 hours flipping
- 1 hour friend visit
- Repeats

**Total**: 8-hour cycle, 75% flipping time

**Use Case**: Maximum flipping time while maintaining some rest

### Example 3: Multiple Accounts Staggered

```javascript
autoRotate: {
    "Account1": "r2:4f2",  // Rest 2h, flip 4h, friend 2h
    "Account2": "r1:5f2",  // Rest 1h, flip 5h, friend 2h
    "Account3": "r3:3f2"   // Rest 3h, flip 3h, friend 2h
}
```

**Result**: Accounts have different schedules, ensuring coverage

**Use Case**: Multiple accounts with rotating coverage

### Example 4: Night/Day Split

```javascript
autoRotate: {
    "DayAccount": "r12:12f0",   // Rest 12h (night), flip 12h (day)
    "NightAccount": "r0:12f12"  // Flip 12h (night), rest 12h (day)
}
```

**Result**: One account active during day, another during night

**Use Case**: 24/7 coverage with two accounts

## Discord Notifications

When auto-rotation occurs, TPM sends Discord notifications:

**Startup Notification:**
```
[Account] is starting up
Next rotation in: [time]
```

**Shutdown Notification:**
```
[Account] is going offline for [duration]
Will return at: [time]
```

**Countdown Updates:**
- Notifications sent at intervals
- Warns before rotation events
- Helps track schedule

## Managing Rotation

### Viewing Current Schedule

Check your config.js for the schedule, or monitor Discord notifications.

### Adjusting Rotation

**To change rotation:**

1. Stop TPM
2. Edit `config.js`
3. Update `autoRotate` values
4. Restart TPM

```bash
# Stop TPM (if using screen)
screen -X -S tpm quit

# Edit config
nano config.js

# Restart TPM
screen -S tpm
node index.js
# Ctrl+A, D to detach
```

### Disabling Rotation

**Option 1**: Remove autoRotate section

```javascript
// Remove or comment out
// autoRotate: {...}
```

**Option 2**: Set to continuous flipping

```javascript
autoRotate: {
    "Account1": "r0:24f0"  // No rest, flip 24h
}
```

## Best Practices

### 1. Start Conservative

Begin with more rest time:
```javascript
"r6:4f0"  // Rest 6h, flip 4h
```

Gradually increase flipping time as comfortable.

### 2. Vary Schedules

Don't use the same schedule for all accounts:
```javascript
autoRotate: {
    "Account1": "r2:4f2",
    "Account2": "r1:5f2",
    "Account3": "r3:3f2"
}
```

### 3. Consider Time Zones

Plan schedules around peak flipping times:
- Peak Hypixel hours: 3-8 PM EST
- Off-peak: Late night/early morning

### 4. Monitor Results

Track:
- Profits per account
- Flips per hour
- Schedule effectiveness
- Any issues

### 5. Adjust Based on Data

Optimize schedules based on:
- Which time periods are most profitable
- When you get most flips
- Account safety
- Market conditions

## Advanced Rotation Strategies

### Strategy 1: Rolling Coverage

Three accounts, always one active:

```javascript
autoRotate: {
    "Account1": "r0:8f0",   // Flip 0-8h
    "Account2": "r8:8f0",   // Flip 8-16h (rest during 0-8h)
    "Account3": "r16:8f0"   // Flip 16-24h (rest during 0-16h)
}
```

**Result**: 24/7 coverage with three accounts

### Strategy 2: Peak Hours Focus

Focus on profitable hours:

```javascript
autoRotate: {
    "Account1": "r18:6f0"  // Rest 18h, flip 6h during peak
}
```

**Schedule**: Only flip during 3-9 PM EST (peak hours)

### Strategy 3: Randomized (Manual)

Change schedule regularly to avoid patterns:
- Week 1: "r2:4f2"
- Week 2: "r1:5f1"
- Week 3: "r3:3f3"

### Strategy 4: Main + Backup

```javascript
autoRotate: {
    "MainAccount": "r0:18f0",  // Flip most of the day
    "BackupAccount": "r18:6f0" // Flip when main rests
}
```

**Result**: Main account does heavy lifting, backup covers gaps

## Troubleshooting

### Rotation Not Working

**Symptoms:**
- Bot doesn't go offline/online as scheduled
- No rotation notifications

**Solutions:**
1. Check config.js syntax
2. Verify autoRotate format
3. Restart TPM
4. Check console for errors

### Wrong Rotation Times

**Symptoms:**
- Bot rotating at unexpected times
- Schedule doesn't match config

**Solutions:**
1. Double-check rotation string format
2. Verify account name spelling
3. Check system time on VPS
4. Review Discord notifications

### Account Not Starting After Rest

**Symptoms:**
- Bot doesn't come back online after rest period
- Stuck in rest mode

**Solutions:**
1. Check TPM process is running
2. Restart TPM manually
3. Review error logs
4. Check VPS resources

### Discord Notifications Not Sending

**Symptoms:**
- No rotation notifications in Discord

**Solutions:**
1. Verify webhook URL is correct
2. Check webhook permissions
3. Test webhook manually
4. Review TPM console output

## Example Complete Config with Rotation

```javascript
module.exports = {
    // Three accounts with different schedules
    igns: ["MainFlip", "AltFlip1", "AltFlip2"],

    discordID: "backend-id",
    webhook: "discord-webhook-url",
    session: "coflnet-password",

    // Auto-rotation schedules
    autoRotate: {
        "MainFlip": "r1:6f1",   // Aggressive schedule
        "AltFlip1": "r2:4f2",   // Balanced schedule
        "AltFlip2": "r3:3f2"    // Conservative schedule
    },

    // Other settings
    delay: 250,
    bedSpam: true,
    relist: true,

    percentOfTarget: {
        "0-10000000": 0.95,
        "10000000-999999999": 0.97
    }
}
```

## Visual Schedule Examples

### Example: "r2:4f2"

```
Hour:  0  1  2  3  4  5  6  7  8
Mode:  R  R  F  F  F  F  V  V  (repeat)

R = Rest
F = Flip
V = Friend Visit
```

Total cycle: 8 hours
- 25% rest
- 50% flipping
- 25% visiting

### Example: "r1:6f1"

```
Hour:  0  1  2  3  4  5  6  7  8
Mode:  R  F  F  F  F  F  F  V  (repeat)

R = Rest
F = Flip
V = Friend Visit
```

Total cycle: 8 hours
- 12.5% rest
- 75% flipping
- 12.5% visiting

## Next Steps

- Configure [Multiple Accounts](multiple-accounts.md) with rotation
- Set up [VPS](vps-setup.md) for 24/7 operation
- Review [Config Structure](../configuration/config-structure.md)
- Monitor using [Troubleshooting Guide](../troubleshooting/common-issues.md)

## Summary

**Auto-Rotation Checklist:**
- [ ] Understand rotation format (r:f:f)
- [ ] Plan your schedule
- [ ] Configure autoRotate in config.js
- [ ] Test with one account first
- [ ] Monitor Discord notifications
- [ ] Track effectiveness
- [ ] Adjust based on results

Auto-rotation helps maintain natural account behavior while maximizing your flipping efficiency!
