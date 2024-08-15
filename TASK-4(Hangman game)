import random

# Hangman ASCII Art
HANGMAN_PICS = [
    """
     -----
     |   |
         |
         |
         |
         |
    =========""",
    """
     -----
     |   |
     O   |
         |
         |
         |
    =========""",
    """
     -----
     |   |
     O   |
     |   |
         |
         |
    =========""",
    """
     -----
     |   |
     O   |
    /|   |
         |
         |
    =========""",
    """
     -----
     |   |
     O   |
    /|\\  |
         |
         |
    =========""",
    """
     -----
     |   |
     O   |
    /|\\  |
    /    |
         |
    =========""",
    """
     -----
     |   |
     O   |
    /|\\  |
    / \\  |
         |
    =========""",
]

# Word categories
WORD_CATEGORIES = {
    "Animals": ["tiger", "elephant", "giraffe", "kangaroo", "dolphin"],
    "Countries": ["canada", "germany", "india", "japan", "brazil"],
    "Movies": ["inception", "gladiator", "matrix", "avatar", "titanic"]
}

# Function to choose a category
def choose_category():
    print("Choose a category:")
    categories = list(WORD_CATEGORIES.keys())
    for idx, category in enumerate(categories):
        print(f"{idx + 1}. {category}")
    choice = int(input("Enter the number of your choice: ")) - 1
    return categories[choice]

# Function to set the difficulty level
def set_difficulty():
    print("Choose a difficulty level:")
    print("1. Easy (10 guesses)")
    print("2. Medium (7 guesses)")
    print("3. Hard (5 guesses)")
    choice = int(input("Enter the number of your choice: "))
    if choice == 1:
        return 10
    elif choice == 2:
        return 7
    else:
        return 5

# Function to give a hint
def give_hint(word, correct_letters):
    for letter in word:
        if letter not in correct_letters:
            print(f"Hint: The word contains the letter '{letter}'")
            return

# Main Hangman function
def hangman():
    category = choose_category()
    word = random.choice(WORD_CATEGORIES[category])
    max_guesses = set_difficulty()
    guessed = False
    guessed_letters = []
    correct_letters = []
    incorrect_guesses = 0

    print(f"\nThe category is: {category}")
    print("_ " * len(word))

    while not guessed and incorrect_guesses < max_guesses:
        guess = input("\nEnter a letter or type 'hint' for a hint: ").lower()

        if guess == "hint":
            give_hint(word, correct_letters)
            max_guesses -= 1
            print(f"You have {max_guesses - incorrect_guesses} guesses left.")
            continue

        if len(guess) == 1 and guess.isalpha():
            if guess in guessed_letters:
                print("You already guessed that letter.")
            elif guess not in word:
                print(f"{guess} is not in the word.")
                incorrect_guesses += 1
                guessed_letters.append(guess)
            else:
                print(f"Good guess! {guess} is in the word.")
                guessed_letters.append(guess)
                correct_letters.append(guess)

        else:
            print("Invalid input. Please enter a single letter.")

        current_word = [letter if letter in correct_letters else "_" for letter in word]
        print(" ".join(current_word))
        print(HANGMAN_PICS[incorrect_guesses])

        if "_" not in current_word:
            guessed = True

    if guessed:
        print(f"\nCongratulations! You guessed the word '{word}'!")
    else:
        print(f"\nSorry, you ran out of guesses. The word was '{word}'.")

# Run the Hangman game
hangman()
