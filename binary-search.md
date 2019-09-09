# Binary Search
Very straightforward binary search Java approach:
```
    public static int search(int[] nums, int target) {
        //standard binary search for target number
        int left = 0;
        int right = nums.length - 1;
        while(left <= right){
            int mid = left + (right - left) / 2;
            if(nums[mid] < target){
                left = mid + 1;
            }else if(nums[mid] > target){
                right = mid - 1;
            }else{
                return mid;
            }
        }
        return -1;  //does not exist in array
    }
```