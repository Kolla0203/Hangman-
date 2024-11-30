# Hangman 
import random

# List of words to choose from
words = ["python", "hangman", "developer", "programming", "random", "function", "variable"]

def choose_word():
    # Randomly choose a word from the list
    return random.choice(words)

def display_progress(word, guessed_letters):
    # Show the current progress with guessed letters
    return " ".join([letter if letter in guessed_letters else "_" for letter in word])

def hangman_game():
    word = choose_word()
    guessed_letters = set()
    attempts = 6  # Limit of incorrect guesses

    print("Welcome to Hangman!")
    print("Guess the word letter by letter.")

    while attempts > 0:
        print("\nWord: ", display_progress(word, guessed_letters))
        print(f"Attempts left: {attempts}")
        guess = input("Enter a letter: ").lower()

        # Check if the letter has already been guessed
        if guess in guessed_letters:
            print("You already guessed that letter. Try again.")
            continue

        guessed_letters.add(guess)

        if guess in word:
            print("Good guess!")
        else:
            print("Incorrect guess.")
            attempts -= 1

        # Check if the player has guessed the word
        if all(letter in guessed_letters for letter in word):
            print("\nCongratulations! You've guessed the word:", word)
            break
    else:
        print("\nGame Over! The word was:", word)

# Run the game
hangman_game()
