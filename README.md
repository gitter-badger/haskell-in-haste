# Haskell in Haste

A (very) short workshop designed to introduce Haskell quickly but practically.

## Getting Started

1. [Download Stack](https://github.com/commercialhaskell/stack/wiki/Downloads) for your operating system (scroll to the bottom for download links)
2. Clone this repository

         git clone https://github.com/charleso/haskell-in-haste.git

3. Run `stack setup` in the root of the directory
4. Run `stack build` in the root of the directory

## Running

1. Run `stack ghci`
2. Type `main` to start app
3. Go to: http://localhost:8080

### To reload files
1. Hit `ctrl-c` to stop app
2. Enter `:r` or `:reload` to recompile the project
3. Type `main` to start app again

## Introduction

See [here](Introduction.md) for the material to be used for teaching (very) basic Haskell.

Some concepts are intentionally not being covered due to the time available, which are listed [here](Avoid.md)

## Practical

![screenshot](static/images/screenshot.png)

It's _really_ important to remember that learning a new language can be tricky,
and Haskell especially so. Pick something really simple to start with and
don't feel bad or frustrated if you don't finish.
There should be plenty of mentors floating around, don't hesitate to ask for help.

## Challenges

A number of "bots" have been partially implemented as part of the chat program.
These are grouped in to three rough levels of difficulty.

To state the obvious, but it's recommend that they are tackled in this order.
Once you feel comfortable, or perhaps you're getting bored, try moving to the next level.

### Easy

- [Guessing game](src/Chat/Bot/Guess.hs)

### Medium

- [Rotational cipher](src/Chat/Bot/Cipher.hs)

### Hard

- [TicTacToe](src/Chat/Bot/TicTacToe.hs)
- [Calculator](src/Chat/Bot/Calculator.hs)

## Further Reading

The best place to start is probably the Yorgey lectures.
Both the online material and talks given by the BFPG group
can be found here:

- https://github.com/bfpg/cis194-yorgey-lectures
