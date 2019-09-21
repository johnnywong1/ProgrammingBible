# Partition array into 3 parts 
https://leetcode.com/problems/partition-array-into-three-parts-with-equal-sum/


```
class Solution {
    public boolean canThreePartsEqualSum(int[] A) {
        int totalSum = 0;
        for(int i : A){
            totalSum+=i;
        }
        int numParts = 0;//want it to be three
        int runningSum = 0; //want it to be totalSum / 3
        if(totalSum % 3 != 0)return false;//otherwise it is impossible to get three equal parts
        for(int i : A){
            runningSum+=i;//order matters for the last one

            if(runningSum == totalSum/3){
                numParts++;
                runningSum=0;
            }

        }
        if(numParts==3) return true;
        else return false;
    }
}
```
