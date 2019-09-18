# Problem
https://leetcode.com/problems/unique-paths-ii/

## Solution
Brute forced right now, for optimizations:
remove the extra array,


```
class Solution {
    public int uniquePathsWithObstacles(int[][] obstacleGrid) {
        if (obstacleGrid==null || obstacleGrid.length==0)
            return 0;
        // make a new array with same dimensions
        int rows = obstacleGrid.length;
        int cols = obstacleGrid[0].length;
        int[][] arrMap = new int[rows][cols];
        // read right to left, down to up
        for(int i=1;i<=rows;i++){
            for(int j=1;j<=cols;j++){
                // if there is an obstacle (1), set the value in the new int[][] to 0
                if(obstacleGrid[rows-i][cols-j]==1){
                    arrMap[rows-i][cols-j] = 0;
                } else if(i==1||j==1){ //edge cases
                    if(j==1&&i!=1){
                        arrMap[rows-i][cols-j] = arrMap[rows-i+1][cols-j];
                    } else if(i==1&&j!=1){
                        arrMap[rows-i][cols-j] = arrMap[rows-i][cols-j+1];                    
                    } else{
                        arrMap[rows-i][cols-j] = 1;// Finish
                    }
                } else{
                    // for each square, the value is the sum of the right and the bottom values
                    arrMap[rows-i][cols-j] = arrMap[rows-i+1][cols-j] + arrMap[rows-i][cols-j+1];
                }
            }
        }
        return arrMap[0][0];
    }
}
```
