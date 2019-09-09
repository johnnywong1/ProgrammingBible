# Contains Duplicates III
TreeSet (Java) approach:
```
    public boolean containsNearbyAlmostDuplicate(int[] nums, int k, int t) {
        //absolute difference between nums[i] and nums[j] <= t
        //absolute difference between i and j <= k;
        //TreeSet approahc (official solution)
        TreeSet<Integer> set = new TreeSet<>();
        for(int i = 0; i < nums.length; ++ i){
            Integer s = set.ceiling(nums[i]);
            //successor of s
            if(s != null && s <= nums[i] + t){
                return true;
            }
            //predecessor of s
            Integer g = set.floor(nums[i]);
            if(g != null && nums[i] <= g + t){
                return true;
            }
            set.add(nums[i]);
            if(set.size() > k){
                set.remove(nums[i - k]);    //remove oldest node from tree
            }
        }
        return false;
    }
```