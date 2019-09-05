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