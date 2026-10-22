# 📘 Assignment: Hangman Game

## 🎯 Objective

Build a Hangman game where players guess letters to reveal a hidden word before running out of attempts. Practice Python string manipulation, loops, conditionals, random selection, and user input.

## 📝 Tasks

### 🛠️	Set Up the Game

#### Description
Create a predefined word list and prepare a new game with a randomly selected hidden word and a limited number of incorrect guesses.

#### Requirements
Completed program should:

- Randomly select one word from a predefined list of words.
- Display an underscore for each letter in the hidden word, separated by spaces (for example, `_ _ _ _` for a four-letter word).
- Set and display the number of incorrect guesses remaining at the start of the game.

### 🛠️	Implement the Guessing Loop

#### Description
Use a loop to accept letter guesses, update the displayed word, and track remaining incorrect guesses until the player wins or loses.

#### Requirements
Completed program should:

- Accept one letter guess at a time from the player.
- Reveal every occurrence of a correctly guessed letter while keeping unguessed letters hidden as underscores.
- Decrease the remaining incorrect guesses by one when a guessed letter is not in the word.
- Display the current word progress and remaining incorrect guesses after each guess.
- End the game when all letters are revealed or no incorrect guesses remain.
- Display a win message when the word is guessed, or a loss message revealing the hidden word when attempts are exhausted.
