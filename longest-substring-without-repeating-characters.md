# Longest Substring without Repeating Characters
Draft Java solution:
```
    public int lengthOfLongestSubstring(String s) {
        //sliding window + count dict approach
        int[] count = new int[26];
        int result = 0;
        int i = 0;
        int j = 0;
        for(i = 0; i < s.length(); ++ i){
            count[(int) s.charAt(i) - 'a'] ++;
            for(int k = 0; k < 26; ++ k){
                if(count[k] > 1){
                    result = Math.max(i - j, result);
                    j = i;
                    //reset mem
                    Arrays.fill(count, 0);  //start recount
                }
            }
        }   
        return result;
    }
```
FAILED

Should not remove whole "chunk" of substring once a duplicate is found (need to search for it)

Passing solution with improved bool mem:
```
    public int lengthOfLongestSubstring(String s) {
        if(s==null){
            return 0;
        }
        boolean[] flag = new boolean[256];
    
        int result = 0;
        int start = 0;
        char[] arr = s.toCharArray();
    
        for (int i = 0; i < arr.length; i++) {
            char current = arr[i];
            if (flag[current]) {
                result = Math.max(result, i - start);
                for (int k = start; k < i; k++) {
                    if (arr[k] == current) {
                        start = k + 1; 
                        break;
                    }
                    flag[arr[k]] = false;
                }
            } else {
                flag[current] = true;
            }
        }
        result = Math.max(arr.length - start, result);
        return result;
    }
```