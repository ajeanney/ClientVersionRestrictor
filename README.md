# ClientVersionRestrictor

Only accept the Minecraft versions you support: the plugin reads the protocol version every player connects with, through ViaVersion, and kicks the ones outside the range you configured.

## Features

- A minimum and a maximum protocol version in the configuration; leave the maximum at `-1` to only set a minimum.
- Works with every client version ViaVersion accepts, since the check uses the protocol number rather than the version name.
- `clientversionrestrictor.bypass` lets a player, or a whole group, skip the check.
- The kick message is configurable, and the player is kicked a few seconds after joining instead of on the login screen, so they get to read it.

## Requirements

- Spigot 1.16 or newer (built against the 1.20.2 API).
- [ViaVersion](https://viaversion.com/), declared as a hard dependency: it is what tells the plugin which version a client is using.

## Installation

1. Drop the built jar in your server's `plugins/` folder, next to ViaVersion.
2. Start the server once to generate `plugins/ClientVersionRestrictor/config.yml`.
3. Set `minVersion` and `maxVersion` to the protocol numbers you want to accept.

## Configuration

```yaml
kickMessage: "§cYou are using an unsupported version of Minecraft!"
minVersion: 472
maxVersion: -1
```

- `minVersion`: the lowest accepted protocol number.
- `maxVersion`: the highest accepted one, or `-1` for no upper limit.
- `kickMessage`: what the kicked player is told, colour codes included.

Protocol numbers are the ones Minecraft uses on the network: 754 is 1.16.5, 763 is 1.20.1 and 767 is 1.21. The full list is on the [Minecraft Wiki](https://minecraft.wiki/w/Protocol_version).

## Permissions

| Permission | Description |
| --- | --- |
| `clientversionrestrictor.bypass` | Lets the player connect with any version |

## Building

```sh
./gradlew build
```

The jar lands in `build/libs/`.
