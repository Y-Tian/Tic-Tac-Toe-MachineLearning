# Machine-Learning
A Tic Tac Toe AI project based on understanding the fundamentals of machine learning in Java.

Run the Main class to begin the Tic Tac Toe simulation against an AI.
This project was compiled in the NetBeans compiler and uses its console to illustrate how the AI makes its moves.
To excute commands for the simulator, type in the console when it's your turn and it will print out the new board state.

The TicTacToe class is the class that stores the AI's knowledge. How machine learning works is that the AI begins by having no values stored in its memory, which is an array of moves available. The moves that the AI can make each weigh a value of zero, so when it randomly selects a move to make, all available moves are taken into account equally. Then, as the AI continues to play against itself, everytime the AI wins a match, the board state at each player's turn is recorded.

This way, when it faces off against a real player, wherever the player makes a move, the weight of the move that the AI can make in order to win will be biased and will be more likely to make that game-winning move.

Comments and criticism welcome!
