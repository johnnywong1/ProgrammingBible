# Sort Colors
Draft Java solution:
```
public void sortColors(int[] nums) {
    //only need to sort 3 colors: 1, 2, 3
    //sort in-place
    //two-pass solution
    int numZeroes = 0;
    int numOnes = 0;
    int numTwos = 0;
    for(Integer i : nums){
        if(i == 0){
            ++ numZeroes;
        }else if(i == 1){
            ++ numOnes;
        }else{
            ++ numTwos;
        }
    }        
    int i = 0;
    while(i < nums.length){
        if(i < numZeroes){
            nums[i] = 0;
        }else if(i < numZeroes + numOnes){
            nums[i] = 1;
        }else{
            nums[i] = 2;
        }
        ++ i;
    }
}
```
ACCEPTED

Optimal Java solution (only uses one pass):
```
  public void sortColors(int[] nums) {
    // for all idx < i : nums[idx < i] = 0
    // j is an index of element under consideration
    int p0 = 0, curr = 0;
    // for all idx > k : nums[idx > k] = 2
    int p2 = nums.length - 1;

    int tmp;
    while (curr <= p2) {
      if (nums[curr] == 0) {
        // swap p0-th and curr-th elements
        // i++ and j++
        tmp = nums[p0];
        nums[p0++] = nums[curr];
        nums[curr++] = tmp;
      }
      else if (nums[curr] == 2) {
        // swap k-th and curr-th elements
        // p2--
        tmp = nums[curr];
        nums[curr] = nums[p2];
        nums[p2--] = tmp;
      }
      else curr++;
    }
  }
```

