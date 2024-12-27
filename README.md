# Pig-dice
# Pig Dice Game

This program implements a simple **Pig Dice Game** where a user competes against the computer to reach a score of 30. Below are the details of the game, followed by the code.

---

## Rules of the Game

1. The game is played with a 6-sided die.
2. Each round, both the player and the computer roll the die.
3. If the die value is **1**, the player or computer loses all their points.
4. Otherwise, the die value is added to the player's or computer's score.
5. The first to reach **30 points** wins the game.

---

## Code Implementation

### Functionality

- **`update_score(score, die_value)`**:
  - Updates the score for the player or computer based on the die value.
  - Resets the score to 0 if the die value is 1.
- **`display_scoreboard(player_score, computer_score)`**:
  - Displays the current scores of the player and the computer in a formatted way.

### Game Flow

1. The player enters their name.
2. The game alternates between the player and the computer rolling the die.
3. The game ends when either the player or the computer reaches a score of 30.

---

## Code

```python
from random import randint

def update_score(score, die_value):
    if die_value == 1:
        return 0
    else:
        return score + die_value

def display_scoreboard(player_score, computer_score):
    print()
    print("#" * 20)
    print(f"Player score: {player_score}")
    print(f"Computer score: {computer_score}")
    print("#" * 20)
    print()

player_score = 0
computer_score = 0

welcome_message = """
Welcome to the Pig Dice Game! 

In this game, a user and a computer opponent roll a 6-sided die each round. 
If the value of the die is a 1, the player that rolled the 1 loses all of their points.
Otherwise, the player gets the value of the die added to their points. 

The first player to reach 30 points wins!
"""
print(welcome_message)

username = input('What is your name?: ')

while True:
    input(f"Press 'Enter' to roll the die, {username}!\n")
    player_die_value = randint(1, 6)
    print(f"{username} rolls a {player_die_value}")
    
    computer_die_value = randint(1, 6)
    print(f"Computer rolls a {computer_die_value}")

    player_score = update_score(player_score, player_die_value)
    computer_score = update_score(computer_score, computer_die_value)
    display_scoreboard(player_score, computer_score)
    
    if player_score >= 30:
        print(f"{username} wins!")
        break
    elif computer_score >= 30:
        print("Computer wins!")
        break

# Add an option to restart or quit
print("\nGame over! Thanks for playing.")
Features to Add
A scoring history for both the player and the computer.
Options to restart or quit the game after each match.
Multiplayer mode for multiple human players.
A leaderboard to keep track of high scores.
