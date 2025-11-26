# Multiple Accounts

Run TPM with multiple Minecraft accounts simultaneously.

## Resource Requirements

**RAM:**
- 1 account: 1GB
- 2-3 accounts: 2GB
- 4-5 accounts: 4GB
- 6+ accounts: 8GB or multiple VPS

**CPU:**
- 1 vCPU for 1-2 accounts
- 2 vCPU for 3+ accounts

## Configuration

**Basic setup:**
```javascript
{
    igns: ["Account1", "Account2", "Account3"],

    webhook: "main-webhook",
    session: "coflnet-password",

    // Settings apply to all accounts
}
```

**Account-specific rotation:**
```javascript
{
    igns: ["MainAccount", "AltAccount1", "AltAccount2"],

    autoRotate: {
        "MainAccount": "r2:3f1",
        "AltAccount1": "r1:2f2",
        "AltAccount2": "r3:4f1"
    }
}
```

## Strategies

**Same config, different thresholds:**
- All load same config
- Adjust minprofit per account: `/cofl set minprofit 5m`
- Good for different purse sizes

**Different configs:**
- Load different configs per account in-game
- Good for specialization (pets, armor, etc.)

## Monitoring

**Console:**
```bash
# Tmux
tmux new -s tpm
# Ctrl+B, C for new window
# Ctrl+B, W to list windows
```

**Discord:** Use separate webhooks per account for tracking

## Best Practices

1. **Start small:** Begin with 1-2 accounts
2. **Monitor resources:** `free -h`, `top`
3. **Stagger starts:** Don't start all simultaneously
4. **Diversify:** Different thresholds/configs/strategies
5. **Regular checks:** Verify all running, monitor profits

## Troubleshooting

**Out of memory:** `free -h` - reduce accounts or upgrade VPS

**Disconnects:** Check network, reduce accounts, upgrade resources

**Can't track:** Use separate webhooks, descriptive names

---

**See also:** [Auto-Rotation](auto-rotation.md) | [VPS Setup](vps-setup.md)
