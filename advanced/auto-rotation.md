# Auto-Rotation

Schedule account on/off times.

## When to Use

- Don't want 24/7 running
- Rotate accounts through time periods
- Multiple accounts with different strategies
- Minimize detection risk

## Configuration

**Basic syntax:**
```javascript
{
    igns: ["Account1", "Account2"],

    autoRotate: {
        "Account1": "r2:3f1",
        "Account2": "r1:4f0"
    }
}
```

**Format:** `"r[hours]:f[hours]f[hours]"`
- `r` = Rest (offline)
- `f` = Flip (active)
- Second `f` = Friend visit (optional)

**Examples:**
```javascript
"r2:3f1"   // Rest 2h, flip 3h, friend 1h
"r1:4f0"   // Rest 1h, flip 4h, no friend
"r0:6f2"   // No rest, flip 6h, friend 2h
"r4:4f0"   // Rest 4h, flip 4h (50% uptime)
```

## Examples

**Conservative:**
```javascript
autoRotate: {
    "MainAccount": "r4:4f0"  // 8h cycle, 50% uptime
}
```

**Aggressive:**
```javascript
autoRotate: {
    "Account1": "r1:6f1"  // 8h cycle, 75% flipping
}
```

**Staggered multi-account:**
```javascript
autoRotate: {
    "Account1": "r2:4f2",
    "Account2": "r1:5f2",
    "Account3": "r3:3f2"
}
```

**24/7 coverage (3 accounts):**
```javascript
autoRotate: {
    "Account1": "r0:8f0",   // Flip 0-8h
    "Account2": "r8:8f0",   // Flip 8-16h
    "Account3": "r16:8f0"   // Flip 16-24h
}
```

## Schedule Visualization

**"r2:4f2" = 8h cycle:**
```
Hour:  0  1  2  3  4  5  6  7
Mode:  R  R  F  F  F  F  V  V
```
R = Rest (25%), F = Flip (50%), V = Friend visit (25%)

## Discord Notifications

TPM sends notifications when rotating:
```
[Account] is starting up
Next rotation in: [time]

[Account] going offline for [duration]
Will return at: [time]
```

## Adjusting Rotation

1. Stop TPM
2. Edit `config.json5`
3. Update `autoRotate`
4. Restart TPM

**Disable rotation:**
```javascript
// Remove autoRotate or:
autoRotate: {
    "Account1": "r0:24f0"  // Continuous
}
```

## Best Practices

1. **Start conservative:** `"r6:4f0"` then increase
2. **Vary schedules:** Different per account
3. **Peak hours:** 3-8 PM EST most profitable
4. **Change patterns:** Rotate schedules weekly

## Troubleshooting

**Not working:** Check config syntax, restart TPM

**Wrong times:** Verify format, check VPS system time

**No notifications:** Verify webhook URL, check permissions

---

**See also:** [Multiple Accounts](multiple-accounts.md) | [VPS Setup](vps-setup.md)
