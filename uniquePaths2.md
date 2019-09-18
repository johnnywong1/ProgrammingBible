# Problem
https://leetcode.com/problems/unique-paths-ii/

## Solution
First attempt was to make a separate array, but doing inplace is really efficient.
Basically for each square, the value is the sum of the right and the bottom values


```
class Solution {
    public int uniquePathsWithObstacles(int[][] obstacleGrid) {
        if (obstacleGrid==null || obstacleGrid.length==0)
            return 0;
        int rows = obstacleGrid.length;
        int cols = obstacleGrid[0].length;
        // read right to left, down to up
        for(int i=1;i<=rows;i++){
            for(int j=1;j<=cols;j++){
                // if there is an obstacle (1), set the value to 0
                if(obstacleGrid[rows-i][cols-j]==1){
                    obstacleGrid[rows-i][cols-j] = 0;
                } else if(i==1||j==1){ //edge cases
                    if(j==1&&i!=1){
                        obstacleGrid[rows-i][cols-j] = obstacleGrid[rows-i+1][cols-j];
                    } else if(i==1&&j!=1){
                        obstacleGrid[rows-i][cols-j] = obstacleGrid[rows-i][cols-j+1];                    
                    } else{
                        obstacleGrid[rows-i][cols-j] = 1;// Finish
                    }
                } else{
                    // for each square, the value is the sum of the right and the bottom values
                    obstacleGrid[rows-i][cols-j] = obstacleGrid[rows-i+1][cols-j] + obstacleGrid[rows-i][cols-j+1];
                }
            }
        }
        return obstacleGrid[0][0];
    }
}
```
