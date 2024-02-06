# Template description

This repository contains the starter materials for your thesis in Computer
Science 600 and 610 in Fall 2022  and Spring 2023 academic term. The main
directory of this repository contains the Markdown template for a project that
is designed for use with GitHub Classroom. To learn more about the course
in which these assignments were completed, please refer to the `README.md` file.

The template specifies various settings in the `config.yaml` file included in the
repository. Change the appropriate values under the `Project-specific values`
heading. Changing other values outside of that section may cause the project to
fail to build. **Modify these values at your own risk.**

Author your thesis in the `thesis.md` document using appropriate Markdown
hierarchy and syntax; GitHub Actions will automatically create a PDF from the
`abstract.md` and `proposal.md` files. Consult the `README` of the proposal
repository to learn how to properly build and release this PDFs.

## Citations and references

Including references throughout requires a specific pseudo-Markdown tag, demonstrated
in the following blockquote. (Inspect the `thesis.md` file to see the format.)

> A citation, when included correctly, will appear as it does at the end of this
> sentence. [@plaat1996research]

## Labeling figures

To label a figure (i.e. an image), referencing the image using correct Markdown
will automatically caption the figure:

```markdown
![Label](images/IMAGE_NAME.png)
```

## Labeling tables

To provide a label for a table, write a short caption for the table and prefix the caption
with `Table:` as in the example below:

```
Table: A two-row table demonstrating tables

|Row number | Description |
|:----------|:------------|
|1          |Row 1        |
|2          |Row 2        |
```

## Other template information

Two things specific to this template to also keep in mind:

1. It is your responsibility to remove this description section before building
the PDF version you plan to defend.
2. References _will only appear if cited correctly_ in the text

## Note on `LaTeX` commands

Documents may include specific `LaTeX` commands _in Markdown_. To render these, surround the commands
with markup denoting `LaTeX`. For example:

```
Checkmark character:   $\checkmark$
Superscript character: $^{\dag}$
```

If using a special package not included in the template, add the desired `LaTeX`
package or command/macro to the `header-includes` property in [config.yaml](config.yaml).

Should this package not be included in the environment shipped with this template,
you may also need to add the package to the [GitHub Actions Workflow](.github/workflows/main.yml).

Direct any questions about issues to your first reader.

# Introduction

This chapter describes your completed senior thesis work,
including the overall aims  and the background motivating your research. Whenever
possible, you should use one or more concrete examples and technical diagrams.

It is often useful and necessary to separate the introduction into multiple sections.
Several possible sections are proposed below, you can use these or distribute your
introductory text into sections in another way.

The headings below propose _one way_ you might structure this section of the document.

## Opening

  Game development in the modern day has become more accessible than ever before
with access to game engines like Unity that provide an interface the user can
easily interact with to create polished games [@haas2014history]. Even within the
engines themselves, there are additional tools that can be installed to make the
process of game development even easier through the use of plugins. These plugins can
be imported into most projects and are essentially just pre-made pieces of code that
do something specifically useful to the given project it's installed for. There are
an abundance of plugins with specific functions that could be useful for a wide array
of games, and it's great to see that many game developers create these plugins so that
others can have an easier time entering the game development space. It's no wonder that
there are so many high quality games being released from independent, amateur game
developers when the tools to do so are just a few internet searches away. This project
is an attempt to make game development even more accessible by creating a Unity plugin
to assist with the random generation of maps, specifically in the style of Roguelike
games.

  When it comes to recent trends in the indie game development space, Roguelikes have
been rather popular for several reasons. The first has to do with the core aspects of
the Roguelike genre, one of which is that whenever you lose in the game, you must start
back from the beginning. In most modern Roguelikes, there's some form of progression
over time where you can unlock things to use at the start of a given run through the
game by completing objectives over the course of several runs. This is mostly so that
the gameplay experience doesn't become too frustrating and to save some progress instead
of starting from scratch. The other main element of Roguelikes, and the one this project
is focused on, is that they heavily involve random generation to vary the gameplay
experience. Usually things like enemies, items, and level layouts are randomly generated
so that the player must adapt to the new challenge to succeed.

  The part of Roguelike generation that is key to this project is the randomization of
