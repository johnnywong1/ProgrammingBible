# Trapping Rain Water
https://leetcode.com/problems/trapping-rain-water
HARD Problem

## Solution
There are a lot of options, including using a stack. But this method uses two pointers on opposite sides, which makes the runtime
linear and constant space complexity.


```
class Solution {
    public int trap(int[] arr) {
        if(arr==null||arr.length==0){
            return 0;
        }
        int result=0, l=0, r=arr.length-1, maxHeight=0;
        while(l<r){
            int elevation = arr[arr[l]<arr[r]?l++:r--];//Finds the minimum wall and the closest section next to it.
            //If the right side has the min wall, we calculate the right side.
            // elevation is the height of the area next to the min wall.
            maxHeight = Math.max(elevation,maxHeight);
            //This is for the possibility that the elevation is higher than the min wall
            //if the elevation is higher than the maxHeight, then the result is elevation - elevation
            result += maxHeight-elevation;
        }
        return result;
    }
}
```
