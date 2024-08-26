---
description: >-
  Documentation for utils file containing useful functions for addon
  development.
---

# 🍌 BananaUtils

**BananaUtils** is utils file that is required by all addons listed in this documentation and needs to be downloaded separately.

## Installation

While BananaUtils is not an addon it should be installed like one, therefore to install it you need to put `bananaUtils.js` file downloaded from [BuiltByBit resource page](https://builtbybit.com/resources/olympus-utils-bananautils.50368/).

## BrayanBot config migration

BananaUtils allows BrayanBot using to migrate their configs to the Olympus Bot format. Actions performed are:

1. Making all keys start from small letter
2. Removes BrayanBot slash command config and leaves only options object
3. Makes option type names start from capital letter
4. Renames file to start from small letter

Old file is saved under `oldname.yml.old` file.

To trigger the config migration, user is required to add `# BRAYANBOT MIGRATE #` to the end of the config file. All `.old` files will be ignored and won't be migrated.

## Developer API

BananaUtils is meant to be used by addon developers or easier and faster addon development.\
Before using BananaUtils functions, it's best to **register addon**. This functions should be called at the top of addon code.

```javascript
const bananaUtils = require("./bananaUtils");
bananaUtils.handleAddon("addonName");
```

This, will register which creates a folder in `addons_config` called the same as registered addon name and allows for [**BrayanBot config migration**](utils.md#brayanbot-config-migration).

### Setup message

With `setupMessage` you are able to transform user-created message config to discord.js message config object. This functions includes support for `content`, `embeds` and `components`. It also supports `variables` both manual and these created using `Utility` functions.

```javascript
const bananaUtils = require("./bananaUtils");
const Utility = require("../utils/modules/Utility");

// ...

message.reply(bananaUtils.setupMessage({
    configPath: // Message config object (See below)
    variables: {
        example: "This is an example variable",
        ...Utility.botVariables(client),
    }
    
});
```

All possible options for `configPath` are listed below in YAML format - since these options should be provided as options in you addon config file which should use YAML (as this is format that is used by Olympus Bot).

#### Message content

`content` contains the text that will be sent as a normal discord message content.

#### Message embeds

`embeds` is a list of objects containing configuration for embeds attached to the message. Limit of embeds in one message is **10**.

```yaml
author: # Embed author
authorIcon: # Embed author icon url
title: # Embed title
url: # Embed (title) URL
description: # Embed content
fields: # Embed fields - see below
footer: # Embed footer
footerIcon: # Embed footer icon url
thumbnail: # Embed thumbnail url
image: # Embed image url
color: # Embed color HEX code
timestamp: # Whenever timestamp should be visible (true/false)
```

`fields` is a list of config objects for embed fields. Limit of fields in one embed is **25**.

```yaml
name: # Field name
value: # Filed content
inline: # Whenever this field should be in the same line (true/false)
```

#### Message components

`components` is a object containting from 1 to 5 actions row config objects.

```yaml
components:
  "1":
  "2":
  "3":
  "4":
  "5":
```

Each action row can list of interactive elements - which can be both buttons and select menus. Each action row has a limit of **5** interactive elements.

#### Button component

```yaml
type: Button
style: # Button type. Available types: Primary, Secondary, Success, Danger, Link
label: # Button label
emoji: # Button emoji
customId: # Button customId
```

{% hint style="danger" %}
Button style `Link` is a unique button style. It is for opening urls after it's clicked. While it doesn't require `customId` you need to provide `link` containing url that should be opened after clicking the button.
{% endhint %}

#### Select Menu component

```yaml
type: SelectMenu
placeholder: # Menu placeholder
customID: # Menu customId
minSelect: # Minimum count of options to be selected. Default: 0
maxSelect: # Maximum count of options to be selected. Default: None 
options: # Menu options - see below
```

`options` is a list of config objects for select menu options

```yaml
default: # Whenever the option should be selected by default. (true/false)
label: # Option label
description: # Option description
emoji: # Option emoji
value: # Option value
```

### Setup command

This function is on **BananaUtils roadmap** and will be implemented in the future.

### Other functions

```javascript
const bananaUtils = require("./bananaUtils");

// Check whenever user has specific role
// member - GuildMember, role - String
if (bananaUtils.hasRole(member, role)) {
    // Do stuff
}
```

```javascript
const bananaUtils = require("./bananaUtils");
const Utility = require("../utils/modules/Utility");

// Replace variable in provided text
// text - String, variables - variables config
let text = "Bot username is {bot-username}";
let variables = Utility.botVariables(client);
text = replaceVariables(text, variables); // Bot username is awesomeUsername
```

```javascript
const bananaUtils = require("./bananaUtils");

// Lowercase first letter of a string
let text = "String";
text = bananaUtils.lowercaseFirstLetter(text); // string
```

```javascript
const bananaUtils = require("./bananaUtils");

// Lowercase first letter of a string
let text = "string";
text = bananaUtils.capitalizeFirstLetter(text); // String
```
