A guide on how to **download** and **install mods** in [BONELAB](https://store.steampowered.com/app/1592190/BONELAB/) on PC and on Meta Quest.

BONELAB is unusual among the games we write these guides for, because it has **two completely separate modding systems** and they do different jobs:

* **[mod.io](https://mod.io/g/bonelab)** is built into the game. It works on PC and on a standalone Quest, needs no external tools, and covers avatars, maps and spawnable items.
* **[MelonLoader](https://melonwiki.xyz/)** is a PC-only mod loader for code mods, the sort that change how the game actually behaves. Those live on [Thunderstore](https://thunderstore.io/c/bonelab/).

Which one you want depends entirely on what kind of mod you are after. We cover both, and use [Ragdoll Player](https://thunderstore.io/c/bonelab/p/Lakatrazz/Ragdoll_Player/) as the worked example for the MelonLoader side.

[**View Guide On TMC (Recommended Due To Better Formatting)**](https://moddingcommunity.com/blog/how-to-install-mods-in-bonelab/)

## Table Of Contents
* [Requirements](#requirements)
* [Two Systems, Two Kinds Of Mod](#two-systems-two-kinds-of-mod)
* [Installing Mods With mod.io](#installing-mods-with-modio)
    * [From Inside The Game](#from-inside-the-game)
    * [From The Website](#from-the-website)
    * [Quest Notes](#quest-notes)
* [Installing Code Mods With MelonLoader](#installing-code-mods-with-melonloader)
    * [BoneLib](#bonelib)
    * [Using Gale Or r2modman](#using-gale-or-r2modman)
    * [Installing MelonLoader By Hand](#installing-melonloader-by-hand)
    * [Installing Ragdoll Player By Hand](#installing-ragdoll-player-by-hand)
* [Installing With The TMC App](#installing-with-the-tmc-app)
* [Multiplayer With Fusion](#multiplayer-with-fusion)
* [Confirming Your Mods Loaded](#confirming-your-mods-loaded)
* [Linux](#linux)
* [Uninstalling](#uninstalling)
* [Troubleshooting](#troubleshooting)
* [Conclusion](#conclusion)
* [See Also](#see-also)

## Requirements
For mod.io content:

* **BONELAB** on any supported platform, including standalone Quest 2, Quest 3 and Quest Pro.
* A free [mod.io](https://mod.io/) account.

For MelonLoader code mods, additionally:

* A PC running **Windows 10** or later, with BONELAB on Steam or through the Oculus PC app. Linux via Proton works with an extra launch option.
* [Microsoft Visual C++ 2015-2019 Redistributable, 64 bit](https://aka.ms/vs/16/release/vc_redist.x64.exe).
* [.NET Desktop Runtime 6.0, x64](https://dotnet.microsoft.com/en-us/download/dotnet/6.0). BONELAB is Il2Cpp and MelonLoader requires this.
* A few GB free if you plan to collect avatars and maps, which are not small.

## Two Systems, Two Kinds Of Mod
Getting this distinction straight up front saves a lot of time.

| | mod.io | MelonLoader |
| --- | ------ | ----------- |
| Where you get it | Built into the game, or [mod.io](https://mod.io/g/bonelab) | [Thunderstore](https://thunderstore.io/c/bonelab/) |
| Platforms | PC and standalone Quest | PC only |
| What it handles | Avatars, maps, spawnable items, made with the BONELAB SDK | Code mods that change game behaviour |
| Needs extra tools | No | Yes, MelonLoader and usually BoneLib |
| Example | A custom avatar or an extra level | Ragdoll Player, Fusion multiplayer |

So if you want to play as a different character or load a community map, mod.io is the whole answer and you never need to touch a file. If you want to change how the game works, that is MelonLoader territory and Quest players are out of luck.

**NOTE** - Quest standalone cannot run MelonLoader. Nothing works around that. Quest players connected to a PC via Link or Air Link are running the PC build, so they are on the PC side of this table.

## Installing Mods With mod.io
### From Inside The Game
This is by far the easiest modding experience of any game in this collection.

1. Start BONELAB and load into the **Hub**.
2. Find the mod.io terminal in the Hub and interact with it.
3. Sign in to your mod.io account. The game gives you a code to enter at [mod.io/connect](https://mod.io/connect) from a phone or a PC browser, which saves typing a password with VR hands.
4. Browse or search the catalogue.
5. Select a mod and install it. It downloads straight onto the device.

Installed avatars appear at the avatar terminals, maps appear in the level list, and spawnables appear in the spawn gun catalogue. There is no folder to find and nothing to launch differently.

### From The Website
You can also queue things up on a computer.

1. Sign in at [mod.io/g/bonelab](https://mod.io/g/bonelab).
2. Find a mod and click **Subscribe**.
3. Start BONELAB while signed in to the same account.

Subscriptions sync down on launch. This is much more comfortable for browsing than doing it inside a headset.

**TIP** - Subscriptions follow your account, not your device. Subscribe on your PC and the same mods appear on your Quest, which is genuinely handy if you play on both.

### Quest Notes
Storage is the constraint here. Avatars and maps are real Unity content and they add up quickly on a headset that also has everything else on it. Unsubscribing from inside the game removes the files.

Quest also runs on a mobile GPU. Maps built for PC will run, but not always well, and the mod description usually says whether Quest is supported. Where a mod has separate PC and Quest builds, mod.io serves the right one automatically.

## Installing Code Mods With MelonLoader
This is the PC-only half.

### BoneLib
Nearly every BONELAB code mod depends on [BoneLib](https://thunderstore.io/c/bonelab/p/bonelib/BoneLib/), the shared library the scene is built on. Ragdoll Player is no exception.

There is one wrinkle worth knowing about. BoneLib used to be published under the `gnonme` namespace and has since moved to a `bonelib` one. The old [gnonme/BoneLib](https://thunderstore.io/c/bonelab/p/gnonme/BoneLib/) package still exists and now just depends on the new one, so older mods that reference the old name keep working. If you see both in your installed list, that is why, and it is not a problem.

Mod managers handle all of this. It only matters if you install by hand.

### Using Gale Or r2modman
1. Download [Gale](https://thunderstore.io/c/bonelab/p/Kesomannen/GaleModManager/) or [r2modman](https://thunderstore.io/c/bonelab/p/ebkr/r2modman/) and install it.
2. Open it and select **BONELAB**.
3. Let it detect your install, or point it at the game folder.
4. Search for **Ragdoll Player** and click **Install** or **Download with dependencies**.
5. MelonLoader and BoneLib come along automatically.
6. Launch with **Launch game (modded)** or **Start modded**.

Starting BONELAB from Steam or the Oculus app instead runs it without mods.

### Installing MelonLoader By Hand
Find your game folder first. On Steam, right-click **BONELAB**, then **Manage** and **Browse local files**:

```
C:\Program Files (x86)\Steam\steamapps\common\BONELAB
```

The easy way is the [MelonLoader Installer](https://github.com/LavaGang/MelonLoader.Installer/releases/latest/download/MelonLoader.Installer.exe). Run it, pick BONELAB from the detected games list, choose a stable version, and click **Install**. If BONELAB is not detected, use **Add Game Manually** and point it at `BONELAB.exe`.

To do it fully by hand:

1. Download [MelonLoader.x64.zip](https://github.com/LavaGang/MelonLoader/releases/latest/download/MelonLoader.x64.zip).
2. Extract the `MelonLoader` folder into the BONELAB folder.
3. Extract `version.dll` into the BONELAB folder as well.
4. Run the game once and quit, which creates the `Mods` and `UserData` folders.

**WARNING** - Do not enable nightly builds in the installer. They are built from the latest commits and break regularly. Mods are built against stable releases.

### Installing Ragdoll Player By Hand
1. Download [BoneLib](https://thunderstore.io/c/bonelab/p/bonelib/BoneLib/) and [Ragdoll Player](https://thunderstore.io/c/bonelab/p/Lakatrazz/Ragdoll_Player/) with **Manual Download**.
2. Extract both.
3. Copy each `.dll` into the `Mods` folder in your BONELAB directory.

MelonLoader mods go in `Mods`, not in a `plugins` folder. If you are coming from a BepInEx game, this is the layout difference to remember.

Ragdoll Player writes a config on first run under `UserData`, where you can set the input that triggers the ragdoll.

## Installing With The TMC App
There is a third route worth knowing about, though it only applies to the MelonLoader half of this guide. [The TMC App](https://moddingcommunity.com/tmc-app) is our own mod manager and server browser, with one-click installs and **sandboxes**: named mod profiles per game, each with its own load order and deployment method, switchable with nothing re-downloaded.

**BONELAB is not in its supported games list yet.** Adding a game means four JSON files rather than code, so it is not a large job.

Two things to be clear about. The app would only ever manage **code mods**; mod.io content is handled inside the game and no external tool is going to change that. And **the app is in very early development**, which its own README states plainly. Much of it is only partially tested, so use it next to Gale rather than in place of it for now. If you try it, we would really like to hear how it went.

It is **open source** under GPL-3.0 at [github.com/modcommunity/tmc-app](https://github.com/modcommunity/tmc-app). Bug reports and feature requests belong in [the issue tracker](https://github.com/modcommunity/tmc-app/issues), pull requests are welcome, and the repository documents the per-game format if you want to add BONELAB support yourself.

Installing it:

* **Linux**: one line, no root and no package manager.

```bash
curl -fsSL https://raw.githubusercontent.com/modcommunity/tmc-app/main/scripts/install.sh | sh
```

* **Windows**: the `setup.exe` or `setup.msi` from the [releases page](https://github.com/modcommunity/tmc-app/releases). There is a portable build too, though it does not register the launcher entry or the `tmc://` link handler.
* **macOS**: the `.dmg` from the same releases page.

## Multiplayer With Fusion
Worth mentioning because it is the mod most people eventually want. [Fusion](https://thunderstore.io/c/bonelab/p/Lakatrazz/Fusion/) adds full multiplayer to BONELAB and is one of the most downloaded mods for the game by a wide margin.

It is a MelonLoader mod, so PC only, and everybody in a session needs it installed. Because it also has to agree on which mod.io content everyone has, there is a companion mod, [ModioModNetworker](https://thunderstore.io/c/bonelab/p/notnotnotswipez/ModioModNetworker/), that syncs mod.io avatars and maps between players in a session.

Install Fusion the same way as anything else on the Thunderstore side, and share a mod manager profile with whoever you are playing with.

## Confirming Your Mods Loaded
**mod.io content:** just look. Avatars appear at the avatar terminals, maps in the level select. If something you subscribed to is missing, check you are signed in to the same account in-game.

**MelonLoader mods:** a console window opens next to the game and prints a line per mod as it loads, with name, version and author. The full log is written here:

```
BONELAB\MelonLoader\Latest.log
```

That log is the first thing to check when a mod does not work, and the first thing anyone helping you will ask to see.

## Linux
BONELAB runs through Proton. MelonLoader needs a DLL override, so set the game's Steam launch options to:

```
WINEDLLOVERRIDES="version=n,b" %command%
```

That is `version`, not `winhttp`. MelonLoader and BepInEx use different hook DLLs and mixing up the launch options is an easy mistake to make.

There is also a [Linux build of the MelonLoader installer](https://github.com/LavaGang/MelonLoader.Installer/releases/latest/download/MelonLoader.Installer.Linux). Gale and r2modman set the override for you when you launch through them.

mod.io content needs nothing special on Linux, since it is handled entirely inside the game.

## Uninstalling
**mod.io:** unsubscribe in-game or on the website. The files are removed from the device.

**A single MelonLoader mod:** uninstall it in your mod manager, or delete its `.dll` from the `Mods` folder.

**MelonLoader entirely:** delete the `MelonLoader` folder, `version.dll`, `Mods` and `UserData` from the game directory, or use the uninstall option in the MelonLoader Installer. Steam's file verification will not do this, since none of it came from Steam.

## Troubleshooting
**mod.io terminal says I am not signed in.** Sign in again through [mod.io/connect](https://mod.io/connect) with the code the game shows you.

**Subscribed mods are not appearing.** Restart the game. Subscriptions sync on launch rather than live.

**Quest is out of storage.** Unsubscribe from what you are not using. Maps and avatars are large.

**No MelonLoader console at all.** MelonLoader is not loading. Check `version.dll` sits directly beside `BONELAB.exe`, and that you launched through your mod manager.

**MelonLoader loads but a mod does not.** Read `MelonLoader\Latest.log`. A missing or mismatched BoneLib version is the most common cause by far.

**MelonLoader crashes at startup.** Install the [VC++ 2015-2019 x64 redistributable](https://aka.ms/vs/16/release/vc_redist.x64.exe) and the [.NET Desktop Runtime 6.0 x64](https://dotnet.microsoft.com/en-us/download/dotnet/6.0).

**A Thunderstore mod does nothing.** Check it is actually a BONELAB mod. Some packages are cross-listed with BONEWORKS, and BONEWORKS mods depend on ModThatIsNotMod rather than BoneLib.

**Everything broke after an update.** Stress Level Zero patches break MelonLoader mods. Empty the `Mods` folder to confirm the game runs clean, then wait for authors to rebuild.

## Conclusion
The decision that matters is which system you need. Avatars, maps and spawnables are mod.io, they work on Quest, and you install them without leaving the game. Code mods are MelonLoader, they are PC only, and a mod manager like Gale makes them a two-click job.

If you are on a standalone Quest, mod.io is the whole story, and it is a good one.

If you have a moment to spare, the [TMC App](https://github.com/modcommunity/tmc-app) is open source, very early in development, and feedback on it would be much appreciated.

## See Also
* [BONELAB on mod.io](https://mod.io/g/bonelab)
* [BONELAB on Thunderstore](https://thunderstore.io/c/bonelab/)
* [MelonLoader Wiki](https://melonwiki.xyz/)
* [BONELAB Modding Discord](https://discord.gg/BONELAB)
* [BONELAB Wiki](https://boneworks.fandom.com/wiki/BONELAB)
* [TMC App](https://github.com/modcommunity/tmc-app)

We keep this guide as current as we can, but the game, mod.io and MelonLoader all change independently. If you spot an instruction that no longer matches what you are seeing, please report it or open a [pull request](https://github.com/modcommunity/how-to-install-mods-in-bonelab/pulls) on this guide's GitHub repository.

Join our [Discord server](https://discord.moddingcommunity.com) if you have any questions or want help with anything modding related!
