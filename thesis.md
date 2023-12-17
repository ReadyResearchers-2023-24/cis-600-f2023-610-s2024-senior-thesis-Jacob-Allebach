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
easily interact with to create polished games. [@haas2014history] Even within the
engines themselves, there are additional programs that can be installed to make the
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
differently and necessitate different kinds of maps. The caveat with this being such
an important aspect, however, is that understanding and implementing map generation
algorithms can be difficult if you're unfamiliar with how they operate.

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
the aesthetic and design requirements for the current area. [@baghdadi2015procedural] This
generation technique makes sense for the type of environment they're going for, and it
especially makes it feel as though you're exploring a sprawling, expansive mine filled with
dangers that could be around any corner.

  The room-and-connector generation varies a bit from tile-by-tile in that it doesn't go
through every position on the map and determine what can and cannot be there, but instead
takes a set of pre-made rooms that were created before starting and places them randomly
around the permitted generation space before connecting the various rooms to form a
dungeon-like map. This doesn't require anywhere near as complex of an algorithm as the
tile-by-tile generation, but it does need to keep track of the locations of rooms, what's
in them, and check for any overlaps between the rooms and the connectors between them. An
example of this generation style can be seen in the game Enter the Gungeon.
[@dodgeroll2016gungeon] The goal of the game is to get through the five main levels by
exploring the rooms of each map to find loot before challenging the boss and moving to the
next level. Each level in Enter the Gungeon is generated by choosing from a set of rooms
that change each floor and randomly placing them before connecting each one with hallways
on their designated hallway location points. This second type of generation is the one that
this project implements.

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
people want and would use to help develop games.

## Goals of the Project

  While the goal of making the plugin was to create an interactive system for generating
maps for Roguelike games, the primary objective while doing it was to make it accessible
for those wildly unfamiliar with how map generation works. This is why the user study
discussed later was conduced the way that it was, because feedback on user interactivity
and ease of use was the most important factor in determining the success of the plugin.
Additionally, the program was meant to be versatile, with the ability to generate drastically
different maps depending on the settings toggled by the user. This allows for users to
tailor the plugin to do exactly what they need for any kind of game they're making with this
generation style. It was important that both of these things were implemented in the final
program so that it would be a well-rounded plugin that is also easy to use for anyone, making
game development an even more approachable activity for newcomers.

## Ethical Implications

This document requires that you discuss the ethical implications of your work -- no
matter how benign you consider the outcome of your project. As several major studies
of ethical issues in computer science assert: _no project is completely value-neutral_.

To assist you in elaborating on these issues, the following areas are topics you might
consider addressing. You do not need to address all of them.

* Information Privacy
* Information Accuracy (e.g. can contain reliability)
* Potential Misuse (e.g. computer crime, unintended consequences)
* Second- or Third-Party Risk (e.g. safety)
* Data Collection Issues (e.g. issues inherent in collecting data)
* Algorithmic or Data Bias
* Potential Power Difference / Social Imbalance / Issues in Equity

In addition, reflect on ways that the above harms can be or are mitigated by your work

# Related work

This chapter includes a broad and detailed review of relevant existing work.
The literature review should provide background and context for the thesis work.
The subsections may be organized in whatever manner seems best suited to the material--
chronological, or by topic, or according to some other criteria
(e.g., primary versus secondary resources).

If ethical issues are central to this work, you should also address historical and
contemporary issues or efforts made to address them.

# FIRST TWO CHAPTERS END HERE

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
