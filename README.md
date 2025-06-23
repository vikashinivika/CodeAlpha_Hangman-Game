# CodeAlpha_Hangman-Game
import random

# Predefined list of words
word_list = ['apple', 'house', 'train', 'river', 'table']

# Randomly choose a word from the list
secret_word = random.choice(word_list)
guessed_letters = []
wrong_guesses = 0
max_wrong_guesses = 6

# Create display with underscores
display_word = ['_' for _ in secret_word]

print("🎯 Welcome to Hangman!")
print("Guess the word, one letter at a time.")
print("You have 6 chances to make wrong guesses.")

while wrong_guesses < max_wrong_guesses and '_' in display_word:
    print("\nWord: ", ' '.join(display_word))
    guess = input("Enter a letter: ").lower()

    if not guess.isalpha() or len(guess) != 1:
        print("Please enter a single alphabetic character.")
        continue

    if guess in guessed_letters:
        print("You've already guessed that letter.")
        continue

    guessed_letters.append(guess)

    if guess in secret_word:
        print("✅ Correct!")
        for i, letter in enumerate(secret_word):
            if letter == guess:
                display_word[i] = guess
    else:
        wrong_guesses += 1
        print(f"❌ Incorrect! You have {max_wrong_guesses - wrong_guesses} tries left.")

# Game over
if '_' not in display_word:
    print(f"\n🎉 Congratulations! You guessed the word: {secret_word}")
else:
    print(f"\n💀 Game Over! The word was: {secret_word}")
