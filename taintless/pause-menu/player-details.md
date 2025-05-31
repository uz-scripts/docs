# Player Details

![FiveM Pause Menu Script](https://uzstore.gitbook.io/~gitbook/image?url=https%3A%2F%2F2351540620-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FcRCyehul5IZdMTnshKMH%252Fuploads%252FjB66WZEt3Q3vSJ8ZzJqT%252FGroup%252037790.png%3Falt%3Dmedia%26token%3D5b7c5c18-2d0e-49c2-b347-6d9f278be7d5&width=768&dpr=4&quality=100&sign=ca76ec6c&sv=2)

## Overview

Player details allow you to display custom information about players in the pause menu. This feature is highly customizable and can show various player statistics like money, bank balance, job information, or any other server-specific data.

{% hint style="info" %}
**Customizable:** You can display any player information by creating custom functions and linking them to the player details system.
{% endhint %}

---

## 1. Defining Player Details in Customize.lua

Edit the `PlayerDetails` section in the `Customize.lua` file to adjust how you want to display player details.

```lua
PlayerDetails = {
    icon = 'money.svg',  -- icon file path (resources/images/PlayerDetails)
    header = 'Money',    -- header (e.g., "Money")
    event = 'GetMoney'   -- event to be called (defined in server/function.lua)
}
```

### Configuration Parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| `icon` | String | Icon filename (stored in `resources/images/PlayerDetails`) |
| `header` | String | Display name/title for this detail |
| `event` | String | Function name in `server/function.lua` to fetch the data |

{% hint style="warning" %}
**Important:** The event name in `PlayerDetails` must match the function name in `server/function.lua` exactly.
{% endhint %}

---

## 2. Defining the Function in server/function.lua

Add the relevant function to the `server/function.lua` file to define how to obtain player details on the server side.

```lua
GetMoney = function(Player, data)
    return '$ ' .. Player?.PlayerData?.money?.cash
end
```

### Function Parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| `Player` | Object | Player object containing all player data |
| `data` | Object | Content of `PlayerDetails` (icon, header, event) |

### Example Functions

{% tabs %}
{% tab title="Money Example" %}
```lua
GetMoney = function(Player, data)
    return '$ ' .. Player?.PlayerData?.money?.cash
end
```
{% endtab %}

{% tab title="Bank Example" %}
```lua
GetBank = function(Player, data)
    return '$ ' .. Player?.PlayerData?.money?.bank
end
```
{% endtab %}

{% tab title="Job Example" %}
```lua
GetJob = function(Player, data)
    return Player?.PlayerData?.job?.label or 'Unemployed'
end
```
{% endtab %}

{% tab title="Level Example" %}
```lua
GetLevel = function(Player, data)
    return 'Level ' .. (Player?.PlayerData?.metadata?.level or 1)
end
```
{% endtab %}
{% endtabs %}

---

## 3. Multiple Player Details

You can display multiple player details by creating an array of detail objects:

```lua
PlayerDetails = {
    {
        icon = 'money.svg',
        header = 'Cash',
        event = 'GetMoney'
    },
    {
        icon = 'bank.svg',
        header = 'Bank',
        event = 'GetBank'
    },
    {
        icon = 'job.svg',
        header = 'Job',
        event = 'GetJob'
    }
}
```

{% hint style="success" %}
**Pro Tip:** You can add as many player details as needed. Each will be displayed as a separate section in the pause menu.
{% endhint %}

---

## 4. Icon Customization

### Icon Requirements

- **Format:** SVG (recommended) or PNG
- **Size:** 24x24 pixels or larger
- **Location:** `resources/images/PlayerDetails/`
- **Style:** Simple, clean icons work best

### Available Default Icons

| Icon Name | Purpose |
|-----------|---------|
| `money.svg` | Cash/Money display |
| `bank.svg` | Bank balance |
| `job.svg` | Job information |
| `level.svg` | Player level |
| `health.svg` | Health status |

---

## 5. Testing Your Customizations

After making all the adjustments, verify in-game that the information is displayed correctly.

### Troubleshooting Steps

1. **Check Console:** Look for any Lua errors
2. **Verify Function Names:** Ensure event names match function names
3. **Test Data:** Make sure the player data structure is correct
4. **Icon Paths:** Verify icon files exist in the correct directory

{% hint style="info" %}
**Debugging Tip:** Use `print()` statements in your functions to debug data values during testing.
{% endhint %}

### Example Debugging Function

```lua
GetMoney = function(Player, data)
    print('Player Data:', json.encode(Player?.PlayerData))
    local cash = Player?.PlayerData?.money?.cash or 0
    print('Cash Amount:', cash)
    return '$ ' .. cash
end
```

---

### Related Pages

{% content-ref url="custom-pages.md" %}
[custom-pages.md](custom-pages.md)
{% endcontent-ref %}

{% content-ref url="social-online-time.md" %}
[social-online-time.md](social-online-time.md)
{% endcontent-ref %} 