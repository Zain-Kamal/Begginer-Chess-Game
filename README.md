# Begginer-Chess-Game
C++ code used to design a simple take of the game of chess. The goal of the code is to design the board and place the pieces which can be moves by the user. However, in this take all the pieces can be moves anywhere across the board rather than restricted to specfic movement.

```
#include <iostream>
using namespace std;

void initBoard(char board[][8], int size);
void printBoard(char board[][8], int size);
bool movePiece(char board[][8], int size, int x1, int y1, int x2, int y2);

int main() {
    int const size = 8, colmn = 8;
    int x1, y1, x2, y2, counter = 1;
    char board[size][colmn];
    initBoard(board, size);
    printBoard(board, size);
    while (true) {
        if (counter % 2 != 0) {
            cout << "Player 1 which piece would you like to move? Enter the row then the column ";
            cin >> x1 >> y1;
            cout << "where would you like to move it? Enter the row then the column";
            cin >> x2 >> y2;
            if (movePiece(board, size, x1, y1, x2, y2))
                printBoard(board, size);
            else
                cout << "This move is invalid!";
        }
        else if (counter % 2 == 0) {
            cout << "Player 2 which piece would you like to move? Enter the row then the column";
            cin >> x1 >> y1;
            cout << "where would you like to move it? Enter the row then the column";
            cin >> x2 >> y2;
            if (movePiece(board, size, x1, y1, x2, y2))
                printBoard(board, size);
            else
                cout << "This move is invalid!";
        }
        counter++;
    }
    return 0;
}


void initBoard(char board[][8], int size) { //This function fills the board with chess pieces
    for (int i = 0; i < size; i++) {
        for (int j = 0; j < 8; j++) {
            if (i < 2)
                board[i][j] = 'X';
            else if (i >= size - 2)
                board[i][j] = 'O';
            else
            board[i][j] = '.';
        }
    }
}

void printBoard(char board[][8], int size) { //This function prints the chess board
    for (int i = -1; i < size; i++) {
        if (i > -1)
            cout << i;
        for (int j = -1; j < 8; j++) {
            if (j == -1 && i == -1)
                cout << " ";
            else if (i == -1)
                cout << j << " ";
            else if (i > -1 && j > -1)
                cout << " " << board[i][j];
        }
    cout << endl;
    }
}

bool movePiece(char board[][8], int size, int x1, int y1, int x2, int y2) { //This function moves the pieces
    if (x1 > size || x2 > size || y1 > 8 || y2 > 8)
        return false;
    board[x2][y2] = board[x1][y1];
    board[x1][y1] = '.';
    return true;
}
```
