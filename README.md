# Hangman-AI
An AI that tries to solve words given by a user, hangman-style.

Note: This repository only explains the guessing mechanism, not the mechanism of the hangman game itself. This is also my first repository so please feel free to suggest possible improvements.

# How to use
pass

# How it works
The first thing the AI does is get a pool of words with the length of the given word. 

It then identifies the most popular letter in said wordpool then guesses that letter.
Note that it doesn't count letters appearing multiple times in a single word! 

Each time the AI guesses, it stores the letter in a "guessedLetters" list and makes sure it doesn't guess that letter again!

After guessing, it narrows down the wordpool using two pruning methods: False Pruning and Index Pruning. 

*(I only came up with the names for myself)*
## False Pruning
- Takes in a letter then removes all words that do not have a certain letter. 
- Used when guess is wrong.
## Index Pruning
- Takes in which letters have already been revealed and their indices. It then removes all words that do not have those letters in their respective indices. 
- Used when guess is right.

This process then loops back to the beginning where it finds the most popular letter in the updated word pool.

# The Dictionary
The words used for this AI is from [this word list by dwyl](https://github.com/dwyl/english-words).

All the words are stored in a json file with keys ranging from "1" to "20". The value of each key is a list containing words with the length equal to the key (e.g: Key "4" contains all words with 4 letters etc.)

This is done this way so that when the user enters a word, the AI can just get the length of that word, use it as a key, then grab the word pool corresponding to the key. This speeds up the initial process of getting all possible words from a giant word pool.
