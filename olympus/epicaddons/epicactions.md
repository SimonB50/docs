---
description: Documentation for EpicAction addon
---

# EpicActions

**EpicActions** addon is a dependency for other addons that allows for running different actions.

## Addon usage

Since this addon is a dependency, it is meant to be used by other addons. See developer documentation for implementation instructions.

## Available actions

### Default actions

<details>

<summary>Give role to user</summary>

```yaml
type: "Role",
action: "Give",
role: # Role to be given
user: # (Optional) User to give role to
```

By default, `user` is a member who triggered the action.

</details>

<details>

<summary>Remove role from user</summary>

```yaml
type: "Role",
action: "Remove",
role: # Role to be removed
user: # (Optional) User to remove role from
```

By default, `user` is a member who triggered the action.

</details>

<details>

<summary>Switch user role</summary>

```yaml
type: "Role",
action: "Switch",
role: # Role to be switched
user: # (Optional) User which role should be switched
```

By default, `user` is a member who triggered the action.

</details>

{% hint style="info" %}
**Switch** is a term for switching whenever the user has the role. \
If the user doesn't have the provided role, it will be given to him but if he does, it will be removed.\
It can be useful if you want to create reaction role menu based on buttons.
{% endhint %}

More default actions (like economy actions) is a topic for future updates to EpicActions.

### Addon actions

Addons are able to register custom actions using developer API (see developer documentation for more information).

{% hint style="warning" %}
**Some actions maybe be compatible only with some EpicAddons.**\
For example, if action requires action message, it will not be compatible with EpicTimers.
{% endhint %}

#### EpicPresets

<details>

<summary>Send a preset in the channel</summary>

```yaml
type: "Preset",
action: "Send",
preset: # Preset to send
channel: # (Optional) Channel, where the preset should be sent
```

By default, `channel` is a channel where the action was triggered.

</details>

<details>

<summary>Edit message following the preset</summary>

```yaml
type: "Preset",
action: "Edit",
newPreset: # New preset for the message to be edited to
```

This will edit the message which triggered the action.\
**This action requires message to be sent by the bot to work!**

</details>

## Developer API

This section of documentation is still W.I.P.