level layouts, also known as maps. Having random level layouts is one of the simplest
ways of keeping the gameplay super engaging and varying in a Roguelike. For most
Roguelikes, if the environment you had to traverse was the same every time you started a
run, it would feel extremely repetitive after only a short time of playing. While it's
standard for games in this genre to have randomly generated maps, most games play very
differently and necessitate different kinds of maps. Although it is such an important aspect,
it can be very difficult to understand and implement map generation algorithms if you're
unfamiliar with how they operate.

  This is why the software created for this project is a Unity plugin to assist in the
process of random map generation. It takes pre-made rooms created by the user
and places them around an area before connecting each one with hallways to generate
sprawling, dungeon-like maps. The goal isn't just to create a good generation
algorithm, but primarily to make the plugin easy to use so that those unfamiliar
with coding something like it would still have the ability to create the game they
want. In addition, the plugin itself is robust with many options for the user to select
from to specify parts of the generation process. Overall, it's a practical, low effort
way for amateur game developers to more easily create games in the Roguelike genre.

## Current State of the Art

  There are two main ways to generate a map for a game: tile-by-tile generation and
room-and-connector based generation. The tile-by-tile generation essentially creates a
map from scratch by filling every tile in a given area with various objects or enemies
based on the criteria provided to the algorithm. These games must have a specific algorithm
for determining what can and cannot be placed in each tile based on surrounding tiles,
existing tiles, and many other factors. A good example of this generation style is in the
game Spelunky, where you're playing as an explorer trying to find treasures throughout a
series of locations under the earth, with each increasing in difficulty as you explore. The
levels are procedurely generated to have specific enemies and special tiles according to
the aesthetic and design requirements for the current area [@baghdadi2015procedural]. This
generation technique makes sense for the type of environment they're going for, and it
especially makes it feel as though you're exploring a sprawling, expansive mine filled with
dangers that could be around any corner.

![A screenshot from the game Spelunky [@martin2021spelunky]](images/Spelunky-Credit-Blitworks-2%402000x1133.jpg)

  The room-and-connector generation varies a bit from tile-by-tile in that it doesn't go
through every position on the map and determine what can and cannot be there, but instead
takes a set of pre-made rooms that were created before starting and places them randomly
around the permitted generation space before connecting the various rooms to form a
dungeon-like map. This doesn't require anywhere near as complex of an algorithm as the
tile-by-tile generation, but it does need to keep track of the locations of rooms, what's
in them, and check for any overlaps between the rooms and the connectors between them. An
example of this generation style can be seen in the game Enter the Gungeon
[@dodgeroll2016gungeon]. The goal of the game is to get through the five main levels by
exploring the rooms of each map to find loot before challenging the boss and moving to the
next level. Each level in Enter the Gungeon is generated by choosing from a set of rooms
that change each floor and randomly placing them before connecting each one with hallways
on their designated hallway location points. This second type of generation is the one that
this project implements.

![An example of a map generated in the game Enter the Gungeon [@boris2019gungeon]](images/gungeon_castle.png)

## Motivation

  A lot of the motivation for this project stems from two things: the increase in
access to game development software and the lack of this desired tool in the
game development space. With engines being so commonly used to develop games
and countless plugins being readily available for anybody to use, it makes sense
for this tool to exist within the space. Creating more ways for people to get
into game development easier is most often a good thing as it allows more
people to build their ideas. The second main motivating factor is that there currently
just isn't any tool that helps with this type of generation. There are many resources
that discuss map generation and how to create the algorithms that go into them, and
although there are plugins available to assist with tile-by-tile generation, there's no
precedent for helping developers with the room-and-connector generation this software
implements. There are even examples of people online asking about how to perform map
generation similar to that of Enter the Gungeon, so it is very clearly a tool that
people want and would use to help develop games [@night2018generation].

## Goals of the Project

  While the goal of making the plugin was to create an interactive system for generating
maps for Roguelike games, the primary objective while doing it was to make it accessible
for those wildly unfamiliar with how map generation works. This is why the user study
discussed later was conduced the way that it was, because feedback on user interactivity
and ease of use was the most important factor in determining the success of the plugin.
Additionally, the plugin was meant to be versatile, with the ability to generate drastically
different maps depending on the settings toggled by the user. This allows for users to
tailor the plugin to do exactly what they need for any kind of game they're making with this
generation style. It was important that both of these things were implemented in the final
plugin so that it would be well-rounded and easy to use for anyone, making game development
an even more approachable activity for newcomers.

## Ethical Implications

  Although a tool that assists game developers with a fairly specific task doesn't seem as
