# Search in a 2D Matrix II
Draft Java solution:
```
    public boolean searchMatrix(int[][] matrix, int target) {
        //just replicate I's solution?
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
PASSED with 1 attempt. 

More efficient solution:
```

```