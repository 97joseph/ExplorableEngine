# ExplorableEngine
 Engine for generating explorable worlds
Introduction 

In  the  Project, you will create an engine for generating explorable worlds. This is a large design project that will require you and one partner to work through every stage of development from ideation to presentation. The goal of this project is to teach you how to handle a larger piece of code with little starter code in the hopes of emulating something like a product development cycle. In accordance with this, the grading of this project will be different from other projects. Since there is no notion of “the correct answer” when it comes to world design and implementation, you will be assessed much like a performance review you might receive at an internship or job in addition to a very general autograder. While this means you will be graded slightly subjectively, we promise to be pretty nice bosses and will respect you as any boss should respect their hard working employees. Please talk to us if you feel the grading scheme feels unfair.

This project will require you a great deal of exploration and experimentation. Searching the web for answers  should be a regular activity throughout this process. Please know that there are no right and wrong answers, as this is a very open-ended project. However, there are some implementations and ideas that are better than others. It is ok and expected that you will go through several iterations before settling on something that you deem good. That is, this project is about software engineering.

You’re not required to use any of the fancy data structures or concepts from class (A*, MSTs, Disjoint Sets, etc). This project is about software engineering, not about data structures or algorithms. The data structures and algorithms we’ve learned about in class will make your code significantly simpler and more efficient, but please don’t use things just because we learned about them in class. Only use these tools if you feel comfortable using them in your implementation.




 2D Game Engine

This is the project page for a game engine that generates explorable 2D tile-based worlds. 

## World Generation
Worlds are initialized as 90 x 40 grids of black tiles. A random number of rooms is generated with random integer positions, widths, and heights. To ensure that worlds are not too cluttered, our world generation algorithm ensures that rooms do not overlap and maintain a distance of at least three spaces away from each other. 

Following room generation, we connect rooms at random by drawing hallways between them until we have a single connected component. Rooms are connected by selecting a point inside a randomly chosen first room and another point inside a randomly chosen second room. Then, a path comprised of a horizontal and vertical component is drawn, connecting the two points together. Finally, we update a weighted union-find data structure to reflect that these two rooms are now connected.

![alt text](https://i.imgur.com/KBYzBKN.png)

## Persistence
Game persistence is accomplished by keeping track of the world seed and user keypresses following world generation. The state of a play is saved in the `data.txt` file when a user quits the program with `:q` in the following format: `n[SEED][PLAYER MOVEMENT]`. The saved game can be loaded when the program is first started by pressing `l`. 

![alt text](https://i.imgur.com/91cs8Cj.png)

## Interactivity
The user is able to control an avatar represented by an `@` tile that can moved around using the `W`, `A`, `S`, and `D` keys. The system is deterministic in that the same sequence of keypresses from the same seed will result in exactly the same behavior every time.
