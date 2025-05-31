# Social/Online/Time Configuration

![FiveM Pause Menu Script](https://uzstore.gitbook.io/~gitbook/image?url=https%3A%2F%2F2351540620-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FcRCyehul5IZdMTnshKMH%252Fuploads%252FQHWyTKMByFZ4ooxgogs5%252FGroup%252037792.png%3Falt%3Dmedia%26token%3D576db47e-23ac-4a82-858b-411303921659&width=768&dpr=4&quality=100&sign=a678ec05&sv=2)

## Overview

Configure social media links, server online player count, and time format settings. This section allows you to connect your community through social media links and display real-time server information to enhance player engagement.

{% hint style="info" %}
**Flexible Configuration:** You can add 0-3 social media links and customize how time and player count are displayed.
{% endhint %}

---

## 1. Configuring Social Media Links and Server Settings

In `Customize.lua`, you can configure social media links and server settings:

```lua
Use24HourFormat = false,  -- true: 24-hour format, false: 12-hour format
ServerMaxOnline = 1200,   -- Maximum number of players that can be online

Socials = {  -- min: 0 - max: 3
    { icon = 'youtube.svg', link = 'https://www.youtube.com/@UZStoree' },
    { icon = 'discord.svg', link = 'https://discord.gg/uzstore' },
    { icon = 'store.svg', link = 'https://uzstore.tebex.io/' }
}
```

### Configuration Parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| `Use24HourFormat` | Boolean | `true` for 24-hour format, `false` for 12-hour format |
| `ServerMaxOnline` | Number | Maximum number of players allowed on the server |
| `Socials` | Array | List of social media links (0-3 items) |

### Social Media Object Structure

| Parameter | Type | Description |
|-----------|------|-------------|
| `icon` | String | Icon filename (stored in `resources/images/Socials`) |
| `link` | String | URL to open when the social media button is clicked |

{% hint style="warning" %}
**Limits:** You can add a minimum of 0 and maximum of 3 social media links.
{% endhint %}

---

## 2. Time Format Configuration

### 24-Hour Format Example
```lua
Use24HourFormat = true  -- Display: 14:30, 09:15, 23:45
```

### 12-Hour Format Example  
```lua
Use24HourFormat = false  -- Display: 2:30 PM, 9:15 AM, 11:45 PM
```

{% tabs %}
{% tab title="24-Hour Format" %}
**Format:** HH:MM
**Examples:**
- 09:30 (9:30 AM)
- 14:15 (2:15 PM)
- 23:45 (11:45 PM)
- 00:00 (Midnight)
{% endtab %}

{% tab title="12-Hour Format" %}
**Format:** H:MM AM/PM
**Examples:**
- 9:30 AM
- 2:15 PM
- 11:45 PM
- 12:00 AM (Midnight)
{% endtab %}
{% endtabs %}

---

## 3. Server Online Player Settings

### Maximum Online Players

Set the `ServerMaxOnline` value to match your server's actual player limit. This helps players understand the server capacity and current load.

```lua
ServerMaxOnline = 1200  -- Supports up to 1200 players
```

### Display Examples

The player count will be displayed as:
- **Current/Maximum:** "45/1200 Players Online"
- **Percentage:** Automatically calculated based on current vs maximum

{% hint style="success" %}
**Tip:** Set `ServerMaxOnline` to your actual server limit for accurate capacity display.
{% endhint %}

---

## 4. Social Media Configuration

### Icon Requirements

- **Format:** SVG (recommended) or PNG
- **Size:** 32x32 pixels minimum
- **Location:** `resources/images/Socials/`
- **Style:** Simple, recognizable social media icons

### Available Default Icons

| Icon Name | Platform | Purpose |
|-----------|----------|---------|
| `youtube.svg` | YouTube | Video content, tutorials |
| `discord.svg` | Discord | Community chat, support |
| `store.svg` | Store | Server shop, donations |
| `twitter.svg` | Twitter/X | News, updates |
| `instagram.svg` | Instagram | Screenshots, community |
| `website.svg` | Website | Official server website |

### Example Configurations

{% tabs %}
{% tab title="Gaming Community" %}
```lua
Socials = {
    { icon = 'discord.svg', link = 'https://discord.gg/yourserver' },
    { icon = 'youtube.svg', link = 'https://youtube.com/@yourchannel' },
    { icon = 'store.svg', link = 'https://yourstore.tebex.io/' }
}
```
{% endtab %}

{% tab title="Roleplay Server" %}
```lua
Socials = {
    { icon = 'discord.svg', link = 'https://discord.gg/rp-server' },
    { icon = 'website.svg', link = 'https://yourwebsite.com' },
    { icon = 'store.svg', link = 'https://store.yourserver.com' }
}
```
{% endtab %}

{% tab title="Minimal Setup" %}
```lua
Socials = {
    { icon = 'discord.svg', link = 'https://discord.gg/minimal' }
}
```
{% endtab %}
{% endtabs %}

---

## 5. Testing Your Configuration

After making all the adjustments, verify in-game that the information is displayed correctly.

### Testing Checklist

✅ **Time Format:** Check if time displays in correct format
✅ **Player Count:** Verify current/max players show accurately  
✅ **Social Links:** Test each social media button opens correct URL
✅ **Icons:** Confirm all icons display properly
✅ **Responsive Design:** Check layout works on different resolutions

{% hint style="info" %}
**Browser Testing:** Social media links will open in the player's default browser, so ensure URLs are correct and accessible.
{% endhint %}

### Troubleshooting Common Issues

| Issue | Solution |
|-------|----------|
| Icons not showing | Check file paths and ensure icons exist in `resources/images/Socials/` |
| Links not working | Verify URLs are complete with `https://` |
| Time format wrong | Double-check `Use24HourFormat` boolean value |
| Player count incorrect | Ensure `ServerMaxOnline` matches server settings |

---

### Related Pages

{% content-ref url="custom-pages.md" %}
[custom-pages.md](custom-pages.md)
{% endcontent-ref %}

{% content-ref url="player-details.md" %}
[player-details.md](player-details.md)
{% endcontent-ref %} 