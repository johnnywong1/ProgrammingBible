# Task Scheduler
Draft Java solution:
```
    public int leastInterval(char[] tasks, int n) {
        //avoid executing same task together as much as possible
        //max heap solution
        PriorityQueue<char[]> heap = new PriorityQueue<char[]>(tasks.length, new Comparator<char[]>(){
            public int compare(char[] a1, char[] a2){
                return Character.getNumericValue(a1[1]) - Character.getNumericValue(a2[1]);
            }
        });

        //fill the heap
        Map<Character, Integer> map = new HashMap();
        for(Character c : tasks){
            map.put(c, map.getOrDefault(c, 0) + 1);
        }
        for(Character c : map.keySet()){
            char[] temp = new char[2];
            temp[0] = c;
            temp[1] = Character.forDigit(map.get(c));
            heap.push(temp);
        }

        //make result
        int result = 0;
        while(!heap.isEmpty()){
            char[] curr = heap.pop();
            ++ result;
            curr[1] --;
            if(heap.isEmpty()){
                result += n;    //add idle time
            }
            ...
        }
    }
```
FAILED. WRONG UNDERSTANDING OF PROBLEM...

Passing solution:
```
    public int leastInterval(char[] tasks, int n){
        int[] map = new int[26];
        for(Character c : tasks){
            map[c - 'A'] ++ ;
        }
        PriorityQueue<Integer> queue = new PriorityQueue<>(26, Collections.reverseOrder());
        for(Integer f : map){
            if(f > 0){
                queue.add(f);
            }
        }
        int time = 0;
        while(!queue.isEmpty()){
            int i = 0;
            List<Integer> temp = new ArrayList();
            while(i <= n){
                if(!queue.isEmpty()){
                    if(queue.peek() > 1){
                        temp.add(queue.poll() - 1);
                    }else{
                        queue.poll();   //task used up
                    }
                }
                ++ time;
                if(queue.isEmpty() && temp.size() == 0){
                    break;
                }
                ++ i;
            }
            for(int l : temp){
                queue.add(l);
            }
        }
        return time;
    }
```