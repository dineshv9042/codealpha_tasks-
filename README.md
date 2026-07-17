# codealpha_tasks-
Task1: Hangman Code:
import random

# List of predefined words
words = ["apple", "tiger", "python", "school", "garden"]

# Randomly choose a word
word = random.choice(words)

# Create blank spaces for the word
display = ["_"] * len(word)

# List to store guessed letters
guessed_letters = []

# Maximum incorrect guesses
max_attempts = 6
wrong_attempts = 0

print("=================================")
print("       WELCOME TO HANGMAN")
print("=================================")

# Main game loop
while wrong_attempts < max_attempts and "_" in display:

    print("\nWord: ", " ".join(display))
    print("Wrong Attempts Left:", max_attempts - wrong_attempts)
    print("Guessed Letters:", guessed_letters)

    # Take user input
    guess = input("Enter a letter: ").lower()

    # Check valid input
    if len(guess) != 1 or not guess.isalpha():
        print("Please enter only one alphabet letter.")
        continue

    # Check if already guessed
    if guess in guessed_letters:
        print("You already guessed this letter.")
        continue

    guessed_letters.append(guess)

    # Check if letter is in the word
    if guess in word:
        print("Correct Guess!")

        # Reveal matching letters
        for i in range(len(word)):
            if word[i] == guess:
                display[i] = guess
    else:
        print("Wrong Guess!")
        wrong_attempts += 1

# Final Result
if "_" not in display:
    print("\nCongratulations!")
    print("You guessed the word:", word)
else:
    print("\nGame Over!")
    print("The correct word was:", word)o
