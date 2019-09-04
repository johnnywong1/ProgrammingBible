# Top K Frequent Elements
Java solution:
```
    public static List<Integer> topKFrequent(int[] nums, int k) {
        //O(n) approach
        //build frequency map
        List<Integer> result = new ArrayList<>();
        Map<Integer, Integer> map = new HashMap<>();    //key: nums[i], value: frequency
        for(int i : nums){
            map.put(i, map.getOrDefault(i, 0) + 1);
        }
        PriorityQueue<int[]> heap = new PriorityQueue<>(Comparator.comparingInt(a -> a[0]));
        for(Integer i : map.keySet()){
            heap.offer(new int[]{map.get(i), i});
            if(heap.size() > k){
                heap.poll();
            }
        }
        //make result
        for(int i = 0; i < k; ++ i){
            result.add(heap.poll()[1]);
        }
        Collections.reverse(result);
        return result;
    }
```