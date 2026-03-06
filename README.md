# Hi!

This is a fork of [SmartCMD's LCE Repo](https://github.com/smartcmd/MinecraftConsoles) with some custom things.
I've removed anything I don't find important from the README. So everything here I believe is what should be needed to use the fork properly.
## Multiplayer

Basic LAN multiplayer is available on the Windows build

- Hosting a multiplayer world automatically advertises it on the local network
- Other players on the same LAN can discover the session from the in-game Join Game menu
- Game connections use TCP port `25565` by default
- LAN discovery uses UDP port `25566`

This feature is based on [LCEMP](https://github.com/LCEMP/LCEMP/)

### Launch Arguments

| Argument           | Description                                                                                         |
|--------------------|-----------------------------------------------------------------------------------------------------|
| `-name <username>` | Sets your in-game username                                                                          |
| `-server`          | Launches a headless server instead of the client                                                    |
| `-ip <address>`    | Client mode: manually connect to an IP. Server mode: override the bind IP from `server.properties`  |
| `-port <port>`     | Client mode: override the join port. Server mode: override the listen port from `server.properties` |

Example:
```
Minecraft.Client.exe -name Steve -ip 192.168.0.25 -port 25565
```

Headless server example:
```
Minecraft.Client.exe -server -ip 0.0.0.0 -port 25565
```

The headless server also reads and writes `server.properties` in the working directory. If `-ip` / `-port` are omitted in `-server` mode, it falls back to `server-ip` / `server-port` from that file. Dedicated-server host options such as `trust-players`, `pvp`, `fire-spreads`, `tnt`, `difficulty`, `gamemode`, `spawn-animals`, and `spawn-npcs` are persisted there as well.


## Build & Run

1. Install Visual Studio 2022
2. Clone the repository
3. Open the project by double-clicking `MinecraftConsoles.sln`
4. Make sure `Minecraft.Client` is set as the Startup Project
5. Set the build configuration to **Debug** (Release is also OK but has some bugs) and the target platform to **Windows64**, then build and run
