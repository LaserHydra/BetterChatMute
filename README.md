**Better Chat Mute** is a simple mute system, made for use with Better Chat. Using it alone will not do anything, so make sure you have Better Chat installed.

## Permissions

This plugin uses Oxide's permission system. To assign a permission, use `oxide.grant user <name or steam id> <permission>`. To remove a permission, use `oxide.revoke user <name or steam id> <permission>`.

- **betterchatmute.use** -- Required for the `mute` command usage and general use
- **betterchatmute.use.global** -- Required for the `toggleglobalmute` command usage
- **betterchatmute.permanent** -- Required for use of the permanent muting feature

**Note:** Permission betterchatmute.use is always needed, also if you have betterchatmute.permanent

## Commands

- **mute `<player|steamid>`** -- Mutes player permanently
- **mute `<player|steamid> [time: 1d1h1m1s]`** -- Mutes player temporarily
- **unmute `<player|steamid>`** -- Unmutes player
- **mutelist** -- Shows players that are muted
- **toggleglobalmute** -- Disables chat for every player without the `betterchatmute.use.global` permission

## API (for developers)

```csharp
void API_Mute(IPlayer target, IPlayer player, bool callHook = true, bool broadcast = true)
void API_TimeMute(IPlayer target, IPlayer player, TimeSpan timeSpan, bool callHook = true, bool broadcast = true)
bool API_Unmute(IPlayer target, IPlayer player, bool callHook = true, bool broadcast = true)
void API_SetGlobalMute(bool state)
List<string> API_GetMuteList()
bool API_GetGlobalMuteState()
bool API_IsMuted(IPlayer player)
```
