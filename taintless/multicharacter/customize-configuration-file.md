---
description: >-
  This file contains the necessary configurations for the character creation and
  management system. Below is a comprehensive explanation of what each parameter
  does and how to configure them properly.
---

# Customize Configuration File

### Table of Contents

* UI Configuration
* Character Slots
* Spawn Settings
* Character Appearance
* Items and Commands
* Advanced Settings

***

### UI Configuration

#### UIColor

Defines the interface colors using hex color codes.

> **💡 Tip:** You can use any hex color code for the interface color (e.g., #FF4F79, #FBCA79, #3498db)

```lua
UIColor = '#FBCA79', -- Interface color
```

#### UIDisplay

Controls which UI elements are displayed to players.

```lua
UIDisplay = {
    BuySlot = true,         -- Shows the character slot purchase button
    DeleteCharacter = true, -- Shows the character deletion button
},
```

#### CustomUIFunction

Allows you to define custom interface logic that triggers when the camera becomes active.

```lua
CustomUIFunction = function(get) -- (get: true/false) true when camera is active
    -- Add your custom UI logic here
    -- Example: Toggle HUD visibility when character selection is active
    -- exports['your-hud']:toggleHUD(not get)
end,
```

***

### Character Slots

#### MaxCharacterSlot

Sets the maximum number of character slots a player can have.

```lua
MaxCharacterSlot = 6, -- Maximum number of character slots
```

#### DefaultCharSlot

Determines how many character slots players start with by default.

```lua
DefaultCharSlot = 3, -- Default number of character slots for new players
```

***

### Spawn Settings

#### SkipSelection

When enabled, players will skip the spawn selection menu and respawn at their last location.

```lua
SkipSelection = false, -- Set to true to skip spawn selection
```

#### SpawnFunction

Defines custom spawn logic that runs on the client side when a character spawns.

> **⚠️ Note:** This function only runs on the client side.

```lua
SpawnFunction = function(data) -- (client-side only)
    -- Custom spawn logic goes here
    TriggerEvent('qb-spawn:client:setupSpawns', data.citizenid)
    TriggerEvent('qb-spawn:client:openUI', true)
    
    -- You can add additional spawn logic here
    -- Example: Set player health, armor, etc.
end,
```

#### DefaultSpawn

Sets the default spawn location using vec4 format (x, y, z, heading).

```lua
DefaultSpawn = vec4(-540.58, -212.02, 37.65, 208.88), -- Default spawn coordinates
```

#### SetHousingSpawnUI

Configures the housing spawn interface for apartment/property spawning.

```lua
SetHousingSpawnUI = function(data) -- (client side only)
    UZFramework.Apartment.setupSpawnUI(data)
    -- Alternative: TriggerEvent('apartments:client:setupSpawnUI', data)
end,
```

***

### Character Appearance

#### SetSkin

Handles character skin/appearance setup on the client side.

> **⚠️ Note:** This function only runs on the client side.

```lua
SetSkin = function(skin, ped) -- (client-side only)
    UZCustomize.Apparance.SetSkin(skin, ped) -- Apply skin to character
end,
```

#### SkinSql

Retrieves character skin data from the database on the server side.

> **⚠️ Note:** This function only runs on the server side.

```lua
SkinSql = function(data) -- (server-side only)
    return MySQL.single.await('SELECT * FROM playerskins WHERE citizenid = ? AND active = 1', {data.citizenid})
end,
```

#### FirstCharacterSkinMenu

Opens the character customization menu when creating a new character.

> **⚠️ Note:** This function only runs on the client side.

```lua
FirstCharacterSkinMenu = function(skin, ped) -- (client-side only)
    local event = (UZCustomize.Framework == "ESX") and 'esx_skin:openSaveableMenu' or 'qb-clothes:client:CreateFirstCharacter'
    TriggerEvent(event)
end,
```

***

### Items and Commands

#### StarterItems

Defines the items given to new characters upon creation.

```lua
StarterItems = { -- Items given to new characters
    { name = 'phone', amount = 1 },          -- Mobile phone
    { name = 'id_card', amount = 1},         -- Identification card
    { name = 'driver_license', amount = 1},  -- Driver's license
    -- Add more starter items as needed
},
```

#### Command

Configures custom commands with permission levels.

```lua
Command = {
    ['logout'] = {
        Permission = 'admin',           -- Required permission level
        Command = 'logout',             -- Command name
        Text = 'Logout (Admin Only)',   -- Display text
        Description = {}                -- Command description
    },
    ['setchar'] = {
        Permission = 'admin',           -- Required permission level
        Command = 'setchar',            -- Command name
        Text = 'Set Character Slots',   -- Display text
        Description = {
            {name='Owner', help='CitizenID or License'},  -- Parameter 1
            {name='Slot', help='New Max Slot'}           -- Parameter 2
        }
    }
},
```

***

### Advanced Settings

#### CharacterOffsets

Defines positioning offsets for character display based on the number of available slots.

```lua
CharacterOffsets = {
    [1] = { -- Single character position
        {x = 0.11, y = -0.6, z = -1.4, h = 170.0}
    },
    [2] = { -- Two character positions
        {x = -0.21, y = -0.5, z = -1.5, h = 190.15}, -- Left position
        {x = 0.59,  y = -0.5, z = -1.5, h = 140.15}  -- Right position
    },
    [3] = { -- Three character positions
        {x = -0.61, y = -0.5, z = -1.5, h = 200.15}, -- Left
        {x = 0.11,  y = -0.6, z = -1.4, h = 170.0},  -- Center
        {x = 0.99,  y = -0.5, z = -1.5, h = 130.15}  -- Right
    },
    -- Add more configurations for additional slots as needed
},
```

#### GiveStarterItems

Function that handles giving starter items to new characters. Supports both QBX and QB-Core frameworks.

```lua
function GiveStarterItems(source)
    local src = source
    for _, v in pairs(Customize.StarterItems) do
        local info = {}
        
        -- QBX Core compatibility
        if GetResourceState('qbx_core'):find('start') then
            if v.name == "id_card" then
                info = exports.qbx_idcard:GetMetaLicense(src, {'id_card'})
            elseif v.name == "driver_license" then
                info = exports.qbx_idcard:GetMetaLicense(src, {'driver_license'})
            end
        -- QB Core compatibility
        elseif GetResourceState('qb-core'):find('start') then
            local Player = Framework.Functions.GetPlayer(src)
            if v.name == "id_card" then
                info = {
                    citizenid = Player.PlayerData.citizenid,
                    firstname = Player.PlayerData.charinfo.firstname,
                    lastname = Player.PlayerData.charinfo.lastname,
                    birthdate = Player.PlayerData.charinfo.birthdate,
                    gender = Player.PlayerData.charinfo.gender,
                    nationality = Player.PlayerData.charinfo.nationality
                }
            elseif v.name == "driver_license" then
                info = {
                    firstname = Player.PlayerData.charinfo.firstname,
                    lastname = Player.PlayerData.charinfo.lastname,
                    birthdate = Player.PlayerData.charinfo.birthdate,
                    type = "Class C Driver License"
                }
            end
        end
        
        UZFramework.AddItem(Player or nil, v.name, v.amount, info, src)
    end
end
```

#### QBXConfig

Loads the configuration file for QBX Core framework compatibility.

```lua
QBXConfig = function(appaYeet)
    local configData = LoadResourceFile('qbx_core', 'config/client.lua')
    local configFunc = load(configData)
    return configFunc()
end
```
