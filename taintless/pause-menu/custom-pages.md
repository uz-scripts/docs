# Custom Pages Configuration

![FiveM Pause Menu Script](https://uzstore.gitbook.io/~gitbook/image?url=https%3A%2F%2F2351540620-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FcRCyehul5IZdMTnshKMH%252Fuploads%252FrPv2tDS0D2ntkLCNwBF3%252FFrame%25201000005713.png%3Falt%3Dmedia%26token%3De7990457-609f-4d90-83f2-b13ec9b3ea90&width=768&dpr=1&quality=100&sign=8e1a36e5&sv=2)

## Overview

Custom pages allow you to create interactive buttons that link to specific features or events in your server. These pages can be used for shops, VIP areas, weapon stores, or any custom functionality you want to provide to your players.

{% hint style="info" %}
**Note:** Custom pages are fully customizable and can trigger client-side events when clicked.
{% endhint %}

---

## 1. Defining Custom Pages in Customize.lua

You can define custom pages by editing the `CustomPage` section in the `Customize.lua` file.

```lua
CustomPage = {  -- event (client side)
    { color = '#FBCA79', text = 'GAME SHOP',   background = 'GameShop.png',   event = '' },
    { color = '#00f37a', text = 'Vip Cars',    background = 'VipCarShop.png', event = '' },
    { color = '#77CDCC', text = 'Weapon Shop', background = 'WeaponShop.png', event = '' },
}
```

### Configuration Parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| `color` | String | Hex color code for the button text |
| `text` | String | Label displayed on the button |
| `background` | String | Background image filename (stored in `resources/images/CustomPage`) |
| `event` | String | Client-side event name to trigger when clicked |

{% hint style="warning" %}
**Important:** Background images must be placed in the `resources/images/CustomPage` directory.
{% endhint %}

---

## 2. Adding Events for Custom Pages

To make these buttons interactive, you need to add a client-side event. For example, if you want the **GAME SHOP** button to open the game shop interface, you should define an event in your client-side script.

### Example Client-Side Event

```lua
RegisterNetEvent('OpenGameShop', function()
    -- Code to open the game shop interface
    print('Game Shop opened')
    -- Add your custom logic here
end)
```

### Updated Configuration

```lua
CustomPage = {
    { color = '#FBCA79', text = 'GAME SHOP', background = 'GameShop.png', event = 'OpenGameShop' },
    { color = '#00f37a', text = 'Vip Cars', background = 'VipCarShop.png', event = 'OpenVipCars' },
    { color = '#77CDCC', text = 'Weapon Shop', background = 'WeaponShop.png', event = 'OpenWeaponShop' },
}
```

{% hint style="success" %}
**Pro Tip:** Event names must match exactly between your configuration and your client-side event handlers!
{% endhint %}

---

## 3. Customizing Button Appearance

### Color Selection
The `color` attribute allows you to define how each button looks, enabling visual differentiation between custom pages. Choose colors that fit well with your overall design for better user experience.

### Background Images
Background images can be customized to visually represent the purpose of each button:
- Use shopping-related imagery for **Game Shop**
- Use car imagery for **VIP Cars**
- Use weapon imagery for **Weapon Shop**

{% tabs %}
{% tab title="Recommended Sizes" %}
**Image Dimensions:** 200x100 pixels
**Format:** PNG with transparency support
**Quality:** High resolution for crisp display
{% endtab %}

{% tab title="File Locations" %}
**Path:** `resources/images/CustomPage/`
**Examples:**
- `GameShop.png`
- `VipCarShop.png`
- `WeaponShop.png`
{% endtab %}
{% endtabs %}

---

## 4. Testing Your Custom Pages

After making changes, ensure to test each button in the game to verify that:

✅ The correct event is triggered
✅ Visuals are displayed as expected
✅ Colors and images render properly
✅ All interactive elements work smoothly

{% hint style="info" %}
**Testing Checklist:**
1. Restart the resource after configuration changes
2. Check console for any errors
3. Test each button individually
4. Verify events are properly registered
{% endhint %}

---

### Related Pages

{% content-ref url="player-details.md" %}
[player-details.md](player-details.md)
{% endcontent-ref %}

{% content-ref url="social-online-time.md" %}
[social-online-time.md](social-online-time.md)
{% endcontent-ref %} 