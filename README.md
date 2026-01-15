```python
"""
projekt_2.py: second project for Engeto Online Python Academy

author: Filip Hazuka
email: hazuk89224@mot.sps-dopravni.cz
discord: FilipH#8063
"""

SEPARATOR = "=" * 44


def print_intro():
    print("Welcome to Tic Tac Toe")
    print(SEPARATOR)
    print("GAME RULES:")
    print("Each player can place one mark (or stone)")
    print("per turn on the 3x3 grid. The WINNER is")
    print("who succeeds in placing three of their")
    print("marks in a:")
    print("* horizontal,")
    print("* vertical or")
    print("* diagonal row")
    print(SEPARATOR)
    print("Let's start the game")
    print(SEPARATOR)


def print_board(board):
    print("+---+---+---+")
    print(f"| {board[0]} | {board[1]} | {board[2]} |")
    print("+---+---+---+")
    print(f"| {board[3]} | {board[4]} | {board[5]} |")
    print("+---+---+---+")
    print(f"| {board[6]} | {board[7]} | {board[8]} |")
    print("+---+---+---+")


def is_winner(board, mark):
    wins = [
        (0, 1, 2),
        (3, 4, 5),
        (6, 7, 8),
        (0, 3, 6),
        (1, 4, 7),
        (2, 5, 8),
        (0, 4, 8),
        (2, 4, 6),
    ]
    for a, b, c in wins:
        if board[a] == mark and board[b] == mark and board[c] == mark:
            return True
    return False


def is_draw(board):
    return " " not in board


def get_move(board, player):
    while True:
        move = input(f"Player {player} | Please enter your move number: ").strip()

        if not move.isdigit():
            print("Invalid input. Please enter a number from 1 to 9.")
            print(SEPARATOR)
            continue

        move_number = int(move)

        if move_number < 1 or move_number > 9:
            print("Invalid number. Please choose a number from 1 to 9.")
            print(SEPARATOR)
            continue

        index = move_number - 1

        if board[index] != " ":
            print("This position is already taken. Choose another one.")
            print(SEPARATOR)
            continue

        return index


def main():
    board = [" "] * 9
    current_player = "x"

    print_intro()
    print_board(board)

    while True:
        print(SEPARATOR)
        move_index = get_move(board, current_player)
        print(SEPARATOR)

        board[move_index] = current_player
        print_board(board)

        if is_winner(board, current_player):
            print(SEPARATOR)
            print(f"Congratulations, the player {current_player} WON!")
            print(SEPARATOR)
            break

        if is_draw(board):
            print(SEPARATOR)
            print("It's a draw!")
            print(SEPARATOR)
            break

        current_player = "o" if current_player == "x" else "x"


if __name__ == "__main__":
    main()
