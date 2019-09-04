# Word Search
Java DFS solution:
```
    public boolean exist(char[][] board, String word) {
        //search for a single word in 2D char array
        //need a visited array
        boolean[][] visited = new boolean[board.length][board[0].length];
        for(boolean[] row : visited){
            for(boolean b : row){
                b = false;  //init
            }
        }
        for(int i = 0; i < board.length; ++ i){
            for(int j = 0; j < board[0].length; ++ j){
                if(board[i][j] == word.charAt(0)){
                    if(search(visited, board, word, i, j)){
                        return true;
                    }
                }
            }
        }
        return false;
    }

    public boolean search(boolean[][] visited, char[][] board, String wordToSearchFor, int row, int col){
        //boundary conditions

        if(row < 0 || col < 0 || row >= board.length || col >= board[0].length ||
                board[row][col] != wordToSearchFor.charAt(0) ||
                visited[row][col]){
            return false;
        }
        if(board[row][col] == wordToSearchFor.charAt(0)){
            if(wordToSearchFor.length() == 1){
                return true;
            }else{
                visited[row][col] = true;
            }
        }
        //search all four directions
        boolean result = search(visited, board, wordToSearchFor.substring(1), row + 1, col) ||
                search(visited, board, wordToSearchFor.substring(1), row - 1, col) ||
                search(visited, board, wordToSearchFor.substring(1), row, col + 1) ||
                search(visited, board, wordToSearchFor.substring(1), row, col - 1);
        visited[row][col] = result;   //reset visited status
        return result;
    }
```