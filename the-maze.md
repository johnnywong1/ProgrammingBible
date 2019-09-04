# The Maze
If the ball can choose direction at **every** step:
```
    public boolean hasPath(int[][] maze, int[] start, int[] destination) {
        //DFS approach
        boolean[][] visited = new boolean[maze.length][maze[0].length];
        for(boolean[] row : visited){
            for(boolean b : row){
                b = false;  //init
            }
        }
        return findDes(visited, maze, start, destination);
    }

    public boolean findDes(boolean[][] visited, int[][] maze, int[] currLoc, int[] des){
        int x = currLoc[0];
        int y = currLoc[1];
        if(x < 0 || y < 0 || x >= maze.length || y >= maze[0].length || maze[x][y] == 1 || visited[x][y]){
            return false;   //no path available
        }
        if(x == des[0] && y == des[1]){
            return true;
        }
        visited[x][y] = true;
        boolean result = findDes(visited, maze, new int[]{x + 1, y}, des) ||
                findDes(visited, maze, new int[]{x - 1, y}, des) ||
                findDes(visited, maze, new int[]{x, y + 1}, des) ||
                findDes(visited, maze, new int[]{x, y - 1}, des);
        visited[x][y] = result;
        return result;
    }
```

Otherwise: 

Depth-first search solution
```
    public boolean hasPath(int[][] maze, int[] start, int[] destination) {
        boolean[][] visited = new boolean[maze.length][maze[0].length];
        return findPath(visited, maze, start, destination);
    }

    public boolean findPath(boolean[][] visited, int[][] maze, int[] currLoc, int[] des){
        int x = currLoc[0];
        int y = currLoc[1];
        if(visited[x][y]){
            return false;
        }
        if(x == des[0] && y == des[1]){
            return true;    //reached destination
        }
        int right = x + 1;
        int left = x - 1;
        int up = y + 1;
        int down = y - 1;
        while(right < maze[0].length && maze[x][right] == 0){
            ++ right;
        }
        if(findPath(visited, maze, new int[]{x, right - 1}, des)){
            return true;
        }
        while(left >= 0 && maze[x][left] == 0){
            -- left;
        }
        if(findPath(visited, maze, new int[]{x, left + 1}, des)){
            return true;
        }
        while(up >= 0 && maze[up][y] == 0){
            -- up;
        }
        if(findPath(visited, maze, new int[]{up + 1, y}, des)){
            return true;
        }
        while(down < maze.length && maze[down][y] == 0){
            ++ down;
        }
        if(findPath(visited, maze, new int[]{down - 1, y}, des)){
            return true;
        }
        return false;
    }
```

Breath-first search solution:
```
    public boolean hasPath(int[][] maze, int[] start, int[] destination) {
        //BFS approach: move in all directions at every step
        int[][] directions = {{0, 1}, {0, -1}, {1, 0}, {-1, 0}};
        boolean[][] visited = new boolean[maze.length][maze[0].length];
        Queue<int[]> queue = new LinkedList<>();    //coordinates
        queue.add(start);
        visited[start[0]][start[1]] = true;
        while(!queue.isEmpty()){
            int[] currLoc = queue.remove();
            if(currLoc[0] == destination[0] && currLoc[1] == destination[1]){
                return true;    //reached destination
            }
            for(int[] direction : directions){
                int x = currLoc[0] + direction[0];
                int y = currLoc[1] + direction[1];
                //walk
                while(x >= 0 && y >= 0 && x < maze.length && y < maze[0].length && maze[x][y] == 0){
                    x += direction[0];
                    y += direction[1];
                }
                if(!visited[x - direction[0]][y - direction[1]]){
                    queue.add(new int[]{x - direction[0], y - direction[1]});
                    visited[x - direction[0]][y - direction[1]] = true;
                }
            }
        }
        return false;
    }
```