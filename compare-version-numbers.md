# Compare Version Numbers
Java approach (accumulative token):
```
    public static int compareVersion(String version1, String version2) {
        //ignore leading zeroes
        //dual pointer approach
        int ptr1 = 0;
        int ptr2 = 0;
        int i1 = 0;
        int i2 = 0;
        while(ptr1 < version1.length() || ptr2 < version2.length()){
            while(ptr1 < version1.length() && version1.charAt(ptr1) != '.'){
                i1 += i1 * 10 + Character.getNumericValue(version1.charAt(ptr1 ++));
                //System.out.println(i1);
            }
            while(ptr2 < version2.length() && version2.charAt(ptr2) != '.'){
                i2 += i2 * 10 + Character.getNumericValue(version2.charAt(ptr2 ++));
                //System.out.println(i2);
            }
            if(i1 > i2){
                return 1;
            }else if(i2 > i1){
                return -1;
            }
            i1 = 0;
            i2 = 0;
            ++ ptr1;
            ++ ptr2;
        }
        return 0;
    }
```