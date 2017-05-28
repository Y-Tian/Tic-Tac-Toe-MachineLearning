/*
 * To change this template, choose Tools | Templates
 * and open the template in the editor.
 */
package tictactoe;

import java.util.ArrayList;

/**
 *
 * @author tony.tian
 */
public class TicTacToe {
    
    private TicTacToe.TTTMove[][] bank;
    private ArrayList<int[]> moves;
    int height = 3;
    int width = 3;
    
    public TicTacToe(int state, int max)//start state 0 up to 3^9, max is 9
    {
        bank = new TicTacToe.TTTMove[state][max];
        for(int x = 0; x < state; x++)
        {
            for(int y = 1; y <= max; y++)
            {
                bank[x][y - 1] = new TicTacToe.TTTMove(y, 1);
            }
        }
        moves = new ArrayList();
    }
    
    public int makeMove(int state, boolean[][] takenSpot)
    {
        int weight = weight(state);
        int choice = (int)(Math.random()*weight);
        
        int count = 0;
        int placement = -1;
        
        int i = 0;
        while(true)
        {
            count += bank[state - 1][i].getWeight();
            if(count > choice)
            {
                placement = bank[state - 1][i].getValue();
                if(isEmpty(placement, takenSpot))
                {
                    break;
                }
                else
                {
                    choice = (int)(Math.random()*weight);
                    count = 0;
                    i = -1;
                    placement = -1;
                }
            }     
            i++;
        }
        int[] move = {state, placement};
        moves.add(move);
        return placement;
    }
    
    /*public boolean isEmpty(int loc, int state)
    {
        String base3 = Integer.toString(state, 3);
        return base3.charAt(loc) == '0';
    }*/
    
    public boolean isEmpty(int placement, boolean[][] takenSpot)
    {
        int count = 9;
        for(int r = 0; r < height; r++)
        {
            for(int c = 0; c < width; c++)
            {
                if(placement == count)
                {
                    if(takenSpot[r][c])
                    {
                        return false;
                    }
                    else
                    {
                        return true;
                    }
                }
                count--;
            }
        }
        return true;
    }
    
    public int weight(int state)
    {
        int w = 0;
        for(int n = 0; n < 9; n++)
        {
            w += bank[state - 1][n].getWeight();//n is the number of states
        }
        return w;
    }
    
    public void record()
    {
        for(int i = 0; i < moves.size(); i++)
        {
            int removed = moves.get(i)[1];
            int left = moves.get(i)[0];
            bank[left-1][removed-1].changeWeight(1);
        }
    }
    
    public void clear()
    {
        moves = new ArrayList();
    }
    
    public class TTTMove
    {
        int value;
        int weight;
        
        public TTTMove(int v, int w)
        {
            value = v;
            weight = w;
        }
        
        public int getValue()
        {
            return value;
        }
        
        public int getWeight()
        {
            return weight;
        }
        
        public void changeWeight(int newWeight)
        {
            weight += newWeight;
        }
    }
    
    
    
}
