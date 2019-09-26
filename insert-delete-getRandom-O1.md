# Insert Delete GetRandom O(1)
Draft Java solution:
```
class RandomizedSet {

    //dual HashMap approach
    Map<Integer, Integer> h1;   //key; val, val: index
    Map<Integer, Integer> h2;   //key: index, val: index

    int index;

    /** Initialize your data structure here. */
    public RandomizedSet() {
        this.h1 = new HashMap();
        this.h2 = new HashMap();
        this.index = 0;
    }
    
    /** Inserts a value to the set. Returns true if the set did not already contain the specified element. */
    public boolean insert(int val) {
        this.h1.put(val, this.index);
        this.h2.put(this.index, val);
        ++ this.index
    }
    
    /** Removes a value from the set. Returns true if the set contained the specified element. */
    public boolean remove(int val) {
        
    }
    
    /** Get a random element from the set. */
    public int getRandom() {
        
    }
}
```
FAILED

Passing solution with HashSet and int[] (ArrayList):
```
class RandomizedSet {

    private List<Integer> list;
    private Map<Integer, Integer> map;
    /** Initialize your data structure here. */
    Random rand;
    public RandomizedSet() {
        list = new ArrayList<>();
        map = new HashMap<>();
        rand = new Random();
    }
    
    /** Inserts a value to the set. Returns true if the set did not already contain the specified element. */
    public boolean insert(int val) {
        
        if (map.containsKey(val) && map.get(val) != -1) return false;
        list.add(val);
        map.put(val, list.size() - 1);
        return true;
    }
    
    /** Removes a value from the set. Returns true if the set contained the specified element. */
    public boolean remove(int val) {
        if (!map.containsKey(val) || map.get(val) == -1) return false;
        swap(list, map.get(val), list.size() - 1, map);
        list.remove(list.size() - 1);
        map.put(val, -1);
        return true;
    }
    
    /** Get a random element from the set. */
    public int getRandom() {
        int idx = rand.nextInt(list.size());
        return list.get(idx);
    }
    
    private void swap(List<Integer> list, int i, int j, Map<Integer, Integer> map) {
        int tmp = list.get(i);
        list.set(i, list.get(j));
        list.set(j, tmp);
        map.put(list.get(i), i);        
    }
}
}
```
Extension: allow duplicate - use `ArrayList` + `HashMap<Integer, Set<Integer>>`
