def get_choice(player):
    print(f"\n{player}, enter your choice:")
    print("1 - Rock\n2 - Paper\n3 - Scissors")
    while True:
        try:
            choice = int(input(f"{player}'s choice: "))
            if choice in [1, 2, 3]:
                return choice
            else:
                print("Invalid choice. Please choose 1, 2, or 3.")
        except ValueError:
            print("Please enter a number (1, 2, or 3).")

def get_choice_name(choice):
    return {1: 'Rock', 2: 'Paper', 3: 'Scissors'}[choice]

def determine_winner(choice1, choice2):
    if choice1 == choice2:
        return "DRAW"
    elif (choice1 == 1 and choice2 == 3) or \
         (choice1 == 2 and choice2 == 1) or \
         (choice1 == 3 and choice2 == 2):
        return "Player 1"
    else:
        return "Player 2"

print('''\nWinning Rules:
Rock vs Paper -> Paper wins
Rock vs Scissors -> Rock wins
Paper vs Scissors -> Scissors wins\n''')

while True:
    player1_choice = get_choice("Player 1")
    print("\n" * 50)  # Clear screen (simulate hiding Player 1 input from Player 2)
    player2_choice = get_choice("Player 2")

    player1_name = get_choice_name(player1_choice)
    player2_name = get_choice_name(player2_choice)

    print(f"\nPlayer 1 chose: {player1_name}")
    print(f"Player 2 chose: {player2_name}")
    print(f"{player1_name} vs {player2_name}")

    result = determine_winner(player1_choice, player2_choice)

    if result == "DRAW":
        print("<== It's a tie! ==>")
    else:
        print(f"<== {result} wins! ==>")

    again = input("\nDo you want to play again? (Y/N): ")
    if again != 'y':
        break

print("Thanks for playing!")
