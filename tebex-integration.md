# 🛠️ Tebex Integration

{% hint style="info" %}
**Overview**: This guide will walk you through the complete process of integrating Tebex with your game server, enabling automated product delivery and payment processing.
{% endhint %}


### Prerequisites

{% hint style="warning" %}
**Before you start, ensure you have:**

* Administrative access to your Tebex account
* Server configuration file access (`server.cfg`)
* The script you want to integrate installed and working
* Basic understanding of server commands
{% endhint %}

***

### Step 1: Connect Game Server

Navigate to **Tebex > Game Servers > Connect Game Server** in your Tebex dashboard.

![Tebex Integration](https://uzstore.gitbook.io/~gitbook/image?url=https%3A%2F%2F2351540620-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FcRCyehul5IZdMTnshKMH%252Fuploads%252F3h2pkZtR8tyZqYbDKidX%252F1.png%3Falt%3Dmedia%26token%3D8340eb31-24ec-44a4-ac9c-f499ee2cd2e8\&width=768\&dpr=4\&quality=100\&sign=faf34fd6\&sv=2)

{% hint style="info" %}
**Note**: Copy the secret key that Tebex provides - you'll need it in the next step.
{% endhint %}

***

### Step 2: Configure Server

Add the **Tebex secret code** to your `server.cfg` file. This establishes the connection between your server and Tebex.

```cfg
# Add this line to your server.cfg
set tebex_secret "YOUR_SECRET_KEY_HERE"
```

![Paste Tebex Secret](https://uzstore.gitbook.io/~gitbook/image?url=https%3A%2F%2F2351540620-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FcRCyehul5IZdMTnshKMH%252Fuploads%252Fg4BLSaqnFksh2GNyU8z2%252F2.png%3Falt%3Dmedia%26token%3D65fa81ae-0b38-4681-bf3b-f37d20710410\&width=768\&dpr=4\&quality=100\&sign=62294c5\&sv=2)

{% hint style="success" %}
**Server Connection Complete**: Your server is now connected to Tebex. You can proceed to create products and link them to your scripts.
{% endhint %}

***

### Step 3: Create a Package in Tebex

Navigate to **Tebex > Package > Create Package** to set up your product.

![Create Package](https://uzstore.gitbook.io/~gitbook/image?url=https%3A%2F%2F2351540620-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FcRCyehul5IZdMTnshKMH%252Fuploads%252FrxvGRClDhPsuTvxOtArY%252F3.png%3Falt%3Dmedia%26token%3D70b67753-ca70-413a-9e99-11eca2cc7c89\&width=768\&dpr=4\&quality=100\&sign=761be50c\&sv=2)

#### Package Configuration Tips:

{% hint style="info" %}
**Recommended Settings**:

* Set a clear, descriptive package name
* Add detailed description for customers
* Configure appropriate pricing
* Set purchase limits if needed
* Enable/disable as required
{% endhint %}

***

### Step 4: Configure Script Commands

This is the crucial step where you define what happens when a customer purchases your package.

![Script Command](https://uzstore.gitbook.io/~gitbook/image?url=https%3A%2F%2F2351540620-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FcRCyehul5IZdMTnshKMH%252Fuploads%252FCbh87ck8pwIYPoUPzg2t%252F4.png%3Falt%3Dmedia%26token%3Deab690dc-9c0d-4a3c-8769-ffcd1eba5c1f\&width=768\&dpr=4\&quality=100\&sign=72fffeed\&sv=2)

#### Available Script Commands:

{% tabs %}
{% tab title="Multicharacter" %}
For UZ-Scripts Multicharacter system:

```bash
purchase_multicharacter_newslot {"transid":  "{transaction}"}
```

This command grants a new character slot to the purchaser.
{% endtab %}

{% tab title="Daily Reward" %}
For UZ-Scripts Daily Reward system:

```bash
purchase_dailyreward {"transid":  "{transaction}"}
```

This command activates daily reward benefits for the purchaser.
{% endtab %}
{% endtabs %}

{% hint style="warning" %}
**Important**: Make sure the commands you use are compatible with your server setup and the scripts are properly installed.
{% endhint %}

***

### Step 5: Testing and Activation

Before going live, thoroughly test your integration to ensure everything works correctly.

![Testing](https://uzstore.gitbook.io/~gitbook/image?url=https%3A%2F%2F2351540620-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FcRCyehul5IZdMTnshKMH%252Fuploads%252FACxPf9wEU5eI9iV0B8G9%252F5.png%3Falt%3Dmedia%26token%3D4e4d3ba7-a1f2-488e-8c70-790b047263da\&width=768\&dpr=4\&quality=100\&sign=7899df95\&sv=2)

#### Testing Checklist:

* [ ] Verify server connection status in Tebex dashboard
* [ ] Test purchase with test payment methods
* [ ] Confirm commands execute correctly
* [ ] Check player receives items/permissions
* [ ] Validate transaction logs

{% hint style="info" %}
**Testing Tip**: Use Tebex's test payment methods to verify your setup without real money transactions.
{% endhint %}

***

### Final Configuration

![Final Step](https://uzstore.gitbook.io/~gitbook/image?url=https%3A%2F%2F2351540620-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FcRCyehul5IZdMTnshKMH%252Fuploads%252FHGia1PNlq10QHY4zArPu%252F6.png%3Falt%3Dmedia%26token%3D6d84d785-1e3e-40b2-b6cf-5b2783e6f075\&width=768\&dpr=4\&quality=100\&sign=131735dc\&sv=2)

***

### Troubleshooting

#### Common Issues and Solutions:

{% hint style="danger" %}
**Server Not Connecting**

* Double-check the secret key in your `server.cfg`
* Ensure your server is online and accessible
* Verify firewall settings allow Tebex connections
{% endhint %}

{% hint style="warning" %}
**Commands Not Executing**

* Verify script is properly installed and running
* Check command syntax matches your script requirements
* Review server console for error messages
* Ensure player is online when purchase is made
{% endhint %}

{% hint style="info" %}
**Payment Issues**

* Check Tebex payment gateway settings
* Verify your store is published and not in draft mode
* Ensure pricing and currency are correctly configured
{% endhint %}

#### Getting Help:

* **Tebex Support**: Contact through their official support channels
* **UZ-Scripts Support**: Join their Discord server for script-specific help
* **Server Logs**: Always check your server console and logs for detailed error information

***

### Best Practices

#### Security:

* Keep your Tebex secret key private and secure
* Regularly update your scripts and server software
* Monitor transaction logs for unusual activity

#### User Experience:

* Provide clear product descriptions
* Set reasonable prices for your community
* Offer good customer support for purchase issues

#### Maintenance:

* Regularly test your integrations
* Keep backups of your configuration
* Stay updated with Tebex and script updates

***

{% hint style="success" %}
**🎉 Congratulations!** Your Tebex integration is now complete and ready to use. Your players can now purchase items directly through your Tebex store, and the integration will automatically handle the delivery.
{% endhint %}
