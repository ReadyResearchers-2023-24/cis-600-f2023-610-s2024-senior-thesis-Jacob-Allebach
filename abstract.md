# Abstract

This research aims to create a plugin for the video game engine Unity that allows
users to more easily generate levels for their games. The algorithm utilized for
the plugin is based on a room-and-connector generation system instead of the
tile-by-tile generation that is common in many games involving map generation. This
means that it has more of a dungeon-like layout instead of a cave-like environment.
It does this by taking in a set of rooms build by the user and creating instances of
those rooms randomly to connect with hallways. The rooms required for this plugin to
function are to be built in a particular way so that each has the necessary components
to interact with the code properly. Within each room, the user is able to specify the
exact dimensions of the room by using a polygon collider, and they are required to put
the exact locations on the edge of the room where other rooms will be connected through
the use of the hallways. The user is also given some other customization
options, those being the number of rooms to generate and the sprites for the hallways
it will connect the rooms with. Because the two main goals of the plugin were creating
a robust map generator as well as making it a tool that's easy to use at any skill
level, a user study was conducted to evaluate how well the final version of the plugin
achieved those. Through the testing of its functionality and getting feedback from
participants of the study, this research has shown that the resulting plugin has a
lot of potential to be developed into something extremely useful within the game
development field.