though it would be able to bring any harm, there are some ethical implications to consider when
it comes to creating a plugin. The primary concern that could be brought up is that creating a
plugin to do the work of a programmer could reduce the number of programmers with specific
expertise that might be hired for this specific kind of task. While there is the potential for
this to occur in the future, the technology used in this project isn't robust enough to warrant
the replacement of human developers quite yet. In addition, one would still generally need
to have an understanding of how map generation works to fully utilize this plugin to the best
of its ability, so it would only be reducing the amount of manual work required of one in that
kind of circumstance.

  A second point that could be brought up is that the reliance on a plugin such as this one
could hinder a game developer's ability to truly understand how their game entirely functions
since the algorithm would already be build for them. This also relates to the previous point,
however, which is that one would need to understand map generation concepts anyway to truly
make best use of this plugin. On top of that, if a game developer ever encounters a situation
in which they can't use this plugin for their map generation, whether there's a specific function
that isn't implemented here or just that they're trying their hand at making their own, they
will need to do the necessary research to build a custom map generation algorithm, meaning they
would now be knowledgable in the field they were previously shortcutting by using this plugin.
So overall, while there are certainly some points to be made about a new plugin cutting down
on the necessity of knowledgable programmers for game development, one plugin alone can't fully
replace the hard work of long-time developers that know how to create the exact algorithm that's
needed.

# Related work

This chapter includes a broad and detailed review of relevant existing work.
The literature review should provide background and context for the thesis work.
The subsections may be organized in whatever manner seems best suited to the material--
chronological, or by topic, or according to some other criteria
(e.g., primary versus secondary resources).

If ethical issues are central to this work, you should also address historical and
contemporary issues or efforts made to address them.

## Preface

  There were many resources encountered when researching this project and some previously
conducted work, so this chapter will go through those articles in order of relevance and
specificity to this project. Some of the early articles are used to discuss concepts that
are essential to understanding how the plugin and underlying algorithms function, where
some of the later ones will be much more focused on a particular aspect of map generation.
Additionally, some resources are only tangentially related to this plugin, but they are
still relevant to map generation and game development very closely and were used when
initially conducting research into the topics, so those will be discussed here as well.

## Unity

  The Unity engine is the piece of software that really allows this plugin to exist in
the first place, so it's important to go over how it functions as well as how it's been
used in the past for similar work. In a statement by David Helgason, one of the former CEOs
of Unity, he stated that it's "a toolset used to build games, and it's the technology
that executes the graphics, the audio, the physics, the interactions, \[and\] the networking"
[@haas2014history]. Unity is the backbone of many different games, allowing so many
developers to get a head start on whatever project they're creating without having to set up
a custom framework themselves. Since it released in 2005, the goal of Unity was to make it
so that amateur game developers could have easy access to powerful tools that helped make
games. Although there has been some controversy in the past year regarding pricing and terms
of service that the company has implemented, it still remains one of the most popular and
easiest engines to start making games with, and it continues to be a foundation of the game
development industry [@unity2023homepage].

  Inside the Unity engine itself, the interface is built so that the user can understand
what is going on without too much trouble by presenting all the necessary windows up front,
such as the asset folders, scene editor, and the object inspector tab. On top of that, the
user is allowed to move around each tab and add any extra ones they might need. Then, their
new layout can be saved to the engine to have a shortcut to it later, allowing experienced
game developers to take full advantage of the interface to customize it to how they like.
Any assets the user needs to use in the game can be added quickly by placing them in the
respective folder within the engine's window, automatically copying that file to the project's
actual assets folder stored within the computer. Once the assets are in the project files,
they can be easily accessed, duplicated, edited, and placed into any scene within the game.
Each scene is essentially the different environments and spaces that a given game takes place
in. A scene is empty when it's first created, but the user can add anything and everything to
the scene that they want. That includes ground, walls, the player character, enemies, items,
buttons, UI elements, and any other objects that a scene might need.

![An empty scene when a Unity project is first created](images/EmptyScene.PNG)

![A Unity scene with a few objects placed around it](images/SceneWithObjects.PNG)

  Any object that is placed into a scene in Unity will have components attached to it that
