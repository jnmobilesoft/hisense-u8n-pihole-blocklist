# Contributing to Hisense Pi-hole Blocklist

Thank you for helping improve this blocklist! Your contributions help the entire Pi-hole community deal with chatty smart TVs.

## How to Contribute

### 🆕 New Domains Discovery

If you find domains that your Hisense TV is trying to reach that aren't in our blocklist:

1. **Monitor your Pi-hole logs** for 24-48 hours
2. **Identify suspicious domains** from your TV's IP address
3. **Test blocking** - make sure TV functionality isn't broken
4. **Submit the domains** via the methods below

### 📝 Reporting New Domains

**Quick Method:**
- Open a GitHub Issue with:
  - Your TV model
  - The new domain(s) found
  - What testing you've done

**Contribution Method:**
1. Fork this repository
2. Add the domain(s) to `domains.txt`
3. Test thoroughly (see testing guide below)
4. Submit a pull request

### 🧪 Testing Guidelines

Before submitting new domains, please test:

**Essential TV Functions:**
- [ ] Power on/off works
- [ ] Channel changing works
- [ ] Volume control works
- [ ] TV settings accessible
- [ ] Input switching works

**Streaming Services:**
- [ ] Netflix opens and plays content
- [ ] YouTube works
- [ ] Amazon Prime Video works
- [ ] Other streaming apps you use

**Network Features:**
- [ ] WiFi connection stable
- [ ] Can access local media servers (if used)
- [ ] Screen mirroring works (if used)

### 📋 Domain Submission Format

When submitting new domains, please provide:

```
**TV Model:** Hisense U8N
**Domain(s):** example.tracking.hisense.com
**Discovery Method:** Pi-hole query logs
**Testing Done:** 
- Blocked for 24 hours
- All streaming services tested
- No functionality issues found
**Notes:** Domain attempts connection every 30 seconds
```

### 🔍 Domain Research Tips

**Finding new domains:**
1. **Pi-hole Query Log** - Check your TV's IP for denied/allowed requests
2. **Network monitoring** - Use tools like Wireshark on your network
3. **Router logs** - Check for connection attempts
4. **2am monitoring** - Many TVs try "stealth" connections at night

**Identifying telemetry vs. legitimate:**
- **Telemetry domains** usually contain: analytics, tracking, telemetry, stats
- **Legitimate domains** usually needed for: updates, streaming, core functions
- **When in doubt** - test blocking for 24-48 hours

### 🚫 What NOT to Block

Please don't submit domains that break:
- Streaming service authentication (when needed)
- Software updates (when needed)
- Core TV functionality (when needed)
- Local network features

### 🏷️ TV Model Compatibility

Help us track compatibility:

**If you test on a new TV model:**
- Report whether the blocklist works
- Note any domains that need to be added/removed
- Update the compatibility table in README.md

**Current compatibility:**
- ✅ Hisense U8N - Fully tested
- ❓ Other models - Need community testing

### 📊 Data Collection Ethics

When monitoring your TV:
- Only collect domain names and connection patterns
- Don't share personal viewing data
- Focus on technical telemetry, not content

### 🔧 Pull Request Guidelines

**For domain additions:**
1. Add domains to `domains.txt` (one per line)
2. Include comment with discovery date
3. Update README.md if needed
4. Test thoroughly before submitting

**PR Title Format:**
- `Add domains: [TV Model] - [Brief description]`
- Example: `Add domains: U7 Model - Netflix tracking endpoints`

**PR Description should include:**
- TV model tested
- How domains were discovered
- Testing performed
- Any special notes

### 🐛 Bug Reports

**If the blocklist breaks your TV:**
1. *** It is supposed to :)
2. **Immediate fix:** Disable the blocklist temporarily
3. **Report:** Open a GitHub issue with:
   - Your TV model
   - What functionality is broken
   - Which domain(s) might be causing the issue
   - Your Pi-hole version

### 📞 Community Support

**Help other users:**
- Answer questions in GitHub Issues
- Share your TV model compatibility results
- Help troubleshoot installation problems

### 🎯 Goals

Our blocklist aims to:
- Block maximum telemetry/tracking
- Support all Hisense TV models
- Maintain clean, documented code

### 📜 Code of Conduct

- Be respectful and helpful
- Focus on technical solutions
- Share knowledge openly
- Help newcomers to Pi-hole

---

**Thank you for contributing!** Every domain you discover and test helps make this blocklist better for everyone. 🎉
