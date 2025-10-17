# Mǽrstánas

> Version 0.4.1

## Overview

**Mǽrstánas** is a free libre open source abstract strategy game where players alternate placing stones within the squares of a 7x7 grid with the goal of creating connection points ("hinges") between their own pieces or the edges of the board.

### Objective

Players try to achieve the highest score by making the most number of connections.

### Components

- Game board (*tæfl*)
- Approximately 40 stones (*stánas*) or tokens, split evenly between two colors
- 1 stone of each color marked in some manner (traditionally a *Þorn*, or "thorn" rune - ᚦ) to designate it as a *Þunor-stán* ("thunder-stone").
- 1 stone of each color marked in some manner (traditionally a *ós*, or "god" rune - ᚩ) to designate it as a *wóden-stán* ("Woden-stone").

### Setup & starting the game

The board begins empty (similar to Go). Traditionally, the player using the darker colored stones would play first, but players may decide who goes first in whatever manner seems appropriate. Players then alternate taking turns.

## Playing the game

- On a player's turn, the player places one stone (*stán*) on a square on the game board.
- Stones (*stánas*) must be placed within the square, not on the intersections as in Go.
- Stones may be placed on any empty square, either standing alone or adjacent to another stone of either color (creating a *heorr* or "hinge").

### Placement limitations

- Stones may have no more than **three** hinges; the fourth side *must always remain free*.
- Stones may not be placed such that four hinges are created immediately.
- The edge of the board counts as **one** hinge; corners count as **two** because they border two edges.
- Play continues until no more viable moves remain.

### Passing rules

- When playing with Special Stones, the opposing player may have viable moves remaining while the active player may not. When this occurs, the active player must pass.
- If the opposing player uses a Thunder-stone, stones are removed from the board so new moves may become available on the player's next turn.

### Thunder-stone rules

- Players each have **one** thunder-stone (*Þunor-stán*), which may be placed on the board during their turn **instead of a regular stone**.
- Thunder-stones are the exception to the four hinge limitation. This is because, when placed, a thunder-stone removes any and all stones orthogonally adjacent to its position, whether they belong to the player or the opponent.
- Stones which have been removed from the board are returned to the respective players and do not count as captures or contribute to scoring in any way.
- After placement, thunder-stones hinges and scoring are treated the same as normal stones.

### Woden-stone rules

- Players each have **one** Woden-stone (*wóden-stán*), which may be placed on the board during their turn **instead of a regular stone**.
- Unlike standard and thunder-stones, which are placed on an open square, players use the Woden-stone to **replace** one of their opponent's stones already on the board.
- Being able to swap out an opponent's stone can create unique scoring and blocking opportunities, so waiting to use the Woden-stone until later in the game may offer greater strategic advantage.
- After placement, Woden-stones are scored the same as normal stones.

## Scoring

- Players receive one point for each stone or edge that is adjacent to one of their own stones (*freóndlíc heorr* or "friendly hinge").
- The player with the highest score wins.
- Note that tie games are possible.

## Alternate rules and scoring

### The wraparound rule ("Advanced Mǽrstánas")

- When considering hinges for edge positions, instead of counting the edge as a hinge, look at the position on the opposite side of the board.
  - For example, position A2 would only count a hinge if a friendly stone was placed at G2. Likewise B1 would need to look at B7.
  - Stones places in corners would need to consider both opposing corners.
- When the "wraparound" rule is in effect, edges are **not** automatically scored as hinges. Only true stone-to-stone hinges, including wraparound positions, are scored.
- Note: This rule may create positions that normally look unplayable. Care must be exercised when looking at at edge plays.

### Simple scoring

- When playing with the traditional ruleset, disregard scoring all edge hinges. This results in a lower scoring game, but may make it easier for new or younger players to grasp scoring more quickly.

## Notation

- **Placement:** `E4` (stone placed at E4)
- **Thunder-stone:** `T E4xE3/D4` (placed at E4, removes adjacent stones at E3 and D4)
- **Wóden-stone:** `W E4` (replaces opponent’s stone at E4 with your Wóden-stone)
- **Scoring:** At end, list the totals `Dark: 42, Light: 39`

## Credits

**Mǽrstánas** was created by John Beers.

It was conceived in 2022 while working on **Oferhlýp**. As a fan of Hnefatafl, I wanted to name my games using Anglo-Saxon words to lend a quasi-historical feel to them. Both **Mǽrstánas** and **Oferhlýp** utilize the same 7x7 grid because, if they *were* historical, it might make sense for people to reuse an existing board, much like chess and checkers.

> The word *mǽrstánas* is the plural form of *mǽrstán*, an Anglo-Saxon (Old English) word that means "a boundary-stone".
> (<https://bosworthtoller.com/22190>)

Special thanks to my cousins, Caleb, Jerome, and Jesse, for play testing and coming up with the Advanced Mǽrstánas rule.

## Legal

**Mǽrstánas** is available under a Creative Commons Attribution-ShareAlike 4.0 International license. (<https://creativecommons.org/licenses/by-sa/4.0/>)

**You are free to:**

- **Share** - copy and redistribute the material in any medium or format

- **Adapt** - remix, transform, and build upon the material for any purpose, even commercially.

The licensor cannot revoke these freedoms as long as you follow the license terms.

**Under the following terms:**

- Attribution - You must give appropriate credit, provide a link to the license, and indicate if changes were made. You may do so in any reasonable manner, but not in any way that suggests the licensor endorses you or your use.
- ShareAlike - If you remix, transform, or build upon the material, you must distribute your contributions under the same license as the original.

**No additional restrictions** — You may not apply legal terms or technological measures that legally restrict others from doing anything the license permits.

## Find out more

More information on **Mǽrstánas** and “living rules” can be found at: <http://codeberg.org/jaerrib/maerstanas>

## Alternative play option

If you don't have access to stones, feel free to use the included page of gameboards. **Mǽrstánas** is similar to Tic-Tac-Toe in that players can just alternate writing an *X* or an *O* in place of the stones. You can also just draw a 7x7 grid if you find yourself without a printer and need to pass the time! Just remember that **Mǽrstánas** is *not* Tic-Tac-Toe, and the rules and win conditions are different.

![image of several small boards](../assets/svg/mini-boards.svg)
