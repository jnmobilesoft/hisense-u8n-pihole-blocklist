# hisense-u8n-pihole-blocklist
Pi-hole blocklist for Hisense Smart U8N TVs - blocks 100% telemetry / services /streaming except LAN

# Hisense Smart TV Pi-hole Blocklist 

An aggressive, comprehensive blocklist for Hisense U8N Smart TVs to eliminate excessive telemetry and tracking while maintaining minimal TV functionality. Turns your TV back into a monitor that only streams LAN traffic. 

## The Problem

Hisense Smart U8N TVs generate an enormous amount of telemetry requests, more so if they are partially blocked - **up to 25,000 blocked requests per day** during just a few hours of TV usage. That's approximately **1.7 requests per second** while the TV is powered on.

The TV attempts to connect to various tracking and telemetry domains, and when blocked, it tries alternative domains (often at 2am when you're asleep). This creates:
- Network congestion
- Router log spam  
- Privacy concerns
- Performance issues

## The Solution

This blocklist was developed over several weeks by monitoring a Hisense U8N TV's network behavior and identifying all the domains it attempts to contact for telemetry purposes. The list blocks streaming, tracking and telemetry while preserving:

✅ **LAN/local network access**  

❌ **Telemetry and tracking requests**  
❌ **Usage analytics**  
❌ **Advertisement profiling**  
❌ **Unnecessary cloud connections**  

## Tested Hardware

- **Primary:** Hisense U8N TV
- **Likely compatible:** Other Hisense Smart TV models (U7, U6, A6, etc.)
- **Feedback welcome:** Please report compatibility with other models

## Installation

### 1: Direct Import to Pi-hole 

1. Log into your Pi-hole admin interface
2. Go to **Group Management** → **Adlists**
3. Add this URL to import the blocklist:
   ```
   https://raw.githubusercontent.com/jnmobilesoft/hisense-pihole-blocklist/main/domains.txt
   ```
4. Go to **Tools** → **Update Gravity**
5. Click **Update** to apply the new blocklist

### Method 2: Device-Specific Blocking (Advanced)

For more granular control, you can apply this blocklist only to your Hisense TV:

1. **Create a group:**
   - Group Management → Groups → Add group "Hisense TVs"

2. **Add your TV as a client:**
   - Group Management → Clients → Add your TV's IP address
   - Assign it to the "Hisense TVs" group

3. **Import blocklist and assign to group:**
   - Add the blocklist URL as above
   - In Adlists, assign the new list to "Hisense TVs" group only

4.  **NB!!! For each domain in the blocklist, change the group to Hisense only ie. tick Hisense and Untick default for each one.
   - Youtube and Google are INCLUDED in this list, so they will be blocked unless you remove them or change the group.

This method blocks domains only for your Hisense TV while leaving other devices unaffected.

## Results

**Before blocklist:**
- 25,000+ requests per day from TV
- Constant network chatter
- 2am "stealth" connection attempts
- Router logs filled with connection attempts

**After blocklist:**
- 25,000+ requests **blocked** per day
- Quiet network operation
- TV functionality completely preserved
- Clean router logs

## Domain Categories Blocked

The blocklist targets these types of connections:
- Netflix telemetry endpoints
- Amazon Video tracking
- Hisense cloud services
- Smart hub analytics
- Usage statistics collection
- Advertisement profiling
- NTP servers (when used for tracking)

## Contributing

Found additional domains your Hisense TV is trying to reach? Please:

1. Fork this repository
2. Add the domain(s) to `domains.txt`
3. Test to ensure TV functionality isn't broken
4. Submit a pull request with:
   - Domain(s) added
   - Your TV model
   - What functionality you tested

## Compatibility Reports

| TV Model | Status | Reported By | Date |
|----------|--------|-------------|------|
| Hisense U8N | ✅ Fully Compatible | Original Author | 2025-06 |
| Hisense U7 | ❓ Needs Testing | - | - |
| Hisense U6 | ❓ Needs Testing | - | - |

## Troubleshooting

**TV not connecting to streaming services:**
- Check if you accidentally blocked legitimate streaming domains
- Temporarily disable the blocklist to test
- Report the issue with your TV model

**TV showing network errors:**
- This is normal - the TV is trying to send telemetry and failing
- All core TV functions should still work
- Error messages can usually be dismissed

**Need to update TV firmware:**
- Temporarily disable the blocklist
- Perform the update
- Re-enable the blocklist

## Technical Details

- **Total domains blocked:** 46
- **Development time:** Several weeks of monitoring
- **Detection method:** Pi-hole query logs analysis
- **Testing period:** Multiple weeks of daily usage
- **False positives:** Zero (all essential functions preserved)

## License

This blocklist is provided under the MIT License. Feel free to use, modify, and distribute.

## Disclaimer

This blocklist is provided as-is. While extensively tested, use at your own risk. Always test thoroughly with your specific TV model and usage patterns.

---

**Star this repository if it helped reduce your Hisense TV's network chatter!** ⭐
