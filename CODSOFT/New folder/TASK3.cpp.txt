#include <iostream>
#include <string>
using namespace std;

char board[9] = {'1','2','3','4','5','6','7','8','9'};
char currentPlayer = 'X';

void displayBoard() {
    cout << "\n";
    for (int i = 0; i < 9; i++) {
        cout << board[i] << " ";
        if ((i + 1) % 3 == 0)
            cout << "\n";
    }
}

bool isWinner() {
    // All possible winning combinations
    int wins[8][3] = {
        {0, 1, 2},
        {3, 4, 5},
        {6, 7, 8},
        {0, 3, 6},
        {1, 4, 7},
        {2, 5, 8},
        {0, 4, 8},
        {2, 4, 6}
    };

    for (auto& win : wins) {
        if (board[win[0]] == currentPlayer &&
            board[win[1]] == currentPlayer &&
            board[win[2]] == currentPlayer) {
            return true;
        }
    }

    return false;
}

bool isDraw() {
    for (int i = 0; i < 9; i++) {
        if (board[i] != 'X' && board[i] != 'O')
            return false;
    }
    return true;
}

void playerMove() {
    int move;
    while (true) {
        cout << "Player " << currentPlayer << ", enter move (1-9): ";
        cin >> move;

        if (cin.fail() || move < 1 || move > 9) {
            cin.clear(); // clear error flags
            cin.ignore(1000, '\n'); // discard invalid input
            cout << "Invalid input! Please enter a number from 1 to 9.\n";
            continue;
        }

        move--; // adjust for 0-indexed array

        if (board[move] != 'X' && board[move] != 'O') {
            board[move] = currentPlayer;
            break;
        } else {
            cout << "Position already taken! Try another.\n";
        }
    }
}

void switchPlayer() {
    currentPlayer = (currentPlayer == 'X') ? 'O' : 'X';
}

int main() {
    cout << "Tic Tac Toe Game\n";
    displayBoard();

    while (true) {
        playerMove();
        displayBoard();

        if (isWinner()) {
            cout << "Player " << currentPlayer << " wins!\n";
            break;
        } else if (isDraw()) {
            cout << "It's a draw!\n";
            break;
        }

        switchPlayer();
    }

    return 0;
}
