# Group anagrams

Java solution:
```
    public static List<List<String>> groupAnagrams(String[] strs) {
        //character count approach
        List<List<String>> result = new ArrayList<>();
        Map<String, List<String>> map = new HashMap<>();    
        //key: char occurrence identifier, val: qualifying words
        for(String word : strs){
            String identifier = assembleIdentifier(word);
            if(map.containsKey(identifier)){
                map.get(identifier).add(word);
            }else{
                List<String> list = new ArrayList<>();
                list.add(word);
                map.put(identifier, list);
            }
        }
        //make result
        for(List<String> anagrams : map.values()){
            result.add(anagrams);
        }
        return result;
    }

    public static String assembleIdentifier(String word){
        StringBuilder result = new StringBuilder();
        int[] charDict = new int[256];
        for(Character c : word.toCharArray()){
            charDict[c] ++;
        }
        for(Integer i : charDict){
            result.append(i);
            result.append('#');
        }
        return result.toString();
    }
```

