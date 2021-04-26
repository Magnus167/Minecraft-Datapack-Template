---
## Minecraft JE Advancements Guide
---
Advancements are the Java Edition equivalent of Achievements/Quests in game,
which are usually set to be complete one time only but with a bit of trickery you can
allow them to be repeatable!

Advancements must be a `.json` file, otherwise it will not be read correctly
and thus the correct syntax must be used:
[Minecraft Fandom Wiki: Advancements](https://minecraft.fandom.com/wiki/Advancement/JSON_format)

Advancements can be granted/revoked using the below  in-game command example;
```
/advancement <grant/revoke> <player/selector> <projectname>:/folder/files
```
*Pressing TAB will autocomplete the command, giving a better idea on the*
*options provided.*

For  example `/advancement grant DarkyyBoy only namespace:creator` gives DarkyyBoi the
"DarkyyBoy/Fackles" advancement in the `\namespace\advancements\creator.json`
file which I have set up to show I made this advancement tab:

![Introductory Advancements](images\Adva101+Creator.png)

This is the beginning of what is called the "Advancement Tree", and has its own
tab like the Vanilla Minecraft Advancements have. The icon and title of the tab
is based on the icon and title chosen in the `root.json` advancement. This does
not have to be named `root.json` but majority of the time developers use this as
it is easier to reference in a namespace.

---
#### Naming Advancements
---
Minecraft advancements have 2 seperate names:
1) **Advancement Name;** what we would fill in the `"title":` field of the `.json`
file.
2) **Namespaced ID;** what developers will regularly call back to time and time again,
which also applies to functions.

It would be smart to think how you name your files and folders, as this becomes
very important later on and *especially* when creating large datapacks, though
usually datapacks are relatively small.
