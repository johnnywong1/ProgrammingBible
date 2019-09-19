# https://leetcode.com/problems/sum-of-even-numbers-after-queries

## O(n) runtime
Original brute force, change the value and then calculate the sum of the even numbers, add to returned array
    
Optimized solution:  
Find the original sum first, as you iterate through the changes do two things:  
If the old value is even, remove it from the sum as you dont need it anymore  
If the new value is even, add it to the sum.



```
class Solution {
    public int[] sumEvenAfterQueries(int[] A, int[][] queries) {
        int sum = 0, ansIndex=0;
        int[] ans = new int[queries.length];
        for(int i=0;i<A.length;i++){
            if(A[i]%2==0){
                sum+=A[i];
            }
        }
        for(int[] query : queries){
            int myIndex = query[1];
            if(A[myIndex]%2==0){ //if the original is even
                sum-=A[myIndex]; //remove it from the sum
            }
            A[myIndex] += query[0];//update the value
            
            if(A[myIndex]%2==0){ //now, if the new value is even
                sum+=A[myIndex]; //add it to the sum
            }
            ans[ansIndex]=sum;
            ansIndex++;
        }
        
        return ans;
    }
}
```
