---
# Minecraft JE Datapack Guide
---
#### What is this datapack for?
This datapack template for Minecraft Java Edition will eventually server as a
full tutorial for new datapack developers with the intention to help teach more
players how to build datapacks!

As a new self-taught datapack developer for Ragnarok Rebirth, I've quickly
learnt how fun and entertaining developing datapacks can be. I aim to
progressively update this public template over time, with multiple `README.md`
files to guide users to an understanding of how datapacks work within the
datapack itself, while also providing useful tools and other resources where
possible.

This file will lay out the basics needed to understand how this *(and generally*
*others)* datapack works. More detailed `README` files will appear within
different folders

**Useful links and Command Generators:**
1. [Minecraft Fandom Wiki: Commands](https://minecraft.fandom.com/wiki/Commands "A place to start for detailed descriptions of command and console use")
2. [Misode Generator](https://misode.github.io "Loot tables, Advancements, Custom Items/Mobs etc.")
3. [MC Stacker](https://mcstacker.net/versions.php "The most useful tool ever for Loot tables, Advancements, Custom Items/Mobs etc.")
4. [Advancement Datapack Generator ](https://advancements.thedestruc7i0n.ca "Allows you to geneate a datapack for custom advancements")

### Support Me!
This is not necessary, but it would go a long way in supporting me and motivating
me to continue updating and improving this datapack tutorial! *(Perhaps in the*
  *future with more support I may even create a video tutorial)*

<a href="https://www.buymeacoffee.com/Fackles"><img src="https://img.buymeacoffee.com/button-api/?text=Buy me a coffee&emoji=☕&slug=Fackles&button_colour=7808b5&font_colour=ffffff&font_family=Comic&outline_colour=ffffff&coffee_colour=FFDD00"></a>

Alternatively you can support my other joint projects like [**Ragnarok Rebirth**](https://ragnarok-rebirth.com)!

#### What is Ragnarok Rebirth?
*(Shameless plug.. but I kind of have to ;P )*

Ragnarok Rebirth (*nicknamed Raggy by myself and staff*) is a Semi-Survival PvE
Minecraft Server with optional Quests and other RPG features that are being
added over time. **This server is only on Minecraft Java Edition**, but we hope
to support Bedrock players in the future!

[**Website:** https://ragnarok-rebirth.com](https://ragnarok-rebirth.com)

**Server-ip:** `play.ragnarok-rebirth.com`

[**Discord:** https://discord.gg/hJ3zEaP](https://discord.gg/hJ3zEaP)

---
## Initialisation
---
### Where do I put this datapack?
**Datapacks must be downloaded as a `.zip` file** *(this can be done using the*
*green button at the top of the repository)*. The location to place these will
change for singleplayer and multiplayer worlds.

**For singleplayer worlds**, you find the world save in your `\.minecraft`
folder. For example:
```
C:\Users\<user>\AppData\Roaming\.minecraft\saves\<world_name>\datapacks
```

**For multiplayer/server worlds**, you will find the `\datapacks` folder in the
`\world` folder of your server directory. For example:
```
\world\datapacks
```
Place the `.zip` folder in here,
and the `.zip` folder should do the rest of the work so long as it is set up
correctly!

If the datapack does not load after an update of Minecraft, first check the
`pack.mcmeta` file which tells the game what type of file it is reading. As of
1.17 the `"pack_format:"` value must be `7`. This will change w/ future updates.
```
{
	"pack": {
		"pack_format": 7,
		"description":
	}
}
```
*(`"description":` must have a JSON string for text to be viewed in-game)*

If this is correct, then check the server console to see which file is not being
read correctly, usually this might be due to a missing character i.e. a comma,
or some type of bracket or it could be due to the permission level function
files have. This permission can be found in your `\server.properties` file.

The permission level for function files can be changed in the `\server.properties`
file, get the Admin Team to sort that out for you ;)

Datapacks will either load on a world or server restart or you can manually load in
a datapack after placing it in the correct folder using the `/datapack` command
in the in-game or server console


---
### Advancements
---
Advancements is the Java Edition equivalent to Achievements/Quests in game,
which are usually set to be complete once but with a bit of trickery you can
allow them to be repeatable!

Advancements must be a `.json` file, otherwise it will not be read correctly
and thus the correct syntax must be used.

Advancements can be granted/revoked using the below  in-game command example;
```
/advancement <give/revoke> <player/selector> <projectname>:/folder/files
      e.g. /advancement give DarkyyBoi minecraft:story/root
            gives DarkyyBoi the "Minecraft" advancment for crafting a crafting
            table
```
*Pressing TAB will autocomplete the command, giving a better idea on the*
*options provided.*

[Minecraft Fandom Wiki: Advancements](https://minecraft.fandom.com/wiki/Advancement/JSON_format)

---
### Functions
---
When calling a function, getting the namespace and file path is vital!!!
For vanilla minecraft, the main namespace is:
```
minecraft:
```

To call a function, similar to targeting an Advancement you use the following
in-game command;
```
      /function minecraft:folder/file
```
These can also be scheduled to have a delay or even loop functions. However,
scheduling a function will execute the commands as the server console so keep
this in mind if you are using commands that target entities/players;
```
      /schedule function <function> <time> [append|replace]
      /schedule function clear <function>
```
**Function files** are the key feature that allows datapacks to be capable of
crazy things. They allow us to run in-game console commands outside of the game
and outside of an external server console. They can also loop themselves and
will run any command inside the function file simultaneously in one game tick.

[Minecraft Fandom Wiki: Functions](https://minecraft.fandom.com/wiki/Function_(Java_Edition))
