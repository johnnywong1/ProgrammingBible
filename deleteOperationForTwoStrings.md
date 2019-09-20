#  Delete Operation for Two Strings
https://leetcode.com/problems/delete-operation-for-two-strings/

## Solution
Very interesting solution, I did not make this but I want to explain.  
This is done in O(m*n) time, where m and n are the lengths of the words  
Done using dynamic programming, holding the values in a int[][] (array of arrays)  
Extra large array to avoid edge cases
If the values are matching, then it is part of the substring so the value goes up
Otherwise, retain the cumulative sum by carrying over gridsquares.


```

class Solution {
    public int minDistance(String word1, String word2) {
        int wordMap[][] = new int[word1.length()+1][word2.length()+1]; // array of arrays, storage for dp
        for(int i = 1; i <= word1.length(); i++){ // read through first string
            for(int j = 1; j <= word2.length(); j++){ // read through second string
                int gridValue = 0; //
                if(word1.charAt(i-1) == word2.charAt(j-1)){ //if equal char
                    gridValue = wordMap[i-1][j-1] + 1; // increase the max
                }else{ 
                    gridValue = Math.max(wordMap[i-1][j], wordMap[i][j-1]);//unaffected by diff chars in between, but affected by order
                }
                wordMap[i][j] = gridValue;//this if/else could be broken down to inplace ternary value, but i split it up so it is easier to understand
            }
        }
        return word1.length() + word2.length() - 2 * wordMap[word1.length()][word2.length()];
        //takes the longest subset and changes it to the number of chars needed to be removed.
    }
}

```
