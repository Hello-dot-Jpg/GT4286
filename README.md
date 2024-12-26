# Retro Arcade Game Console (GT-4286)

Hopefully I will get my thoughts together and write up what I have learnt about this product. Backup your SD card before reading on.

## For now, you can find:

1. [dat](./dats/) files for the FBNeo emulator.

2. a [screenshot](./img/fbneo-hexedit-fix-p1-r-and-l-buttons.png) of a couple of bytes to patch to enable the P1 R and P1 L buttons to work in the FBNeo emulator. 
This screenshot show the changes to be made to /emus/fbneo/fbneo and assume that the file SHA-256 hash of the file is 24B4026764C6B8F218D56222A534EDB3D21210A2C8FCDEE8A5F96505D6B85E9F
If your file has a different hash then please don't perform this edit.

3. a [remap](./sdcard_tweaks/keyremap) file for the (patched) FBNeo emulator that orders the 6 buttons (of each player) correctly for Street Fighter 2 (maybe more).

4. some [information](./sdcard_tweaks/roms/MAME/output/) extracted from the running system

## In the future I hope to show how to:

1. Use a program to refresh the /game.db sqlite db

2. delete the built in roms and images and place your own in the /roms sub folders and then rebuild the game.db index doing away with using the /download folder (see issues below for why)

3. Fix the issue of FBNeo arcade games being listed as their cryptic (upto) 8 character rom names and give them human readable names.

3. replace the mame emulator (because it is an exact dupe of the fbneo emulator) with a script that can run other scripts to extract information from the running system

4. improving some of the menu wordings by editing:
    * /tr/en_US.json
    * /menu/2/menubg*.png


## Some issues with the stock console:

* MAME is shown as a separate emulator but it is just a copy of the FBNeo (aka FBA) emulator. Let's repurpose it.

* If you add roms to the appropriate emulator sub dir in /downloads, duplicate entries for some games might appear after saving a game and rebooting the console. This is because while most emulators save their game state in the emulator folder, some emulators eg GB, GBC, MD save their state in the rom folder and next time the console is rebooted it will rescan the download folder and add a non working entry to the list.

* FBNeo emulator (and it's clone MAME) have a misconfiguration which means that the Player 1 L and R buttons have no effect. (fixable by patching emulator and adding a keyremap files)

* FBNeo games are listed as their cryptic rom .zip file name which is ugly by comparison to the other emulators which can have nice human readable name. (See page 10 in the [manual](https://media.jaycar.com.au/product/resources/GT4286_manualMain_130153.pdf) for an example of this). Let's do something about this.