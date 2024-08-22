---
description: Documentation for EpicPresets addon
---

# EpicPresets

[**EpicPresets**](#user-content-fn-1)[^1] addon allows for sending messages based on presets predefined in the config file.

## Basic addon configuration

For basic addon configuration, check `config.yml`, `commands.yml` and `language.yml.` These files include configs for both functions and messages across the addon.&#x20;

## Creating presets

Default set of presets that showcase all possible config options are available in the `presets.yml` file.

Now, let's break down all possible features that can be used while creating a preset

&#x20;All presets contain to values: `name` which is a preset name that must be lowercase and `message` containing message config.

You can see all available message options below.

{% hint style="info" %}
This part of documentation is temporary and will be moved to BananaUtils section after it's done.
{% endhint %}

### Message content

`content` contains the text that will be sent as a normal discord message content.

### Message embeds

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

### Message components

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

{% hint style="danger" %}
Only one option can have `default` value set to `true`.
{% endhint %}

## Sending presets

To send a preset that you created, use `preset` command. Running it without any arguments will display all available presets. To send specific preset, run `preset [presetName]` . You can also add a channel where the preset should be sent (by default, preset will be sent in the channel where the command was executed).

{% hint style="info" %}
You can also send presets using EpicActions! Check the addon docs for more information.
{% endhint %}

## Developer API

This section of documentation is still W.I.P.

[^1]: Awaiting Olympus verification
