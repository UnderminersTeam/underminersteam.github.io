---
title: General Info JSON Specification
weight: 101
---

This page contains the specification for the optional `general-info-options.json` file that can be created at the root level of a project, in order to customize General Info of a game.

## JSON fields

**Every one of these fields is optional. If not supplied, values will remain at what already exists within a game's data file.**

Also, it's worth noting that there are redundancies between [`InfoFlags`](#infoflags) and [`OptionsFlags`](#optionsflags) for unknown reasons.

| Field | Type | Description |
| ----- | ---- | ----------- |
| `FileName` | `string` | The name of the runner (runtime) executable file. |
| `Config` | `string` | The name of the configuration the game is using. (As defined in GameMaker.) |
| `GameID` | `uint` | Unsigned 32-bit integer representing the ID of the game. |
| `Name` | `string` | The internal name of the game, e.g. used for savedata directories (not the display name). |
| `DefaultWindowWidth` | `uint` | Unsigned 32-bit integer representing the default window width of the game. |
| `DefaultWindowHeight` | `uint` | Unsigned 32-bit integer representing the default window height of the game. |
| `GeneralInfo` | [`InfoFlags`](#infoflags) | Comma-separated flags that can enable/disable engine features that the game uses. |
| `DisplayName` | `string` | The display name that is used for the game, e.g. displayed in the window title by default. |
| `SteamAppID` | `int` | Signed 32-bit integer representing the Steam App ID of the game. May be negative. |
| `GMS2FPS` | `float` | 32-bit floating pointer number representing the default game FPS, in games using GMS2 or above. |
| `OptionsInfo` | [`OptionsFlags`](#optionsflags) | Comma-separated flags that can enable/disable additional engine features that the game uses. |
| `VertexSync` | `uint` | Unsigned 32-bit integer representing vertical synchronization, which can avoid tearing. Typically just 0 or 1. |

## InfoFlags

Represents engine features in a comma-separated `string`.

Example:
```json
"SyncVertex1, Scale, ShowCursor, BorderlessWindow"
```

All possible features are:
| Name | Description |
| ---- | ----------- |
| `Fullscreen` | Start the game in fullscreen. |
| `SyncVertex1` | Use synchronization to avoid tearing. |
| `SyncVertex2` | An alternate way to use synchronization to avoid tearing. (The difference is not well-known.) |
| `Interpolate` | Interpolate colors between pixels. |
| `Scale` | Maintain aspect ratio when scaling the game. |
| `ShowCursor` | Display the mouse cursor by default. |
| `Sizeable` | Allow the game window to be resized. |
| `ScreenKey` | Allows fullscreen switching. (Not well-understood.) |
| `SyncVertex3` | (Unknown.) |
| `StudioVersionB1` | (Unknown.) |
| `StudioVersionB2` | (Unknown.) |
| `StudioVersionB3` | (Unknown.) |
| `SteamEnabled` | Whether Steam (or the ancient YoYoPlayer) is enabled. |
| `UseAppDataSaveLocation` | When enabled, the game will write save data to `%appdata%\GameName`, otherwise it will write to `%localappdata%\GameName` |
| `BorderlessWindow` | Whether the game supports borderless window. |
| `JavaScriptMode` | Tells the runner to run JavaScript code. (Not well-supported.) |
| `GameRunFromGMS2IDE` | Set when a game is launched from a GameMaker IDE using Run/Debug options. |
| `TransparentBackground` | For the GX.games runner, allows the browser canvas to be transparent where nothing is drawn. |
| `WindowsD3DSwapEffectDiscard` | For the Windows runner, reverts the swapchain to an older/legacy swap effect. |

## OptionsFlags

Represents additional engine features in a comma-separated `string`.

Example:
```json
"FullScreen, InterpolatePixels, ShowCursor, EnableCopyOnWrite"
```

All possible features are:
| Name | Description |
| ---- | ----------- |
| `FullScreen` | Start the game in fullscreen. (Mind the uppercase S!) |
| `InterpolatePixels` | Interpolate colors between pixels. |
| `UseNewAudio` | Use a new audio engine/format. |
| `NoBorder` | Make the game window borderless. |
| `ShowCursor` | Display the mouse cursor by default. |
| `Sizeable` | Allow the game window to be resized. |
| `StayOnTop` | Make the game window stay on top. |
| `ChangeResolution` | Allow the game resolution to be changed. |
| `NoButtons` | (Unknown.) |
| `ScreenKey` | Likely allows fullscreen switching. (Not well-understood.) |
| `HelpKey` | (Unknown.) |
| `NoButtons` | (Unknown.) |
| `ScreenKey` | (Unknown.) |
| `HelpKey` | (Unknown.) |
| `QuitKey` | (Unknown.) |
| `SaveKey` | (Unknown.) |
| `ScreenShotKey` | (Unknown.) |
| `CloseSec` | (Unknown.) |
| `Freeze` | (Unknown.) |
| `ShowProgress` | (Unknown.) |
| `LoadTransparent` | (Unknown.) |
| `ScaleProgress` | (Unknown.) |
| `DisplayErrors` | (Unknown.) |
| `WriteErrors` | (Unknown.) |
| `AbortErrors` | (Unknown.) |
| `VariableErrors` | (Unknown.) |
| `CreationEventOrder` | (Unknown.) |
| `UseFrontTouch` | (Unknown.) |
| `UseRearTouch` | (Unknown.) |
| `UseFastCollision` | (Unknown.) |
| `FastCollisionCompatibility` | Enables collision compatibility mode for newer GameMaker games (that is, this reverts behavior to round coordinates in the collision system.) |
| `DisableSandbox` | Mostly disables the savedata/filesystem sandbox. |
| `EnableCopyOnWrite` | Enables array copy-on-write behavior, for newer GameMaker games where it has been disabled by default. |
| `LegacyJsonParsing` | Enables legacy JSON parsing behavior, for newer GameMaker games. |
| `LegacyNumberConversion` | Enables legacy number conversion behavior, for newer GameMaker games. |
| `LegacyOtherBehavior` | Enables legacy `other` keyword behavior in GML, for newer GameMaker games. |
| `AudioErrorBehavior` | Changes behavior of the audio system when errors occur (e.g., whether they should be silently logged or crash), for newer GameMaker games. |
| `AllowInstanceChange` | Enables legacy `instance_change()` (and related functions) in GML, for newer GameMaker games. |
| `LegacyPrimitiveDrawing` | Enables legacy drawing behavior of primitive drawing functions in GML, for newer GameMaker games. |
