# Add to array
https://leetcode.com/problems/add-to-array-form-of-integer/

## Solution
Interesting thing done here is instead of dividing by digits of K and holding a carry value,  
K itself was the carry  
Just add sum and all of K

```
class Solution {
    public List<Integer> addToArrayForm(int[] A, int K) {
        List<Integer> ans = new LinkedList<Integer>();//Option between ArrayList and LinkedList
        //LinkedList has faster insertion time, which is used here
        for(int i=0;i<A.length;i++){
            ans.add(0,(A[A.length-1-i]+K)%10);
            K = (A[A.length-1-i]+K)/10;
        }
        
        while(K>0){
            ans.add(0,K%10);
            K/=10;
        }
        //Collections.reverse(ans);//can do this OR add at index 0, slower than add at 0
        return ans;
    }
}
```