affect the object in various ways. For most objects, they will have some kind of mesh renderer
and collider so that they can be visualized on the screen within the game, though some objects
are meant to be invisible to the player, like cameras and objects that manage things in a
scene. Another important component that can be attached to objects is scripts, which allow
the user to give an object a chunk of code that will execute under certain conditions. It's
most common for scripts to be written in the C# language for Unity, but the engine also
natively supports C++ and Rust, with many plugins that can be installed to use other languages
as well. Scripts commonly utilize the `Start` function, which makes the code within it run
immediately when the object with the script enters the scene, and the `Update` function,
which runs the code within it every frame the object is active in the scene. There are many
other components that can be added to any given object and most of them can be interacted
with through scripts to best utilize the features of each component, such as the colliders
which can be used to detect when another object has entered or exited the defined collision
zone.

![The inspector view of a cube object with a new script attached \(Left\) and the default code within the new script \(Right\)](images/CubeObjectAndNewScript.png)

  One last important thing to note about Unity objects is that any object within a scene can
be turned into what is called a prefab, which is essentially an object that is saved outside
of the scene itself. This makes it so that the user can create an endless number of copies of
a given object without having to manually copy and duplicate it to another scene. Prefabs also
allow for the instantiation of objects within a scene by spawning them in through a script.
Prefabs generally make the process of developing a game much faster as it cuts down on the
amount of object duplication that would be required otherwise.

## Preliminary Research on Map Generation

  In order to get a better understanding of how map generation functioned, there were a few
resources used near the beginning of this project that cover this topic quite well. In an
article about mixed-initiative level design [@karavolos2015mixed], it discusses how most
game levels are created with an objective in mind, but when generating content in real-time
like many Roguelikes do, it can be difficult to make sure the objective aligns with how the
level is generated so that it feels like it makes sense when playing. One of the examples it
gives of how to do this is through the game Dwarf Quest, which utilizes an action graph of
the intended player experience to generate each individual room. The action graph would
entail the actions the player is meant to take when traversing the dungeon. This graph is
then transformed into a level layout by generating each room based on what the player is
supposed to do next. It's a rather inventive way of tailoring the level generation to result
in the intended player experience and significantly influenced this project's featured
options. Giving the game developer options for more control over how each map can be
tailored to a certain type of gameplay feel was crucial in making a robust plugin that
users can put in their games easily.

  Another article takes a different approach to generation as it utilizes a two-step 
tile-by-tile generation system [@green2019two], but the core concepts it implements are still
very relevant to the way this project was shaped. The two-step process the article focuses
on begins with a layout creator, followed by a game element furnisher. The layout creator
starts with a grid filled with walls, then drills through the walls in the grid to make a
level layout based on the type of drilling method. The game element furnisher takes the level
created by the first step and places objects on various tiles based on the constraints of
each object in each different furnishing method. This approach to level generation is highly
variable depending on the methods used for each step, but it's very clear that some
generation styles cater to certain playstyles compared to others. As an example, it shows in
the data from the article that a type of player that runs through the level as fast as
possible completed the levels most often when the first step in level generation used the
cellular automata method because it created much larger, open spaces that allows the player
to avoid fighting strong enemies more easily. Even though the specific methods used to get
the data in this article didn't impact this project due to its tile-by-tile generation
style, this does reinforce the concept that maps can be generated to incentivize certain
playstyles.

  In another article that leans more towards the generation method used in this project
[@smith2014logical], a similar method is used to that which was used for Dwarf Quest in that
it takes a set of actions it wants the player to do, but combines it with the tile-by-tile
and multi-step generation methods of the previous article. It does this by first establishing
a set of pre-made rooms and hallways that can be placed around the map, so instead of
individually drilling through each tile to create the level, it uses chunks of tiles as
preestablished areas that make for a much more refined and intentional-feeling level.
After creating the map, it then goes in tile-by-tile and places the other objects such
as enemies, treasures, and exits. This makes it so that the space being traversed feels
more developed while keeping the variability of the tile-by-tile generation style. Most
importantly though, this article establishes the use of pre-made rooms being effective
in map generation and shows that they are a useful tool in developing algorithms for it
as it takes some of the load off of the computation while improving the experience for
players.

## Research on Room-and-Connector Generation

  Throughout the research on this project, there were a few sources that directly
