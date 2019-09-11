# QBeat
A Cross platform mod installer for Beat Saber

Current state is fairly primitive, but does provide an alternative to BeatDrop/ModAssistant on Linux
- Limited functionality - Actions are fairly dumb right now
- Not heavily tested, only test on Linux (/should/ build and run on windows, might break things)
- Just a command line interface at first, gui will come once base actions are implemented

# Mod Setup Walkthrough
QBeat includes everything needed to setup mods on Linux, so no need to download the scripts separately. Either build from source (requires Qt5, ZLIB/minizip), or take a prebuilt version from the releases page

## First Time Setup
These steps should only need to be run once on your machine.
If there's a beat saber update you'll need to re-install mods/patch again but the config and wine setup should only need to be done once.

```
# If QBeat has never been run you'll need to setup the paths. Will be stored in $HOME/.config/gfrancisdev/QBeat.conf
QBeat --config set winePrefix "~/.wine"
QBeat --config set bsProtonDir "~/.steam/steam/steamapps/common/Proton 4.11"
QBeat --config set bsInstall "~/.steam/steam/steamapps/common/Beat Saber"

# Validate that your wine installation is correct
QBeat --validate-wine
# If this fails then there's a command to set things up. This one may take a while so please be patient
QBeat --setup-wine

# List available mods
QBeat --list

# Install mods
QBeat --install "BSIPA"

# Run BSIPA to patch the game (Remember, you need to have run BS once before doing this)
QBeat --patch
```

## Adding More Mods
```
# Once the game is patched you can just pile more mods into the installation
QBeat --install "Perfection Display"
QBeat --install "HTTP Status"
```


# Features
- Installation of mods on Linux, package manager style interface
- Ability to setup wine prefix for running BSIPA
- Ability to apply the other Linux-specific tweaks here
- Ability to patch game with BSIPA
- Config values allow setting steam v oculus, game version, and other parameters. Run QBeat --config get to list variables

# Limitations
- QBeat --install : Will install latest version of a mod and it's dependencies, no checking of current version, will overwrite if already present
- There's no way to list currently installed mods, or verify that a mod is valid (yet)
- There's no way to uninstall mods (yet)
- BSIPA will not be run automatically
- No gui (yet)



If you want to try this feel free, let me know how it goes.

Like all early software this might break your beatsaber installation, delete your files, and make the kittens cry. If you don't know what you're doing ask first, or wait until things are ready :)