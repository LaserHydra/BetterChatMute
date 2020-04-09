**Better Chat Mute** is a simple mute system, made for use with Better Chat. Using with Better Chat is intended, but the plugin can be used standalone as well.

## Permissions

This plugin uses Oxide's permission system. To assign a permission, use `oxide.grant user <name or steam id> <permission>`. To remove a permission, use `oxide.revoke user <name or steam id> <permission>`.

- **betterchatmute.use** -- Required for the `mute` command usage and general use
- **betterchatmute.use.global** -- Required for the `toggleglobalmute` command usage
- **betterchatmute.permanent** -- Required for use of the permanent muting feature

**Note:** Permission betterchatmute.use is always needed, also if you have betterchatmute.permanent

## Commands

**Note**: When trying to use these as console commands in Rust, they need to be prefixed with `bcm`. For example: `bcm.unmute <player|steamid>`  

- **mute `<player|steamid> [reason]`** -- Mutes player permanently
- **mute `<player|steamid> <time: 1d1h1m1s> [reason]`** -- Mutes player temporarily
- **unmute `<player|steamid>`** -- Unmutes player
- **mutelist** -- Shows players that are muted
- **toggleglobalmute** -- Disables chat for every player without the `betterchatmute.use.global` permission

## API (for developers)

### Hooks

```csharp
OnBetterChatMuteHandle(IPlayer player, [CanBeNull]JObject muteInfo) // -> return a non-null value to cancel behaviour
OnBetterChatMuted(IPlayer target, IPlayer initiator, string reason)
OnBetterChatTimeMuted(IPlayer target, IPlayer initiator, TimeSpan time, string reason)
OnBetterChatUnmuted(IPlayer target, IPlayer initiator)
OnBetterChatMuteExpired(IPlayer player)
```

### API Methods

```csharp
void API_Mute(IPlayer target, IPlayer player, string reason = "", bool callHook = true, bool broadcast = true)
void API_TimeMute(IPlayer target, IPlayer player, TimeSpan timeSpan, string reason = "", bool callHook = true, bool broadcast = true)
bool API_Unmute(IPlayer target, IPlayer player, bool callHook = true, bool broadcast = true)
void API_SetGlobalMuteState(bool state, bool broadcast = true)
bool API_GetGlobalMuteState()
bool API_IsMuted(IPlayer player)
List<string> API_GetMuteList()
```