inspired the generation method used in the final version and helped in proving the
feasibility of this type of plugin. In an article specifically about connecting rooms
together, it goes over the concept and implementation of generating maps using pre-made
rooms and connecting them to each other through the script [@silva2020procedural]. The
example presented in this article is built using 3D room pieces and shows off several
algorithms for generating maps with this method. The main four algorithms that it shows
are arena, corridor, star, and branch generation. Arena generation is fairly standard,
generating as many rooms adjacent to the currently selected piece as possible, moving to the
next one when all the spaces are full, resulting in a sprawling area filled with rooms.
Corridor generation does the opposite, only generating one piece adjacent to the current one
and moving to the newly generated piece to continue the process, resulting in a single long
path of connected rooms that is fairly linear to traverse. The star method is a combination
of the arena and corridor methods, beginning by generating rooms all adjacent to the starting
room, and then only generating singular paths from each of these extensions to create several
corridor-like paths. Lastly, branch generation starts by using corridor generation to create
one path forward, but then chooses points in the path to create new diverging paths. Each of
these methods provide drastically different types of maps that provide highly varying
gameplay experiences and were crucial features to add as options in this projects
plugin.

  Inside of the previous article, there is a section discussing the exact ways in which
this map generation style is utilized within games like The Binding of Isaac: Rebirth
and Enter the Gungeon, which both use procedural map generation to tremendous success.
Both of them are Roguelikes that use a form of the room-and-connectors method, but in
slightly different ways. The Binding of Isaac: Rebirth makes use of all its rooms being
shaped and sized in a particular way that the maps can fit on a sort of grid system,
meaning every room can be placed perfectly adjacent to one another without worry of
overlap [@mcmillen2014isaac]. Enter the Gungeon is not built in the same way as every
room is varying in size and shape, with the connector pieces varying in location on each
wall depending on the room. This makes the generation algorithm quite a bit more
complicated as it has to connect each room with a hallway to avoid the issue of excessive
overlapping when trying to initially generate a map, but that also means it has to take
each hallway into account along with the rooms themselves. In the previously discussed
post discussing tools for helping with map generation similar to that of Enter the
Gungeon, one of the developers for the game left a comment discussing these exact methods
used for generating the maps within it [@night2018generation]. He details the concept for
having pre-made rooms that are placed and connected to create full maps, but also
discusses how they are generated according to a graph of player actions as well. Combining
these generation tactics to result in a randomized map that also feels intentionally
crafted for the player makes the maps in Enter the Gungeon extremely effective at
providing an entertaining experience for the player. That is why it served at the primary
inspiration and somewhat of a baseline for the generation implemented in this project's
plugin.

# Method of approach

This chapter answers the "how" question - how did you complete your project,
including the overall design of your study, details of the algorithms and tools you
have used, etc.  Use technical diagrams, equations, algorithms, and paragraphs of text
to describe the research that you have completed. Be sure to number all figures and
tables and to explicitly refer to them in your text.

This should contain:

* lists
* with points
* and more points
  * possibly subpoints

For those projects whose implications address social or moral issues (i.e. ethical
standards, causes, effects), you will want to use this section to describe how you
actively mitigated or considered these issues.

## Part 1: The User's Perspective

* This first section will discuss how the plugin is interacted with from the user's end
* There won't be any code involved in this section of the chapter, but it will instead
  focus on what a developer using this plugin will see and work with in the Unity
  interface
* More specifically, this will go over the `MapGenerator` script, the `RoomDataContainer`
  script, the process of making a room, and adding all of the necessary game objects and
  data to the map generator itself

## Part 2: The Algorithm Behind the Interface

* This section is going over exactly what's going on within the scripts and how it's all
  formatted
* The algorithm is very complicated itself and somewhat convoluted in some areas, so good
  diagrams will be needed to explain everything in an understandable fashion

# THIRD CHAPTER ENDS HERE

# Experiments

This chapter describes your experimental set up and evaluation. It should also
produce and describe the results of your study. The section titles below offer
a typical structure used for this chapter.

## Experimental Design

Especially as it pertains to responisble computing, if conducting experiments or
evaluations that involve particular ethical considerations, detail those issues here.

## Evaluation

## Threats to Validity

# Conclusion

Traditionally, this chapter addresses the areas proposed below as sections, although
not necessarily in this order or organized as offered. However, the last section --
"Ethical Implcations" is required for this chapter. See the heading below for more
details.

## Summary of Results

## Future Work

## Future Ethical Implications and Recommendations

Especially as pertains to the public release or use of your software or methods, what
unresolved or special issues remain? What recommendations might you make?

## Conclusions


# References

::: {#refs}
:::
