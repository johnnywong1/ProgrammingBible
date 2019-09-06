# Design Tic Tac Toe

`O(n^2)` check win algorithm (naive):
```
    private int checkWin(int row, int col, int player){
        //O(n^2) algorithm
        //check rows
        int winner = 0;
        for(int i = 1; i < this.grid[0].length; ++ i){
            if(this.grid[row][i] != this.grid[row][i - 1]){
                winner = 0;
                break;  //no one wins
            }
            winner = player;
        }
        //check cols
        for(int i = 1; i < this.grid.length; ++ i){
            if(this.grid[i][col] != this.grid[i - 1][col]){
                winner = 0;
                break;
            }
            winner = player;
        }
        //check diagonal
        if(row == col){
            for(int i = 1; i < this.grid.length; ++ i){
                if(this.grid[i][i] != this.grid[i - 1][i - 1]){
                    winner = 0;
                    break;
                }
                winner = player;
            }
        }
        if(row + col == this.grid.length - 1){
            for(int i = 1; i < this.grid.length; ++ i){
                if(this.grid[this.grid.length - i - 1][i] != this.grid[this.grid.length - i][i - 1]){
                    winner = 0;
                    break;
                }
                winner = player;
            }
        }
        return winner;   //no one wins yet
    }
```

`O(n)` check win algorithm:
```
public class TicTacToe {
    /** Initialize your data structure here. */

    int[][] grid;
    int[] rows;
    int[] cols;
    int diagonal;
    int diagonalRev;

    public TicTacToe(int n) {
        //underlying data structure: 2D char[][]
        this.grid = new int[n][n]; //default: null
        this.rows = new int[n];
        this.cols = new int[n];
        this.diagonal = 0;
        this.diagonalRev = 0;
    }

    /** Player {player} makes a move at ({row}, {col}).
     @param row The row of the board.
     @param col The column of the board.
     @param player The player, can be either 1 or 2.
     @return The current winning condition, can be either:
     0: No one wins.
     1: Player 1 wins.
     2: Player 2 wins. */
    public int move(int row, int col, int player) {
        this.grid[row][col] = player;
        return checkWin(row, col, player);
    }

    private int checkWin(int row, int col, int player){
        int temp = player == 1 ? 1 : -1;
        this.rows[row] += temp;
        this.cols[col] += temp;
        if(row == col){
            this.diagonal += temp;
        }
        if(row == this.grid.length - col - 1){
            this.diagonalRev += temp;
        }
        if(Math.abs(this.rows[row]) == this.grid.length || Math.abs(this.cols[col]) == this.grid.length ||
                Math.abs(this.diagonalRev) == this.grid.length || Math.abs(this.diagonal) == this.grid.length){
            return player;
        }
        return 0;
    }
}
```