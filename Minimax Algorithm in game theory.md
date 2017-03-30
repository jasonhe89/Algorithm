**Minimax** is a kind of backtracking algorithm that is used in decision making and game theory to find the optimal move for a player, asuuming that your opponent also plays optimally. it is widely used in two player turn based games such as Tic-Tac-toe, Backgamon, Mancala,Chess, etc.

In Minimax the two players are called maximizer and minimizer. The **maximizer** tries to get the highest score possible while **the minimizer **tries to get the lowest score possible while minimizer tries to do opposite.

Every board state has a value associated with it. In a given state if the maximizer has upper hand, then the score of the board will tend to be some positive value. If the minimizer has the upper hand in that board state then it will tend to be some negative value. The values of the board are calculated by some heuristics which are unique for every type of game.

**Example:**

Consider a game whic has 4 final states and paths to reach final states are form root to 4 leaves of a perfect binary tree as shown below. Assume you are the maximizing player and you get the first chance to move, i.e.., you are at root, and your opponent at next level.**Which move you would make as a maximizing player considering that your opponnent also plays optimally?**

![](resources/E5C1D1DC3D566130A15AABBB3981142F.jpg)**
**

Since this is a backtracking based algorithm, it tries all possible moves, then backtracks and makes a decision.

* Maximizer goes LEFT: it is now the minimizers turn. The minimizer now has a choice between 3 and 5\. Being the minimizer it will definitely choose the least among both, that is 3
* Maximizer goes RIGHT: it is now the minimizers turn. The minimizer now has a choice between 2 and 9\. He will choose 2 as it is the least among the two values.

**
**

Tic-tac-toe

Lets build our evaluation function:

**Minimax Algorithm in Game theory**

**
**

**Finding the Best Move:**

function findBestMove(board);

 bestMove = Null

 for each move in board:

 if current move is better than bestMove

 bestMove = current move

 return bestMove

```c
// C++ program to compute evaluation function for
// Tic Tac Toe Game.
#include<stdio.h>
#include<algorithm>
using namespace std;

// Returns a value based on who is winning
// b[3][3] is the Tic-Tac-Toe board
int evaluate(char b[3][3])
{
	// Checking for Rows for X or O victory.
	for (int row = 0; row<3; row++)
	{
		if (b[row][0]==b[row][1] && b[row][1]==b[row][2])
		{
			if (b[row][0]=='x')
			return +10;
			else if (b[row][0]=='o')
			return -10;
		}
	}

	// Checking for Columns for X or O victory.
	for (int col = 0; col<3; col++)
	{
		if (b[0][col]==b[1][col] && b[1][col]==b[2][col])
		{
			if (b[0][col]=='x')
				return +10;
			else if (b[0][col]=='o')
				return -10;
		}
	}

	// Checking for Diagonals for X or O victory.
	if (b[0][0]==b[1][1] && b[1][1]==b[2][2])
	{
		if (b[0][0]=='x')
			return +10;
		else if (b[0][0]=='o')
			return -10;
	}
	if (b[0][2]==b[1][1] && b[1][1]==b[2][0])
	{
		if (b[0][2]=='x')
			return +10;
		else if (b[0][2]=='o')
			return -10;
	}

	// Else if none of them have won then return 0
	return 0;
}

// Driver code
int main()
{
	char board[3][3] =
	{
		{ 'x', '_', 'o'},
		{ '_', 'x', 'o'},
		{ '_', '_', 'x'}
	};

	int value = evaluate(board);
	printf("The value of this board is %d\n", value);
	return 0;
}

```

关键代码

**function** minimax(board, depth, isMaximizingPlayer):

        **if** current board state is a terminal state :
            **return** value of the board

        **if** isMaximizingPlayer :
            bestVal = -INFINITY 
            **for each** move in board :
                value = minimax(board, depth+1, false)
                bestVal = max( bestVal, value) 
            **return** bestVal

        **else** :
            bestVal = +INFINITY 
            **for each** move in board :
                value = minimax(board, depth+1, true)
                bestVal = min( bestVal, value) 
            **return** bestVal

**We shall be introducing a new function called **findBestMove()**. This function evaluates all the available moves using **minimax()** and then returns the best move the maximizer can make. The pseudocode is as follows :**

    **function** findBestMove(board):
        bestMove = NULL
        **for each** move in board :
            if current move is better than bestMove
                bestMove = current move
        **return** bestMove