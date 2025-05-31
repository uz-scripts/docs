# Announces

![FiveM Pause Menu Script](https://uzstore.gitbook.io/~gitbook/image?url=https%3A%2F%2F2351540620-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FcRCyehul5IZdMTnshKMH%252Fuploads%252F0sQQV8xSVxMUAHgwmrJK%252FPROJECT%2520ANNOUNCES.png%3Falt%3Dmedia%26token%3Db4ae6f08-754f-497f-9ab0-ef73d7a36296&width=768&dpr=1&quality=100&sign=4fdeeb7f&sv=2)

## Announces Overview

Announcements are used to communicate important messages to players, such as server updates, events, or general announcements. The announce system can include text, headers, dates, and optionally images to make your messages more engaging.

{% hint style="info" %}
**Important:** Make sure to configure your announces properly in the `Announces.json` file to ensure they display correctly to your players.
{% endhint %}

### 1. Structure of Announces in `Announces.json`

The announcements are defined in the `Announces.json` file. Each announcement includes several key elements:

```json
[
    {
        "text": "Lorem ipsum dolor sit amet consectetur. Penatibus ullamcorper dui suscipit fringilla dis magna. Et viverra tellus vitae id congue tellus lorem. Pharetra feugiat nunc facilisi vitae pellentesque integer. Hendrerit orci rutrum odio.",
        "date": "05.09.2024",
        "header": "Welcome to the server!",
        "photo": ""
    }
]
```

#### Fields Explanation

| Field | Type | Description |
|-------|------|-------------|
| `text` | String | The main content of the announcement |
| `date` | String | Date when the announcement was created (format: DD.MM.YYYY) |
| `header` | String | Title/header of the announcement |
| `photo` | String | Optional image URL for the announcement |

{% hint style="warning" %}
**Note:** If you don't want to include an image, leave the `photo` field as an empty string `""`.
{% endhint %}

### 2. Adding New Announces

There are two ways to add new announcements to your server:

#### Method 1: Using In-Game Commands

To add a new announce using the in-game command:

```
/addAnnounce Header Text
```

**Example:**
```
/addAnnounce "Weekend Event" "Join us for an exciting new event happening this weekend. There will be exclusive rewards!"
```

#### Method 2: Manual Addition via JSON File

1. Open the `Announces.json` file
2. Copy an existing announcement object
3. Modify the `text`, `date`, `header` and `photo` fields as needed:

```json
{
    "text": "Join us for an exciting new event happening this weekend. There will be exclusive rewards!",
    "date": "10.10.2024",
    "header": "Weekend Event Announcement!",
    "photo": "https://i.imgur.com/3taJXrA.jpeg"
}
```

### 3. Command Customization

You can customize the announce command in the `Customize.lua` file:

```lua
Command = {
    Permission = 'admin',
    Command = 'addAnnounce',
    Text = 'New Announce',
    Description = {
        {name='Header', help='Header'},
        {name='Text', help='Text'},
    }
}
```

#### Command Configuration Options

| Option | Description |
|--------|-------------|
| `Permission` | Authorization level required to use the command (e.g., `admin`, `moderator`) |
| `Command` | The actual command name (default: `addAnnounce`) |
| `Text` | Description text for the command |
| `Description` | Command syntax helper with parameter descriptions |

### 4. Adding Multiple Announces

You can add multiple announcements by creating additional objects in the JSON array:

```json
[
    {
        "text": "First announcement content here...",
        "date": "05.09.2024",
        "header": "Server Update",
        "photo": "https://example.com/image1.jpg"
    },
    {
        "text": "Second announcement content here...",
        "date": "06.09.2024",
        "header": "New Event",
        "photo": ""
    },
    {
        "text": "Important maintenance scheduled for tonight. Server will be offline from 2 AM to 4 AM EST.",
        "date": "07.09.2024",
        "header": "Maintenance Notice",
        "photo": ""
    }
]
```

{% hint style="success" %}
**Pro Tip:** You can update announcements instantly using in-game commands or by editing the `Announces.json` file directly!
{% endhint %}

---

### Related Pages

{% content-ref url="configuration.md" %}
[configuration.md](configuration.md)
{% endcontent-ref %}

{% content-ref url="customization.md" %}
[customization.md](customization.md)
{% endcontent-ref %} 