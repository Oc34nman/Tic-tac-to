# Tic-tac-to\

#include<iostream>
using namespace std;


void printBoard(const char board[3][3]);
void playerTurn(char board[3][3], char player);
bool checkWin(const char board[3][3]);
bool checkFull(char board[][3]);


int main() {
char board[3][3] = { {'-','-','-'}, {'-','-','-',}, {'-','-','-',} };
char player = 'X';
bool endgame = false;




cout << "welcome to tictactoe" << endl;
while (endgame == false) {
printBoard(board);
playerTurn(board, player);

if (checkWin(board) == true) {
cout << "Player " << player << " wins!" << endl;
endgame = true;
}
else if (checkFull(board) == true) {
cout << "It's a draw!\n";
endgame = true;
}

if (player == 'X')
player = 'Y';
else if (player == 'Y')
player = 'X';
}

if (endgame == false)
cout << "Player " << player << "'s turn" << endl << endl;




}

bool checkFull(char board[][3]) {
for (int i = 0; i < 3; i++) {
for (int j = 0; j < 3; j++) {
if (board[i][j] == '-') {
return false;
}
}
}
}




void playerTurn(char board[3][3], char player) {

int row;
int col;

if (player == 'X')
cout << "Player X, type row and column to place X:" << endl;
else
cout << "Player Y, type row and column to place O:" << endl;

cin >> row;
cin >> col;

if (player == 'X')
board[row - 1][col - 1] = 'X';
else
board[row - 1][col - 1] = 'O';

}


bool checkWin(const char board[3][3]) {


for (int i = 0; i < 3; i++) {

if (board[i][0] == board[i][1] && board[i][1] == board[i][2] && board[i][0] != '-')
return true;

if (board[0][i] == board[1][i] && board[1][i] == board[2][i] && board[0][i] != '-')
return true;

}

if (board[0][0] == board[1][1] && board[1][1] == board[2][2] && board[0][0] != '-')
return true;
if (board[0][2] == board[1][1] && board[1][1] == board[2][0] && board[0][2] != '-')
return true;

return false;
}


void printBoard(const char board[3][3]) {
for (int i = 0; i < 3; i++) {
for (int j = 0; j < 3; j++) {
cout << board[i][j] << " ";
}
cout << endl;
}
}

