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

  Game development is a rather difficult field of work to get involved with. There's
so many different parts that make up an entire game, and without a large team of
people to split up the work with, a huge skill set is required of one person to
fully develop something substantial. Luckily, making games nowadays is much easier
than it was 40 years ago. With the help of the internet, there's endless resources
available to find tutorials and guides on how to create whatever one could want. A
big part of that is in the availability of game engines, like Unreal Engine and Unity,
which provide a fairly user-friendly interface to develop games and robust systems to
support all types of ideas. With engines being the foundation of most game
development, many look to plugins to solve the most basic and broad of problems that
they might face when initially starting work on a new idea. Plugins are very common
to the game development space as they are essentially just pre-made software that one
can import into any project and start using immediately for whatever purpose is
needed. They're primarily used for further assistance in performing specific tasks
that the user doesn't necessarily want to create an entire system for from scratch.
There are a massive number of plugins available for people to use with any given
engine, and most can be found fairly easily just by searching for them online. The
usefulness of many plugins can really ease the monumental amount of work one might
have to do to create the game they're imagining. (WRITING NOTE: This section is
rambling way too much, should get into discussing random generation way sooner)

  When it comes to recent trends in the indie game development space, the Roguelike
genre has influenced the industry in many ways. Random generation and challenging
gameplay excites players to keep playing games of the like to hone their skill.
Even games that aren't strictly Roguelikes themselves like to incorporate aspects
of procedural or random generation into various facets of their games, especially
their map systems, which often leads to fresh experiences that are unique to every
player. This makes for highly entertaining and replayable experiences that keep people
coming back.

  The software created for this project is a plugin for Unity to assist in the
process of random map generation by taking pre-made rooms created by the user
and placing and connecting them to generate maps in an efficient and easy way.
The goal isn't just to create a good generation algorithm, but primarily to
make the plugin easy to use so that those unfamiliar with coding something like
it would still have the ability to create the game they want. In addition, the
plugin itself is robust with many options for the user to select from to specify
parts of the generation process. Overall, it's a practical, low effort way for
amateur developers to more easily create games of the Roguelike genre.

## Motivation

A lot of the motivation for this project stems from two things: the increase in
access to game development software and the lack of this desired tool in the
game development space. With engines being so commonly used to develop games
and countless plugins being readily available for anybody to use, it makes sense
for this tool to exist within the space. Creating more ways for people to get
into game development easier is most often a good thing as it allows more
people to create their vision. To discuss the second main motivating factor,
it's honestly astonishing that this specific tool hasn't been created before!
Although there are plugins available to assist with some types of map generation,
most of them have to do with tile-by-tile generation as opposed to the dungeon-style
generation this software implements.

## Current State of the Art

Much of this plugin was inspired by the level generation of the popular Roguelike
Enter the Gungeon. It inspired many developers to create games of a similar
style and still remains one of the most popular Roguelikes of all time, so it
seems like a solid baseline for map generation. There are also many articles
that discuss map generation philosophies and various commonly used algorithms.
(WRITING NOTE: Go more into detail on the articles and algorithms)

## Goals of the Project

The primary goal of the project was to create a plugin that's both easy to use
and robust in its generation capabilities. Because its meant to help bridge the gap
between those that want to make games and the ability to actually create them,
ease of use was the main objective going into it.

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
