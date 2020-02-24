To add custom lines of Dialogue, it is important to follow the correct [Mod Structure](https://github.com/EverestAPI/Resources/wiki/Mod-Structure#mod-structure).

## Setting up the Dialogue File

Create a `Dialog` Folder in your Mod's root folder. Example: `Celeste/Mods/MyExampleMap/Dialog`

In this folder you can now create a new `.txt` file. What you name this file depends on to what language you want to add your custom Dialogue. Files for Languages that are already present in Vanilla Celeste:
* `Brazilian Portuguese.txt`
* `English.txt`
* `French.txt`
* `German.txt`
* `Italian.txt`
* `Japanese.txt`
* `Korean.txt`
* `Russian.txt`
* `Simplified Chinese.txt`
* `Spanish.txt`

If a Dialogue String from the currently selected Language is called and a file for that language is not given, Everest defaults the displayed Dialogue to use `English.txt`instead. 

Implementation for custom Languages is the same, however be sure to check what the specific Dialogue file needs to be named.

## Creating Dialogue Strings

In the Dialogue file you set up Strings for Dialog. The game uses these strings to look up what should be displayed in,
for Example, a Message Box.

Example of a String and corresponding Dialogue:
`CH2_THEO_B=
	[THEO left normal]		Sorry about that.
		Don't worry, I won't post that one.`