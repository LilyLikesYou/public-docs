# Config Structure

TPM configuration file: `config.json5`

## Basic Example

```javascript
{
    igns: ["YourAccount"],
    webhook: "https://discord.com/api/webhooks/...",
    session: "your-coflnet-password",

    delay: 250,
    clickDelay: 100,
    bedSpam: true,

    percentOfTarget: { /* TODO */ },
    listHours: { /* TODO */ },

    skip: { /* TODO */ },
    doNotRelist: { /* TODO */ }
}
```

## Core Settings

**Accounts:**
```javascript
igns: ["Account1", "Account2"]
```

**Discord:**
```javascript
webhook: "https://discord.com/api/webhooks/..."
webhookFormat: "{itemName} bought for {price}" // Optional
sendAllFlips: "webhook-url" // Optional: test webhook
```

**Auth:**
```javascript
session: "your-coflnet-password"
discordID: "backend-id" // Provided by TPM
```

## Timing

```javascript
delay: 250              // ms between actions (200-300 recommended)
clickDelay: 100         // bed spam click interval
waittime: 15            // bed spam timing
bedSpam: true           // enable bed spam
```

## Flipping

**Price Markup:**
```javascript
percentOfTarget: {
    /* TODO: fill with actual structure */
}
```

**Listing Duration:**
```javascript
listHours: {
    /* TODO: fill with actual structure */
}
```

**Cookie Settings:**
```javascript
useCookie: true
autoCookie: "1d"        // y/d/h units
```

**Pricing:**
```javascript
roundTo: 0              // 0 = no rounding, 4 = round to 10k
relist: true
```

## Filters

**Auto-skip (HIGHER BAN RISK):**
```javascript
skip: {
    profitThreshold: 5000000,    // Auto-buy if profit > 5m
    finderTypes: ["SNIPER", "USER"],
    cosmetics: true,
    lowProfit: 1000000           // Skip if < 1m
}
```

**Relist Exclusions:**
```javascript
doNotRelist: {
    items: ["Item Name"],
    minProfit: 1000000,
    tags: ["TAG_NAME"],
    finders: ["FINDER_TYPE"]
}
```

**Other:**
```javascript
angryCoopPrevention: true       // Block coop auctions
blockUselessMessages: true      // Reduce console spam
pingOnUpdate: false             // Update notifications
```

## Advanced

**Account Rotation:**
```javascript
autoRotate: {
    "Account1": "r2:3f1",    // rest 2h, flip 3h, friend visit 1h
    "Account2": "r1:2f2"
}
```
Format: `r[hours]:f[hours]f[hours]`

**Friend Island:**
```javascript
visitFriend: "username"
```

---

**See also:** [Filters & Settings](filters-and-settings.md) | [Cofl Commands](cofl-commands.md)
