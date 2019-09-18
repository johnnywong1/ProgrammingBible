# Flood Fill
https://leetcode.com/problems/flood-fill/

## Solution
Recursion, fastest
Just recurse on the four sides of the initial square. Break if it goes past the bounds OR if not the right init color 
Note: To break the recursion after changing the color we break if the square is the same color as the new color, which means it was recently filled


```
class Solution {
    public int[][] floodFill(int[][] image, int sr, int sc, int newColor) {
        int initColor = image[sr][sc];
        fillBoi(image, sr, sc, initColor, newColor);
        return image;
    }
    public static void fillBoi(int[][] image, int sr, int sc, int initColor, int newColor){
        if(sr<0 || sr>=image.length || sc<0 || sc>=image[0].length || image[sr][sc]!=initColor || image[sr][sc]==newColor){
            return;
        }
        image[sr][sc] = newColor;
        fillBoi(image,sr, sc-1, initColor, newColor);
        fillBoi(image,sr+1, sc, initColor, newColor);
        fillBoi(image,sr, sc+1, initColor, newColor);
        fillBoi(image,sr-1, sc, initColor, newColor);
    }
}
```
