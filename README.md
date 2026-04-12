# FAF — Fiojf's Attribute Swap Fix

A Paper 1.21.11 plugin that restores vanilla attribute swapping behavior on servers.

## What is Attribute Swapping?

Attribute swapping ([MC-28289](https://bugs.mojang.com/browse/MC-28289)) is a vanilla Minecraft mechanic where swapping weapons within 1-2 ticks of an attack causes the game to mix attributes from both items — using one weapon's base damage with another weapon's enchantments.

Paper prevents this by forcing equipment updates on player actions. FAF undoes that fix, restoring vanilla behavior.

## How it Works

1. **Disables Paper's `update-equipment-on-player-actions`** at runtime via reflection
2. **Preserves the attack cooldown ticker** across item swaps using NMS reflection, counteracting Paper's cooldown reset
3. **Falls back to temporary attribute modifiers** if the config toggle is unavailable

## Installation

1. Drop `faf-1.0.0.jar` into your server's `plugins/` folder
2. Restart the server
3. Attribute swapping is enabled by default

## Commands

| Command | Permission   | Description                        |
|---------|--------------|------------------------------------|
| `/faf`  | `faf.toggle` | Toggle vanilla attribute swap on/off |

Permission defaults to **op**.

## Config

```yaml
# config.yml
enabled: true
```

## Building

Requires Java 21 and Maven.

```sh
mvn clean package
```

The jar will be in `target/faf-1.0.0.jar`.

## License

[LGPL-3.0-only](LICENSE)
