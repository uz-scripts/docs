# Installation Guide

Welcome to the **UZ Multicharacter** installation guide! This comprehensive tutorial will help you install and configure the multicharacter system for your FiveM server.

{% hint style="success" %}
**Before You Begin:** Make sure you have purchased the resource from our official store and have access to your Keymaster account.
{% endhint %}

### 📋 Prerequisites

Before starting the installation, ensure you have:

* ✅ FiveM server with admin access
* ✅ Basic knowledge of server file management
* ✅ FTP client or server file manager access
* ✅ Text editor for configuration files
* ✅ Active Keymaster account with purchased resource

{% hint style="info" %}
**Supported Frameworks:** ESX, QBCore, QBX
{% endhint %}

### 🔗 Dependencies

Make sure these resources are installed and running:

| Resource       | Required | Purpose                    |
| -------------- | -------- | -------------------------- |
| `uz_core`      | ✅ Yes    | Core framework integration |
| `oxmysql`      | ✅ Yes    | Database operations        |
| Your framework | ✅ Yes    | ESX/QBCore/QBX             |

### 📥 Step 1: Download from Keymaster

#### 1.1 Access Your Purchase

1. Navigate to [Keymaster Assets](https://portal.cfx.re/assets/granted-assets)
2. Log in with your CFX.re account credentials
3. Search for **"uz\_Multicharacter"** in your granted assets
4. Locate the resource in your purchased items list

#### 1.2 Download the Files

1. Click the **📥 Download** button next to the resource
2. The download will start as a `.zip` file
3. Wait for the download to complete
4. Extract the contents to a temporary folder

{% hint style="warning" %}
**Important:** Always download the latest version to ensure compatibility and security updates.
{% endhint %}

### 📁 Step 2: Server File Management

#### 2.1 Access Your Server

Choose your preferred method:

**Option A: FTP Client**

* Use FileZilla, WinSCP, or similar
* Connect to your server using FTP credentials

**Option B: Server Panel**

* Access your hosting provider's file manager
* Navigate to server files section

**Option C: Direct Access**

* SSH into your server (advanced users)
* Use command line file operations

#### 2.2 Upload the Resource

1. Navigate to your server's `resources` folder
2. Create a new folder structure: `resources/[scripts]/`
3. Upload the extracted `uz_Multicharacter` folder
4. Ensure all files are properly uploaded
5. Verify folder permissions (755 recommended)

**Expected folder structure:**

```
resources/
└── [UZ]/
    └── uz_Multicharacter/
        ├── client/
        ├── locales/
        ├── resources/
        ├── server/
        ├── Customize.lua
        ├── fxmanifest.lua
```

### ⚙️ Step 3: Server Configuration

#### 3.1 Update server.cfg

Open your `server.cfg` file and add the following:

```bash
# Core Dependencies (Add these first)
ensure oxmysql
ensure [your_framework]  # esx/qbcore/qbx
ensure uz_core

# UZ Scripts (Add at the bottom)
ensure uz_Multicharacter
```

{% hint style="danger" %}
**Critical:** Always place `ensure uz_Multicharacter` at the **very bottom** of your startup order to prevent loading conflicts.
{% endhint %}

#### 3.2 Verify Load Order

Your startup order should look like this:

```bash
# 1. Database
ensure oxmysql

# 2. Framework
ensure es_extended  # or qb-core/qbx_core

# 3. Core Dependencies
ensure uz_core

# 4. Other resources...
ensure other-resources

# 5. UZ Scripts (LAST)
ensure uz_Multicharacter
```

### 🔧 Step 4: Resource Configuration

#### 4.1 Basic Configuration

1. Navigate to `uz_Multicharacter/Customize.lua`
2. Open the file in your text editor
3. Configure the settings according to your preferences:

### 🎮 Step 5: Framework Integration

#### QBX Framework

{% hint style="info" %}
**QBX Users:** Follow these specific configuration steps.
{% endhint %}

1. Open `qbx_core/shared/config/client.lua`
2. Find the multicharacter section
3. Update the configuration:

```lua
-- Multicharacter Settings
useExternalCharacters = true,
startingApartment = false, -- Disable default apartments
enableCharacterCreator = false, -- Use UZ system
```

4. Save and close the file

#### ESX Framework

{% hint style="info" %}
**ESX Users:** Simple one-line configuration required.
{% endhint %}

1. Open `es_extended/shared/config/main.lua`
2. Find or add the multichar configuration:

```lua
-- Multicharacter Integration
Config.Multichar = GetResourceState("uz_Multicharacter") ~= "missing"
Config.StartingAccountMoney = {bank = 50000} -- Optional: Starting money
```

3. Save the file

#### QBCore Framework

{% hint style="success" %}
**QBCore Users:** No additional configuration needed! The resource works out of the box.
{% endhint %}

### 🗄️ Step 6: Database Setup

#### 6.1 Automatic Setup

The resource includes automatic database setup. When you first start the server:

1. Tables will be created automatically
2. Default configurations will be applied
3. Check your server console for confirmation

#### 6.2 Manual Setup (If Needed)

If automatic setup fails, manually run:

```sql
CREATE TABLE IF NOT EXISTS `uz_multichar` (
  `owner` varchar(65) DEFAULT NULL,
  `maxchar` int(11) DEFAULT 1,
  UNIQUE KEY `owner` (`owner`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

CREATE TABLE IF NOT EXISTS `uz_multichar_tebex` (
  `tebex` varchar(255) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COLLATE=utf8_general_ci;
```

### 🚀 Step 7: Server Restart & Testing

#### 7.1 Restart Your Server

1. Stop your FiveM server completely
2. Wait 10-15 seconds for full shutdown
3. Start the server again
4. Monitor the console for any errors

#### 7.2 In-Game Testing

1. Connect to your server
2. You should see the multicharacter selection screen
3. Test creating a new character
4. Test switching between characters
5. Verify all features work as expected

### 🔍 Troubleshooting

#### Common Issues

| Issue                  | Solution                                      |
| ---------------------- | --------------------------------------------- |
| Characters not loading | Check database permissions and table creation |
| UI not showing         | Verify resource load order in server.cfg      |
| Spawn issues           | Check DefaultSpawn coordinates in config      |
| Framework conflicts    | Ensure proper framework configuration         |

### 📞 Support & Updates

#### Getting Help

{% hint style="info" %}
**Need Help?** Contact our support team through:

* 🎫 Support ticket system
* 💬 Discord community
* 📧 Email support
{% endhint %}

#### Updates

{% hint style="warning" %}
**Stay Updated:**

* Check Keymaster regularly for updates
* Always backup your server before updating
* Read changelogs for breaking changes
{% endhint %}

#### Backup Recommendations

Before any changes:

1. Backup your `customize.lua` file
2. Export character data from database
3. Create server file backup
4. Test updates on development server first

### ✅ Installation Complete!

Congratulations! Your **UZ Multicharacter** system is now installed and ready to use.

**Next Steps:**

* Customize the appearance to match your server theme
* Configure character creation rules
* Set up any additional integrations
* Train your staff on the new system

{% hint style="success" %}
🎉 **Success!** Your players can now enjoy a seamless multicharacter experience on your FiveM server!
{% endhint %}

***

_Thank you for choosing UZ Scripts! We're committed to providing the best FiveM resources for your server._
