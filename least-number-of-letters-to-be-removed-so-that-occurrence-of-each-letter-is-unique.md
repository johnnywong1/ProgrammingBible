# Least Number of Letters to be Removed so that Occurrence of Each Letter is Unique

`leetcode` -> `2`

Draft Java solution:
```
public int remove(String s){
    //int[256] dict approach
    int result = 0;
    if(s.length() == 0 || s.length() == 1){
        return result;
    }
    int[] dict = new int[256];
    for(Character c : s.toCharArray()){
        dict[c] ++;
    }
    for(Integer i : dict){
        if(i != 0){
            result += Math.abs(i - 1);
        }
    }
    return result;
}
```
PASSED with custom test cases