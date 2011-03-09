# Land of Lisp

Some of the source code examples from the book by Conrad Barski, with minor
additions.

## Why?

Because I wanted to know how it feels to program in Lisp, even if that meant
just typing examples.

## How?

All the programs were developed with Common Lisp 2.48. Usually, they are run by
loading the source file into the Common Lisp interpreter, and then typing Lisp
expressions in the repl.

    $ clisp -repl <filename>

## What?

Which games did I bother to type in? Read on.

## Grand Theft Wumpus

Grand Theft Wumpus is a remake of the classic Hunt The Wumpus, with a different
background story, but without the dodecahedron map. Instead, the map is a
randomly generated graph. Every game looks different.

![screenshot of the game](known-city2.png)

#### Differences to the game from the book

* All the nodes of the city are displayed from the beginning. Imagine the Lisp
  alien has a city map. Nodes you haven't yet visited are tagged with a
  question mark.

* The nodes of the city have different visual appearance:
    * Your current position (\*) is marked with a thick border.
    * Nodes with a distance of 2 or smaller to the Wumpus (blood) are marked
      light red.
    * Nodes with edges blocked by cops (sirens) have a blue border.


#### Running and playing the game

1. Load the program.

        $ clisp -repl gtw.cl

2. Start a new game.

        [1]> (new-game)

3. The file known-city.svn gets created. Open that file with an svg viewer
   capable of auto-reloading when the displayed file has changed. I'm using
   evince.

4. Walk around the city with the 'walk' command.

        [2]> (walk 26)

5. Observe how known-city.svg changes.
    
6. If you think you have tracked down the wumpus, attack with the 'charge'
   command. Remember: you have only one chance to charge.

        [3]> (charge 22)

7. If you're stuck or game over, you can start a new game anytime.

        [1]> (new-game)

## Orc Battle

Defeat vicious foes in this exciting turn-based fighting game.

    You are a valiant knight with a health of 30, an agility of 30, and a strength of 30
    Your foes:
       1. (Health=3) A slime mold with a sliminess of 5
       2. (Health=6) A fierce BRIGAND
       3. (Health=4) A fierce BRIGAND
       4. (Health=5) A slime mold with a sliminess of 2
       5. (Health=1) A healslime with a heal power of 5. 
       6. (Health=5) A slime mold with a sliminess of 3
       7. (Health=3) A slime mold with a sliminess of 4
       8. (Health=10) A wicked orc with a level 5 club
       9. (Health=6) A wicked orc with a level 7 club
       10. (Health=2) A slime mold with a sliminess of 2
       11. (Health=2) A healslime with a heal power of 1. 
       12. (Health=8) A malicious hydra with 8 heads.
    Attack style: [s]tab [d]ouble swing [r]oundhouse:

#### Differences to the game from the book

There is a new kind of enemy, the healslime. It either heals you (with a
probability of 3/4) or revives one of the dead foes (with a probability of
1/4). It is a weak enemy and can be defeated easily. Decide if you want to let
it live to heal you, but then you face the risk that it revives a hydra.

#### Running and playing the game

1. Load the program.

        $ clisp -repl orc-battle.cl

2. Start a new game.

        [1]> (orc-battle)

3. In each round, decide what kind of attack you want to launch, and type the
   corresponding character. The number of attacks you can launch in every round
   depends on your agility.
    * [s]tab to deal lots of damage to a specific enemy.
    * [d]ouble swing to deal a medium amount of damage to two specific enemies.
    * [r]oundhouse to deal a small amount of damage to a number of random
      enemies.

## Robots

The classic robots game. Walk around, avoid bumping into robots while trying to
make the robots bump into each other. When all robots are scrap, You have won.

    |                                                                |
    |   A                                               A            |
    |                                                                |
    |                                                                |
    |                                                                |
    |                                                                |
    |                                                                |
    |                                                                |
    |                                @                               |
    |                                                     A          |
    |     A     A                                                    |
    |                                                                |
    |                                                                |
    |                A                                          A    |
    |    A                               A                           |
    |                   A                                            |
    qwe/asd/zxc to move, (t)eleport, (l)eave:

@: The Player.

A: A Robot.

\#: Scrap.

#### Differences to the game from the book

None this time.

#### Running and playing the game

1. Load the program.

        $ clisp -repl robots.cl

2. Start a new game

        [1]> (robots)

3. Walk around until all robots are scrap.
    * q: north-west
    * w: north
    * e: north-east
    * a: west
    * s: stay put
    * d: east
    * z: south-west
    * x: south
    * c: south-east
    * t: teleport to a random spot (dangerous!)
    * l: exit the game

## FAQ

Q: I looked at the source code and noticed that you used VIM to type LISP
code. Are you insane?

A: I'm not going to answer that.
