# Foot
2D Turn-Based Football Management Simulator (C#/.Net) for Godot

This code sample gives a snapshot of the implementation of the game's league and cup fixture systems.

- The abstract superclass Competition is extended by the abstract subclasses Cup & Division.

- These can be extended by various different instances configured for different types of Cup competitions (Division Cup, Seeded Cup & Unseeded Cup), with different numbers of teams, rounds and methods for drawing each round.

- And similarly, different Division subclasses can have different configurations for promotion, relegation and playoffs.

- When a Division object is created, it takes a List of Ints as a parameter - representing the clubs - and constructs the fixture list using Berger Tables (a round-robin system). The Division instance contains a Queue of Lists, where each List represents a game week. Each List is populated by Fixture objects - representing the week's Fixtures - each of which contain two ints, representing the Home and Away sides.

- Each team plays every other team twice - home and away (taking (n-1) * 2 weeks, where n is the size of the division). The Home and Away matches are in two different halves of the season, and no team plays consecutive Home or Away matches. Furthermore, the two halves of the season are not mirrored, and are instead randomised, though any given game week occurs twice in a Season (with the Home/Away teams reversed).

- Finally, the player's team (0) is always positioned in a given Fixture list at index 0.

- The Competition superclass implements the construction of the initial Berger tables and the randomising of lists of teams, since these can also be utilised in the implementation of Cup Competitions - in forming the basis of group stages, and the drawing of rounds respectively.

- The Cup Subclass contains implementations for drawing a single round, and a function to recursively draw every round, pushing the final onto the bottom of the stack first, and working backwards.
