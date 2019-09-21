# Search in a 2D Matrix
Draft Java solution:
```
    public boolean searchMatrix(int[][] matrix, int target) {
        //binary search approach: binary search every row?
        for(int[] row : matrix){
            if(search(row, 0, matrix[0].length, target)){
                return true;
            }
        }
        return false;
    }

    private boolean search(int[] nums, int left, int right, int target){
        while(left < right){
            int mid = left + (right - left) / 2;
            if(nums[mid] == target){
                return true;
            }else if(nums[mid] > target){
                right = mid;
            }else{
                left = mid + 1;
            }
        }
        return false;
    }
```
PASSED with 6 attemptes. 

More efficient solution:
```
    public boolean searchMatrix(int[][] matrix, int target){
        //best approach: search space reduction
        int row = matrix.length - 1;
        int col = 0;    //search entry point
        while(row >= 0 && col < matrix[0].length){
            if(matrix[row][col] > target){
                -- row;
            }else if(matrix[row][col] < target){
                ++ col;
            }else{
                return true;
            }
        }
        return false;
    }
```
NOTE: choose an entry point `wisely`
