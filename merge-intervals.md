# Merge Intervals
Draft Java solution:
```
    public int[][] merge(int[][] intervals) {
        //merge all overlapping intervals
        List<int[]> result = new ArrayList();
        int first = intervals[0][0];
        int last = -1;
        for(int i = 1; i < intervals.length; ++ i){
            if(intervals[i][0] <= intervals[i - 1][1]){
                last = intervals[i][1];  //merge
                //System.out.println("last merged: " + last);
            }else{
                if(first == intervals[0][0]){
                    int[] temp = new int[2];
                    temp[0] = first;
                    temp[1] = last;
                    result.add(temp);
                }
                //append to result
                int[] temp = new int[2];
                first = intervals[i][0];
                last = intervals[i][1];
                temp[0] = first;
                temp[1] = last;
                //System.out.println("first: " + first);
                //System.out.println("last: " + last);
                result.add(temp);
            }
        }
        int[][] realResult = new int[result.size()][2];
        for(int i = 0; i < result.size(); ++ i) {
            realResult[i][0] = result.get(i)[0];
            realResult[i][1] = result.get(i)[1];
        }
        return realResult;
    }
```
FAILED

Passing solution (need to consider intervals such as [1, 6] and [2, 5] -> requires sorting of input intervals by starting time):
```
    private static class IntervalComparator implements Comparator<int[]>{
        @Override
        public int compare(int[] o1, int[] o2) {
            return o1[0] - o2[0];
        }
    }

    public static int[][] merge(int[][] intervals){
        List<int[]> input = new ArrayList<>();
        for(int[] interval : intervals){
            input.add(interval);
        }
        //sort intervals by starting time
        Collections.sort(input, new IntervalComparator());
        List<int[]> temp = new ArrayList<>();
        for(int[] interval: input){
            if(temp.size() == 0 || temp.get(temp.size() - 1)[1] < interval[0]){
                //append to result
                int[] newInterval = new int[2];
                newInterval[0] = interval[0];
                newInterval[1] = interval[1];
                temp.add(newInterval);
            }else{
                //directly modify temp result...
                temp.get(temp.size() - 1)[1] = Math.max(temp.get(temp.size() - 1)[1], interval[1]);
            }
        }
        //make result
        int[][] result = new int[temp.size()][2];
        for(int i = 0; i < temp.size(); ++ i){
            result[i][0] = temp.get(i)[0];
            result[i][1] = temp.get(i)[1];
        }

        return result;
    }
```
https://leetcode.com/problems/merge-intervals/solution/