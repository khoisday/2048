# 2048 Project

## Table of content

- [Introduction](#introduction)
- [The original `2048` game](#first-game)
- [`2048 Solitaire`](#second-game)

## Introduction <a name="introduction"></a>

This is a website inspired by the very famous game `2048`. This contains 2 games:
- `2048 `
- `2048 Solitaire` - a combination of `2048` and `Solitaire`

## The `2048` game <a name="first-game"></a>

### Game state

The game state is determined by a 4x4 matrix, along with the highest score and current score. This state can be saved in the local storage so that if the players reload the website, they can continue playing the previous game without losing any progress.

### Merging

We have implemented the merging of tiles only along the left direction. However, to enable merging along the right, up, and down directions, we make use of the reverse or transpose of the board. We first perform the merging along the left direction on this modified board and then change it back to the original state.

During every merging event, we update the state of the board inside the JavaScript code first. Once we have finished changing the state of the board, we update the HTML to match the board and save the new board to the local storage.

### Endgame

At the start, we set the "winning state" to `display: none` to hide it from the user.

After each merging event, we check whether the game has ended or not. This is determined by whether the player has reached the `2048` tile or is unable to make any further merges. If the game has ended, we will display a message to the user indicating either "Game over" or "Victory", along with a "Try again" button. This is achieved by changing their `display` property.

### How to play board

We have added a `How to play` button to provide instructions for playing the game. By hovering over the button, the board will gradually disappear, and the instructions will be displayed. This effect was achieved using `requestAnimationFrame` to decrease the `opacity` CSS property. Once the board disappears, the instructions will be shown.

### Show keys option

To make the game available with only a mouse or for playing with a phone, we added arrow keys to the game. You can show or hide the key by pressing the `Show keys` button. The key is one arrow image and its rotation.

## `2048 Solitaire` <a name="second-game"></a>

### Game state

Using HTML and CSS to represent the card game. Each column has a bonus indicator and a bottom marker, and the cards have 30px distance in their top attributes. We use drag and drop API to implement the dragging and dropping effect of the cards. We have a new game button and a how to play button. We also use localStorage to keep track of the maximum score.

### Merging cards

When a new card is added to a column, we check if the two bottom cards have the same number. If they do, we merge them by deleting the last card and updating the number of the penultimate card. We use `requestAnimationFrame` to move the last card slightly until it reaches the penultimate card. If two bottom cards still have the same number, we repeat the process. We also keep track of `bonus`, which is the number of times this merging process occurs. The bonus amount is displayed in a small box with the `top` attribute set to the `top` attribute of the penultimate card `+40px`.

### Endgame

We keep track of a variable called `maxCard`, which represents the maximum `log2` of cards on the board. We update `maxCard` every time cards are merged. If `maxCard` is greater than 11, it means the player has reached `2048`. We disable the dragging effect of the card, and the columns have `display` none. In the losing state, we check if all columns are full, and no last cards match the current card.
