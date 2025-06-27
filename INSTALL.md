# Installation Guide

## Prerequisites

- Pi-hole running and accessible
- Admin access to Pi-hole web interface
- Your Hisense TV's IP address (optional for device-specific blocking, assume IP is fixed)

## Option 1: Network-Wide Blocking (Simple)

This method blocks Hisense telemetry domains for all devices on your network.

### Steps:

1. **Access Pi-hole Admin Interface**
   - Open your browser and go to your Pi-hole admin panel
   - Usually: `http://[PI-HOLE-IP]/admin/`

2. **Add the Blocklist**
   - Navigate to **Group Management** → **Adlists**
   - Click **Add a new adlist**
   - Enter this URL:
     ```
     https://raw.githubusercontent.com/jnmobilesoft/hisense-pihole-blocklist/main/domains.txt
     ```
   - Add a comment: "Hisense TV Telemetry Blocklist"
   - Click **Add**

3. **Update Gravity**
   - Go to **Tools** → **Update Gravity**
   - Click **Update**
   - Wait for the process to complete

4. **Verify Installation**
   - Go to **Group Management** → **Adlists**
   - Confirm your new list shows "Last Modified" as recent
   - Check that it shows the correct number of domains

## Option 2: Device-Specific Blocking (Advanced)

This method applies the blocklist only to your Hisense TV, leaving other devices unaffected.

### Steps:

1. **Find Your TV's IP Address**
   ```bash
   # Check your router's DHCP client list, or:
   nmap -sn 192.168.1.0/24  # Adjust subnet as needed
   ```

2. **Create a Device Group**
   - Go to **Group Management** → **Groups**
   - Click **Add a new group**
   - Name: "Hisense TVs"
   - Description: "Hisense Smart TVs with telemetry blocking"
   - Click **Add**

3. **Add Your TV as a Client**
   - Go to **Group Management** → **Clients**
   - Click **Add a new client**
   - Enter your TV's IP address
   - Comment: "Hisense U8N TV" (or your model)
   - Assign to group: "Hisense TVs"
   - Click **Add**

4. **Add the Blocklist**
   - Go to **Group Management** → **Adlists**
   - Click **Add a new adlist**
   - Enter the URL:
     ```
     https://raw.githubusercontent.com/jnmobilesoft/hisense-pihole-blocklist/main/domains.txt
     ```
   - Comment: "Hisense Telemetry Blocklist"
   - Assign to groups: Select **only** "Hisense TVs"
   - Click **Add**

5. **Update Gravity**
   - Go to **Tools** → **Update Gravity**
   - Click **Update**

## Verification

### Check if Blocking is Working:

1. **Monitor Query Logs**
   - Go to **Query Log over Time** or **Query Log**
   - Look for blocked queries from your TV's IP address
   - You should see red "blocked" entries for Hisense domains

2. **Test TV Functionality**
   - Power on your Hisense TV
   - Test streaming services (Netflix, YouTube, Amazon Prime), they should FAIL
   - Verify most TV functions no longer work normally
   - Browse shared content on a LAN should work

3. **Check Blocking Statistics**
   - Go to Pi-hole **Dashboard**
   - You should see an increase in blocked queries
   - Your TV should appear in "Top Clients" with many blocked requests

### Expected Results:

- **Blocked queries:** Significant increase (potentially 1000s per day)
- **TV functionality:** 100% preserved
- **Network performance:** Improved (less chatter)
- **Streaming services:** LAN Access only

## Troubleshooting

### TV Shows Network Errors
- **Normal behavior** - TV is trying to send telemetry and failing
- All streaming and TV functions will NOT work
- Error messages can usually be dismissed
- Unblock as per requirements
- LAN access is not affected

## Maintenance

### Regular Updates
The blocklist may be updated as new telemetry domains are discovered.

To update:
1. Go to **Group Management** → **Adlists**
2. Click **Update Gravity** 
3. The latest version will be automatically downloaded

### Monitoring
- Check Pi-hole's **Query Log** periodically
- Look for new domains your TV might be trying to reach
- Report new discoveries to help improve the blocklist

## Uninstalling

To remove the blocklist:

1. **Remove from Adlists**
   - Group Management → Adlists
   - Find the Hisense blocklist
   - Click the red trash icon to delete

2. **Update Gravity**
   - Tools → Update Gravity
   - Click Update

3. **Clean up Groups/Clients** (if using device-specific blocking)
   - Remove the TV from Groups → Clients
   - Delete the "Hisense TVs" group if no longer needed

Your TV will resume its normal telemetry behavior after removal.
