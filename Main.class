/*
 * To change this template, choose Tools | Templates
 * and open the template in the editor.
 */
package tictactoe;
import java.util.*;

/**
 *
 * @author tony.tian
 */
public class Main {
    
    public static class gameInterface
    {
        int height = 3;
        int width = 3;
        int[][] board = new int[height][width];
        //int[][] board = {{2,0,0},{1,2,1},{2,0,1}};
        //int[][] board = {{0,0,2},{0,2,0},{2,0,1}};
        int EMPTY = 0;
        int PLAYER1 = 1;
        int PLAYER2 = 2;
        boolean[][] takenSpot = new boolean[height][width];
        
        public gameInterface()
        {
            initialize();
        }
        
        public void initialize()
        {
            for(int r = 0; r < height; r++)
            {
                for(int c = 0; c < width; c++)
                {
                    board[r][c] = EMPTY;
                    
                    takenSpot[r][c] = false;
                }
            }
        }
        
        public void build()
        {
            System.out.print("   1  2  3\n");
            int count = 1;
            for(int r = 0; r < height; r++)
            {
                System.out.print(count + "  ");
                for(int c = 0; c < width; c++)
                {
                    if(board[r][c] == EMPTY)
                    {
                        System.out.print("*");
                        System.out.print("  ");
                    }
                    else if(board[r][c] == PLAYER1)
                    {
                        System.out.print("X");
                        System.out.print("  ");                       
                    }
                    else if(board[r][c] == PLAYER2)
                    {
                        System.out.print("O");
                        System.out.print("  ");
                    }
                }
                System.out.println();
                count++;
            }
        }
        
        public void updateBoard(int player, int placement)
        {
            int count = 9;
            for(int r = 0; r < height; r++)
            {
                for(int c = 0; c < width; c++)
                {
                    if(count == placement)
                    {
                        board[r][c] = player;
                    }
                    count--;
                }
            }
            build();
        }
        
        public void updateBoardTRAINING(int player, int placement)
        {
            int count = 9;
            for(int r = 0; r < height; r++)
            {
                for(int c = 0; c < width; c++)
                {
                    if(count == placement)
                    {
                        board[r][c] = player;
                    }
                    count--;
                }
            }
        }
        
        public int getState()
        {
            int state = 0;
            int index = 8;
            for(int r = 0; r < height; r++)
            {
                for(int c = 0; c < width; c++)
                {
                    if(board[r][c] == PLAYER1)
                    {
                        state += PLAYER1*Math.pow(3, index);
                    }
                    else if(board[r][c] == PLAYER2)
                    {
                        state += PLAYER2*Math.pow(3, index);
                    }
                    index--;
                }
            }
            return state;
        }
        
        public void setTaken(int placement)
        {
            int count = 9;
            for(int r = 0; r < height; r++)
            {
                for(int c = 0; c < width; c++)
                {
                    if(placement == count)
                    {
                        takenSpot[r][c] = true;
                        return;
                    }
                    count--;
                }
            }
        }
        
        public boolean noWinnerYet()
        {
            int rowCount = 0;
            int colCount = 0;
            int diaCount1 = 0;
            int diaCount2 = 0;
            
            for(int r = 0; r < 3; r++)
            {
                for(int c = 0; c < 3; c++)
                {
                    if(board[r][c] == PLAYER1)
                    {
                        colCount++;
                    }
                    else if(board[r][c] == PLAYER2)
                    {
                        colCount--;
                    }                     
                    if(board[c][r] == PLAYER1)
                    {
                        rowCount++;
                    }
                    else if(board[c][r] == PLAYER2)
                    {
                        rowCount--;
                    }
                }
                if(colCount == 3 || colCount == -3 || rowCount == 3 || rowCount == -3)
                {
                    return false;
                }             
                colCount = 0;
                rowCount = 0;
            }
            
            int r = 2;
            int c = 0;
            for(int i = 0; i < 3; i++)
            {
                if(board[i][i] == PLAYER1)
                {
                    diaCount1++;
                }
                else if(board[i][i] == PLAYER2)
                {
                    diaCount1--;
                }             
                if(board[r][c] == PLAYER1)
                {
                    diaCount2++;
                }
                else if(board[r][c] == PLAYER2)
                {
                    diaCount2--;
                }
                r--;
                c++;
            }
            if(diaCount1 == 3 || diaCount1 == -3 || diaCount2 == 3 || diaCount2 == -3)
            {
                return false;
            }
            return true;
        }
        
