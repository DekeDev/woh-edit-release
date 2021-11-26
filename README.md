# WOHEdit
Event Editor for **WORLD OF HORROR**

This is a public repository for public builds of *WOHEdit* only. The source code for this software is currently not publically available (and may never be, since I honestly *really* don't want someone to see my bad spaghetti code).

## About
This little software is meant as a handy little tool to give you a WYSIWYG experience while creating and editing **WORLD OF HORROR** event cards. 
This was mainly created as a little toy for myself, but I figured I might as well publically release this anyway.
Depending on how mod support for WOH evolves, the tool *might* get expanded into allowing to edit encounters, characters and mysteries as well.

## Download
You can find the downloads [right here on the Release page](https://github.com/DekeDev/woh-edit-release/releases)

## How to use
The first thing you should to is to click the **[SET MOD PATH]** button at the top to select your custom folder inside your WOH installation folder. Generally:
`Steam/steamapps/common/WOH/custom`
The program expects all data it loads being inside this `custom` folder, although you should be able to utilize as many sub-folders as you want to organize your events and images.

After that is done, you can start creating your events! There's **6** different menus:
* [Top Menu](https://github.com/DekeDev/woh-edit-release#top-menu)
* [Card View](https://github.com/DekeDev/woh-edit-release#card-view)
* [Base Settings](https://github.com/DekeDev/woh-edit-release#base-settings)
* [Option Settings](https://github.com/DekeDev/woh-edit-release#option-settings)
* [Nav Menu](https://github.com/DekeDev/woh-edit-release#nav-menu)
* [Editor Options](https://github.com/DekeDev/woh-edit-release#editor-options)

## Top Menu
### New Event
Allows you to create a new event card.
### Load Event
Load an existing event card. Make sure that the card you'd like to load is inside the `custom` folder.

**Important Info**: While the editor will do error checking and sanitizes most variables, I can't guarantee that it'll catch *everything*. So be aware of that when loading broken/janky event files.
### Save Event
Save the current event. The filename will be generated from the event name and will be saved to the `custom` folder automatically. 
For example: `custom/evt_thisisacustomevent.ito`
### [SET MOD PATH]
See above
### [?]
Open this readme
### Palette Selector
Using the arrows you can switch through all available palettes from the actual game. This will allow you to preview your artwork with different palette configurations. Additionally using the **2-Bit/1-Bit** button, you can switch between 2-Bit and 1-Bit display modes. 

## Card View
### Event Name
Click the Event Name to enter the name of your event. You won't have to manually apply your changes, just type away. This field is limited to `65` characters for now.
### Event Image
Click on the image field to select the image you'd like to use for your event. This requires the `Mod Path` to be set beforehand. 
Event Images come in two sizes:
* `195 x 164 px`: normal event images
* `506 x 220 px`: full-size event images

The editor will automatically crop images that are greater than those two dimensions. The editor will also automatically switch to full-size (or `"big"` mode as it's called in the actual file) depending on the image dimensions.

To create 2-bit artwork you can use the following base palette for your image. 

![enter image description here](https://raw.githubusercontent.com/DekeDev/woh-edit-release/96b04e12022e3b6bfcbdc974e205d9b2fb23820a/woh_2bit_palette.png)

This is the same one that is used by WOH, so it should be accurate when looking at your event in-game.
### Flavour text
Using this field you can edit the flavour texts for your event and the different option paths. 
You don't have to input any special characters for newlines, since those are handled by the editor on export. Additionally, when editing option path flavour texts, the stat checks and prizes/penalties will automatically be added after entering your text. 
If your text goes out-of-bounds that's generally "fine" although the preview in WOHEdit will not be 100% accurate to the actual output in WOH due to differences in text rendering.
### Option buttons
Clicking on the option buttons will open a small editor to edit the button contents. When you've entered your text, press `Enter` to apply it to the button.
Button texts can also go out-of-bounds, but again: in that case, the preview is likely not accurate to the actual game.

## Base Settings
### Location selector
With this you can set the location your event should spawn in. This is either globally, one of the Shiokawa locations or globally, but limited to a specific OLD GOD.
### Set Event Info
This will open an editor where you can set some miscellaneous info for your event:
* Your author name
* Your contact (like Twitter, etc.)
* A short description for the event that is shown in the WOH mod menu
### Wavy image
Activate this to use the `wavy` effect for your event image. Works on normal and full-sized images. With the `SPD` input, you can set the speed of the effect.
The wavy effect in WOHEdit is just an approximation of the shader WOH uses. It's probably not 100% accurate, but should give you a good idea on how the effect looks on your image in-game.
### Number of Options
Sets the number of options available to the player (1 to 3).
### Test selector
With this you can set the skill checks for each option. 
* **Story**: this check will always succeed. You can still edit failure states for story checks, but those will do nothing in-game
* **Strength, Dexterity, Perception, Knowledge, Charisma, Luck**: will check the corresponding stat using normal rules
* **Funds1, Funds2**: will only succeed if you have **1** or **2** funds respectively.

## Option Settings
This menu will switch depending on which option (`A`/`B`/`C`/) and path (`SUCCESS`/`FAILURE`) you've selected in the **Nav Menu**. At the top of the menu you will always see which option/path is currently selected.
### Prize
Here you can select the `"prize"` a player will get on the selected path.
* **Stamina, Reason, Doom, Experience, Funds**: will increase/decrease the corresponding stat
* **Injury, Curse, Ally**: will give the player a random injury, curse or ally
* **Item**: will give the player a specific item
* **Spell**: will give the player a random or specific spell
* **Itempool**: will give the player a random item from a specific item pool
### Number
Depending on the selected `Prize` the `Number` menu changes. It allows you to set stat changes or specify given items, spells or item pools.
* **Unknown Items and Spells**: Items and Spells marked with a **`[!]`** are present in the game, but have unknown uses. Few of them work, many of them crash the game, some do nothing at all. I added those items for the sake of completeness, but be aware that using them in your mods is probably a bad idea for now.
* **Spell Prizes**: Even though documented, right now it's not possible to actually get specific spells even if selected. You will always get a random spell. Unfortunately, this is likely nothing I can fix on my side, so we just have to see if future updates to WOH will fix this.
### EX Prize
These will be given to the player in addition to the normal prizes. Works as above, although only **Stamina, Reason, Doom and Experience** are available for this one. You *can* set an `EX Prize` without setting a normal `Prize` and it is supported in-game, though not really intended (or sensible).
### EX Number
Same as the `Number` menu above, but for the selected `EX Prize`.
### Effect
This will allow you to show one of two full-screen effects - **Bloodsplat** and **Whiteflash** - to play when the player reaches this specific path.

## Nav Menu
This menu will allow you to navigate through your event paths.
* **Base**: brings you to the beginning of the event
* **Success**: brings you to the success path for options `A`/`B`/`C`
* **Failure**: brings you to the failure path for options `A`/`B`/`C`

## Editor Options
### Sound
Enables/Disables the keyboard clicking sounds in-editor
### Window Size
Scales the window up or down, not exceeding your maximum screen dimensions.

## Closing Words
Aaaaand that's all for now! I hope at least someone will find this little tool useful for creating new and amazing custom events. The tool is probably a bit janky and has some weird quirks due to my spaghetti code, but it hopefully gives you an **accurate enough** representation of what your event looks like in-game without having to fiddle with text files all the time.
And if this tool gets replaced by an in-game editor, so be it - it was still a fun experience nevertheless.

If you find anything wrong with WOHEdit, please let me know in the Issues tab, thanks!

~*AGrumpyFox*
