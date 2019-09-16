# Lonely Integer
In a array of duplicate integers, find the only one without a pair.

## Solution
It is possible to use a hashmap and linear time, but the space complexity is O(n).
Rather, we can use bit manipulation to get linear space complexity.
Using XOR on all the integers in bit form gives us 0 if 1s are even and 1 if 1s are odd.
This somehow gives the lone integer


```
class Playground {
    public static void main(String[ ] args) {
        int[] arr = new int[]{1,1,2,2,3,3,4,4,5,6,6,7,7};
        int result = 0;
        for (int i : arr){
            result ^=i;    
        }
        System.out.println(result);
    }
}
```
