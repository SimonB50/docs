---
description: Documentation for EpicInteractions addon
---

# EpicInteractions

**EpicInteractions** is an addon that allows for creating interactive messages using Discord buttons and select menus**.**

## Creating interactive messages

For creating interactive messages you need to setup a message with some button(s) or menu(s). To do that, you can use [EpicPresets](epicpresets.md#message-components).\
While creating you will need to use unique `customId`s and write them down - that's what you need to make everything work.

### Making buttons work

To make working button, you need to open `buttons.yml` config file and create new button config object in the `buttons` list.

```yaml
name: # Button name
customId: # Button ID - unique + lowercase + no_spaces
actions: # Button actions - see below
reply: # Button reply - see below
```

`actions` is a list of actions config objects from [EpicActions](epicactions.md#available-actions) to execute.\
`reply` is a config object for interaction response. [Click here for more info.](epicinteractions.md#interaction-replies)

### Making menus work

To make a working select menu, you need to open `menus.yml` config file and create new menu config object in the `menus` list.

```yaml
name: menu # Menu name
customId: # Menu ID - unique + lowercase + no_spaces
options: # Menu options
reply: # Button reply - see below
```

`options` is a list of select menu objects.\
`reply` is a config object for interaction response. [Click here for more info.](epicinteractions.md#interaction-replies)

Option config object format

```yaml
name: # Option value
actions: # Option actions
```

`name` is representing the value of option, which means that if options selected by user contain one with this value, all added `actions` will be executed.

### Interaction replies

For handling responses you need to select a preset from [EpicPresets](epicpresets.md).

```yaml
preset: # Preset name
private: # Whenever the reply should be private
```
