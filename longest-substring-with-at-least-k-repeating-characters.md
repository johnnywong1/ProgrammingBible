# Longest Substring with At Least K Repeating Characters
Draft Java solution:
```
    public int longestSubstring(String s, int k) {
        
    }
```
FAILED

Passing solution (divide and conquer approach):
```
    public int longestSubstring(String s, int k){
        return count(s, 0, s.length() - 1, k);
    }

    private int count(String s, int left, int right, int k){
        //base case
        if(right - left + 1 < k){
            return 0;
        }
        //recount
        int[] count = new int[26];
        //make count map
        for(int i = left; i <= right; ++ i){
            count[(int) (s.charAt(i) - 'a')] ++;
        }

        //find "separator"
        for(int i = 0; i < 26; ++ i){
            if(count[i] > 0 && count[i] < k){
                //iteratie again

                for(int j = left; j <= right; ++ j){
                    if(s.charAt(j) == (char)('a' + i)){
                        return Math.max(count(s, left, j - 1, k), count(s, j + 1, right, k));
                    }
                }
            }
        }
        return right - left + 1;
    }
```

Dennis' (unfortunately naive and definitely not correct) solution:
```
    public int longestSubstring(String s, int k) {
        char currentFinder = s.charAt(0);
        int longest = 0;
        int currentStreak = 0;
        currentStreak++;
        for (int i=1; i<s.length(); i++) {
            if (s.charAt(i) == currentFinder) {
                currentStreak++;
            }
            else {
                if (currentStreak > longest) {
                    longest = currentStreak;
                }
                currentStreak = 1;
                currentFinder = s.charAt(i);
            }
        }
    }
```