        public int getEmpty()
        {
            int count = 0;
            for(int r = 0; r < height; r++)
            {
                for(int c = 0; c < width; c++)
                {
                    if(board[r][c] == EMPTY)
                    {
                        count++;
                    }
                }
            }
            return count;
        }
        
        public void play(Scanner input, TicTacToe trainer1, TicTacToe trainer2)
        {
            boolean playGame = true;
            while(playGame)
            {            
                System.out.println("Which player will you be (1/2)?");
                boolean player1 = input.next().equals("1");
                int PLAYER;
                int COMPUTER;

                TicTacToe computer;
                if(player1)
                {
                    computer = trainer2;
                    PLAYER = 1;
                    COMPUTER = 2;
                }
                else
                {
                    computer = trainer1;
                    PLAYER = 2;
                    COMPUTER = 1;
                }

                gameInterface gui = new gameInterface();
                gui.build();

                boolean playersTurn = player1 ? true : false;

                while(gui.noWinnerYet())
                {
                    if(gui.getEmpty() == 0)
                    {
                        System.out.println("Nobody wins");
                        break;
                    }
                    else
                    {
                        int placement;
                        if(playersTurn)
                        {
                            System.out.println("Place your marker(placement #)");
                            placement = input.nextInt();
                            gui.updateBoard(PLAYER, placement);
                            gui.setTaken(placement);
                        }
                        else
                        {
                            System.out.println("Computer's turn");
                            int currState = gui.getState();
                            if(currState < 1)
                            {
                                placement = 5;
                                gui.updateBoard(COMPUTER, placement);
                                gui.setTaken(placement);
                            }
                            else
                            {
                                placement = computer.makeMove(gui.getState(), gui.takenSpot);
                                gui.updateBoard(COMPUTER, placement);
                                gui.setTaken(placement);
                            }                        
                        }
                    }
                    playersTurn = !playersTurn;              
                }
                if(playersTurn)
                {
                    System.out.println("Computer Victory");
                }
                else
                {
                    System.out.println("???");
                    computer.record();
                }
                computer.clear();

                System.out.println("Do you want to lose again?(y/n)");            
                playGame = input.next().equalsIgnoreCase("y");
            }
        }
    }  
    
    

    /**
     * @param args the command line arguments
     */
    public static void main(String[] args) {
        // TODO code application logic here
        
        
        int states = (int)Math.pow(3, 9);
        int max = 9;
        
        System.out.println("How many rounds do I train?");
        Scanner input = new Scanner(System.in);
        int rounds = input.nextInt();
        
        TicTacToe trainer1 = new TicTacToe(states, max);
        TicTacToe trainer2 = new TicTacToe(states, max);
        
        System.out.println("Training...");
        
        int counter = 0;
        
        for(int n = 0; n < rounds; n++)
        {
            //System.out.println("Round: " + counter);
            
            gameInterface gui = new gameInterface();
            
            boolean player1 = true;
            while(gui.noWinnerYet())
            {
                if(gui.getEmpty() == 0)
                {
                    trainer1.clear();
                    trainer2.clear();
                    break;
                }
                else
                {
                    int placement;
                    if(player1)
                    {
                        int currState = gui.getState();
                        if(currState < 1)
                        {
                            placement = 5;
                            gui.updateBoardTRAINING(gui.PLAYER1, placement);
                            gui.setTaken(placement);
                        }
                        else
                        {
                            placement = trainer1.makeMove(gui.getState(), gui.takenSpot);
                            gui.updateBoardTRAINING(gui.PLAYER1, placement);
                            gui.setTaken(placement);
                        }
                    }
                    else
                    {
                        placement = trainer2.makeMove(gui.getState(), gui.takenSpot);
                        gui.updateBoardTRAINING(gui.PLAYER2, placement);
                        gui.setTaken(placement);
                    }
                    player1 = !player1;
                }
            }
            if(player1)
            {
                trainer2.record();
            }
            else
            {
                trainer1.record();
            }
            
            trainer1.clear();
            trainer2.clear();
            
            counter++;
        }
        
        System.out.println("Done");
        
        gameInterface gui = new gameInterface();
        gui.play(input, trainer1, trainer2);
    }
}
