# Merge Intervals
Draft Java solution:
```
    public int[][] merge(int[][] intervals) {
        //merge all overlapping intervals
        List<List<Integer>> result = new ArrayList();
        for(int i = 0; i < intervals.length - 1; ++ i){
            if(intervals[i][1] > intervals[i + 1][0]){
                //...;
            }   
        }   
    }
```