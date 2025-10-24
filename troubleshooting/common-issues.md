# Common Issues

Troubleshooting guide for common TPM problems and their solutions.

## Table of Contents

- [Connection Issues](#connection-issues)
- [Bot Not Buying Flips](#bot-not-buying-flips)
- [Authentication Problems](#authentication-problems)
- [Performance Issues](#performance-issues)
- [Config Issues](#config-issues)
- [Webhook/Discord Issues](#webhookdiscord-issues)
- [VPS Issues](#vps-issues)

## Connection Issues

### Bot Won't Connect to Hypixel

**Symptoms:**
- Bot fails to join Hypixel
- Connection timeout errors
- Repeated disconnects

**Solutions:**

1. **Check Minecraft Account**
   ```bash
   # Verify credentials in config.js
   nano config.js
   ```
   - Ensure igns array has correct username/token
   - Verify session password is correct

2. **Check Internet Connection**
   ```bash
   ping hypixel.net
   ```
   - If no response, check VPS network
   - Contact VPS provider if persistent

3. **Hypixel Server Status**
   - Check if Hypixel is down
   - Visit hypixel.net/status
   - Wait and retry if server issues

4. **Rate Limiting**
   - Too many connection attempts
   - Wait 5-10 minutes
   - Increase delay in config

### Bot Disconnects from Coflnet

**Symptoms:**
- "Disconnected from Coflnet" messages
- No flip notifications
- WebSocket errors

**Solutions:**

1. **Check Coflnet Status**
   - Visit sky.coflnet.com
   - Verify service is online
   - Check for maintenance announcements

2. **Verify Session Password**
   ```javascript
   session: "your-correct-coflnet-password"
   ```
   - Must match your Coflnet account password
   - Case-sensitive

3. **Check Subscription**
   - Verify Cofl Premium/Premium+ is active
   - In-game: `/cofl premium`
   - Renew if expired

4. **Restart Bot**
   ```bash
   # Stop and restart TPM
   screen -X -S tpm quit
   screen -S tpm
   node index.js
   ```

### Frequent Disconnects

**Symptoms:**
- Bot disconnects every few minutes
- Unstable connection
- Constant reconnects

**Solutions:**

1. **Check VPS Resources**
   ```bash
   free -h  # Check memory
   top      # Check CPU
   ```
   - Upgrade VPS if resources maxed out

2. **Network Stability**
   ```bash
   ping -c 100 hypixel.net
   ```
   - High packet loss? Contact VPS provider
   - Try different VPS location

3. **Reduce Load**
   - Decrease number of accounts
   - Increase delay setting
   - Close unnecessary processes

## Bot Not Buying Flips

### No Flips Coming In

**Symptoms:**
- Bot connected but no flip notifications
- `/cofl` commands work but no flips
- Long periods with no activity

**Solutions:**

1. **Check Config Loaded**
   ```
   /cofl status
   ```
   - Should show active config name
   - If not, reload: `/cofl loadconfig [name] [name]`

2. **Check Profit Thresholds**
   ```
   /cofl set minprofit 3m
   /cofl set minprofitpercent 4
   ```
   - Thresholds may be too high
   - Lower gradually and monitor

3. **Verify Cofl Subscription**
   ```
   /cofl premium
   ```
   - Must have active Premium or Premium+
   - Renew if expired

4. **Check Blacklist**
   ```
   /cofl blacklist list
   ```
   - May have blacklisted too many items
   - Remove unnecessary items

5. **Market Conditions**
   - Some periods have fewer flips
   - Peak hours: 3-8 PM EST
   - Wait 15-30 minutes

### Bot Ignoring Flips

**Symptoms:**
- Flip notifications appear
- Bot doesn't attempt to buy
- Skips all flips

**Solutions:**

1. **Check Filters**
   ```
   /cofl status
   ```
   - Review active filters
   - May be too restrictive

2. **Enable Auto-Fast**
   ```
   /cofl set autofast true
   ```
   - Enables automatic purchasing

3. **Check Purse**
   - Ensure sufficient coins
   - Bot skips if can't afford

4. **Config Issues**
   - Review skip settings in config.js
   - May have too many skip conditions

### Bot Buys Wrong Items

**Symptoms:**
- Purchases unprofitable items
- Buys items you don't want
- Bad flips

**Solutions:**

1. **Adjust Filters**
   ```
   /cofl set minprofit 5m
   /cofl set minprofitpercent 7
   ```

2. **Blacklist Items**
   ```
   /cofl blacklist add "Item Name"
   ```

3. **Contact Config Provider**
   - Report bad items
   - Request config update
   - See [Handling Bad Flips](../guides/handling-bad-flips.md)

## Authentication Problems

### Invalid Session Error

**Symptoms:**
- "Invalid session" error
- Can't connect to Minecraft
- Authentication fails

**Solutions:**

1. **Verify Account Credentials**
   - Check username/token in config.js
   - For Microsoft accounts, ensure correct email

2. **Token Expired** (if using tokens)
   - Generate new authentication token
   - Update config.js with new token

3. **Account Locked**
   - Check if Minecraft account is locked
   - Verify on minecraft.net
   - Unlock if necessary

### Microsoft Authentication Issues

**Symptoms:**
- Can't authenticate with Microsoft account
- Browser auth required
- Authentication loop

**Solutions:**

1. **Use Correct Format**
   ```javascript
   igns: ["username"]  // Not email if < 16 chars
   ```

2. **Check Account Type**
   - Ensure account migrated to Microsoft
   - Verify can log into minecraft.net

3. **Browser Auth**
   - May need to auth in browser first
   - Follow prompts if they appear

## Performance Issues

### Bot Running Slowly

**Symptoms:**
- Slow responses
- Delayed actions
- Laggy performance

**Solutions:**

1. **Check Resources**
   ```bash
   free -h  # Memory
   top      # CPU
   df -h    # Disk
   ```

2. **Restart Bot**
   ```bash
   screen -X -S tpm quit
   screen -S tpm
   node index.js
   ```

3. **Reduce Load**
   - Fewer accounts
   - Higher delay settings
   - Close other processes

4. **Upgrade VPS**
   - Consider better plan
   - More RAM/CPU

### High Memory Usage

**Symptoms:**
- Memory usage climbing
- Bot crashes with out of memory
- VPS freezing

**Solutions:**

1. **Restart Regularly**
   - Restart bot daily
   - Clears memory leaks

2. **Reduce Accounts**
   - Fewer simultaneous accounts
   - Spread across multiple VPS

3. **Upgrade RAM**
   - Increase VPS plan
   - 2GB+ recommended for multiple accounts

### Missing Flips

**Symptoms:**
- Bot too slow to claim
- Always losing to faster bots
- "Already sold" messages

**Solutions:**

1. **Reduce Delay**
   ```javascript
   delay: 200  // Lower is faster (but risky)
   ```

2. **Enable Bed Spam**
   ```javascript
   bedSpam: true
   clickDelay: 100
   ```

3. **Better VPS Location**
   - Choose VPS closer to Hypixel servers
   - US East recommended

4. **Lower Ping**
   ```bash
   ping hypixel.net
   ```
   - < 50ms excellent
   - 50-100ms good
   - > 100ms may miss flips

## Config Issues

### Config Won't Load

**Symptoms:**
- `/cofl loadconfig` fails
- "Config not found" error
- Config doesn't apply

**Solutions:**

1. **Check Config Name**
   ```
   /cofl loadconfig configname configname
   ```
   - Verify exact spelling
   - Names are case-sensitive

2. **Verify Access**
   - Confirm you purchased/have access
   - Contact config provider

3. **Check Cofl Connection**
   - Must be connected to Coflnet
   - Restart and try again

### Config Syntax Errors

**Symptoms:**
- Bot won't start
- Syntax error messages
- Config.js errors

**Solutions:**

1. **Check Syntax**
   ```bash
   node -c config.js
   ```
   - Shows syntax errors
   - Fix any issues

2. **Common Mistakes**
   - Missing commas
   - Mismatched brackets
   - Incorrect quotes
   - Missing colons

3. **Use Example Config**
   - Start from working example
   - Add settings gradually
   - Test after each change

### Settings Not Applying

**Symptoms:**
- Changed config but no effect
- Old settings still active
- New values ignored

**Solutions:**

1. **Restart Bot**
   - Config changes need restart
   - Stop and start TPM

2. **File Not Saved**
   - Ensure config.js saved
   - Check file modification time

3. **Wrong File**
   - Editing correct config.js?
   - Check file path

## Webhook/Discord Issues

### No Discord Notifications

**Symptoms:**
- Bot running but no Discord messages
- Webhooks not working
- Silent bot

**Solutions:**

1. **Check Webhook URL**
   ```javascript
   webhook: "https://discord.com/api/webhooks/..."
   ```
   - Must be complete URL
   - Test in browser

2. **Verify Permissions**
   - Webhook must have send permissions
   - Check Discord server settings

3. **Test Webhook**
   ```bash
   curl -X POST "webhook-url" \
     -H "Content-Type: application/json" \
     -d '{"content":"Test message"}'
   ```

4. **Check Console**
   - Look for webhook errors in console
   - May show connection issues

### Webhook Format Issues

**Symptoms:**
- Notifications look wrong
- Missing information
- Broken formatting

**Solutions:**

1. **Check Format String**
   ```javascript
   webhookFormat: "Item: {itemName}, Profit: {profit}"
   ```
   - Verify placeholder syntax
   - Use valid placeholders

2. **Review Examples**
   - Check config documentation
   - Use tested formats

## VPS Issues

### Can't Connect to VPS

**Symptoms:**
- SSH connection fails
- "Connection refused"
- Timeout errors

**Solutions:**

1. **Check VPS Status**
   - Log into provider dashboard
   - Verify VPS is running
   - Restart if stopped

2. **Verify IP Address**
   - Correct IP in SSH command
   - Check for IP changes

3. **Firewall Issues**
   - Ensure port 22 open
   - Check UFW status

4. **Use Web Console**
   - Provider's web-based console
   - Alternative access method

### VPS Out of Space

**Symptoms:**
- "No space left on device"
- Can't write files
- Bot crashes

**Solutions:**

1. **Check Disk Usage**
   ```bash
   df -h
   ```

2. **Clear Logs**
   ```bash
   rm -rf ~/tpm/logs/*.log
   ```

3. **Clear Cache**
   ```bash
   sudo apt clean
   ```

4. **Upgrade Storage**
   - Increase VPS disk size
   - Or move to bigger plan

## General Troubleshooting Steps

### Step 1: Check Basics

- Bot process running?
- Config.js correct?
- Internet working?
- All services up?

### Step 2: Review Logs

```bash
# Screen logs
screen -r tpm

# PM2 logs
pm2 logs tpm

# System logs
journalctl -xe
```

### Step 3: Restart Services

```bash
# Restart TPM
screen -X -S tpm quit
screen -S tpm
node index.js

# Restart VPS (if needed)
sudo reboot
```

### Step 4: Test Components

- Test Minecraft connection
- Test Coflnet connection
- Test Discord webhooks
- Test config loading

### Step 5: Get Help

- Check documentation
- Ask in TPM Discord
- Contact config provider
- Open support ticket

## Error Messages

### Common Error Messages and Solutions

| Error | Cause | Solution |
|-------|-------|----------|
| "ECONNREFUSED" | Can't connect to server | Check internet, server status |
| "Invalid credentials" | Wrong username/password | Verify config.js credentials |
| "Out of memory" | Insufficient RAM | Restart bot, upgrade VPS |
| "Config not found" | Wrong config name | Check spelling, verify access |
| "Session invalid" | Cofl session wrong | Update session password |
| "Rate limited" | Too many requests | Wait, increase delay |
| "Webhook failed" | Bad webhook URL | Verify webhook URL |

## Prevention Tips

### 1. Regular Maintenance

- Restart bot daily
- Update system weekly
- Monitor resources
- Check logs regularly

### 2. Backups

```bash
# Backup config
cp config.js config.backup.js

# Backup to local machine
scp user@vps:~/tpm/config.js ./
```

### 3. Monitoring

- Set up monitoring
- Check Discord notifications
- Review performance
- Track metrics

### 4. Stay Updated

- Update TPM when available
- Update system packages
- Update configs
- Follow announcements

## Getting More Help

### Documentation

- [Installation Guide](../getting-started/installation.md)
- [Config Structure](../configuration/config-structure.md)
- [VPS Setup](../advanced/vps-setup.md)

### Support Channels

- TPM Discord server
- Config provider support
- VPS provider support
- Community forums

### Before Asking for Help

Provide:
1. Error messages (exact text)
2. What you were doing
3. Config details (remove sensitive info)
4. System info (VPS specs, OS)
5. When it started
6. What you've tried

## Quick Fixes Checklist

When something goes wrong, try these in order:

- [ ] Check if bot process is running
- [ ] Review console/logs for errors
- [ ] Verify config.js syntax
- [ ] Check internet connection
- [ ] Restart TPM
- [ ] Check Coflnet status
- [ ] Verify Hypixel status
- [ ] Check VPS resources
- [ ] Review recent changes
- [ ] Test with minimal config
- [ ] Ask for help if stuck

## Summary

Most issues can be resolved by:
1. Checking logs
2. Verifying configuration
3. Restarting services
4. Ensuring resources are sufficient
5. Following error messages

If stuck, don't hesitate to ask for help in the TPM Discord or from your config provider!
