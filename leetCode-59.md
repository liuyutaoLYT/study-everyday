```/*
 * @lc app=leetcode.cn id=59 lang=java
 *
 * [59] 螺旋矩阵 II
 */

// @lc code=start
class Solution {
    public int[][] generateMatrix(int n) {
        int [][]result = new int [n][n];
        if(n==0){
            return result;
        }
        int row1 = 0;
        int row2 = result.length-1;
        int col1 = 0;
        int col2 = result[0].length-1;
        int index = 1;
        while(row1<=row2 && col1<=col2){
            if(row1 == row2 && col1==col2){
                result[row1][col2] = index;
            }
            if(row1==row2 && col1<=col2){
                for(int o = col1;o<=col2;o++){
                    result[row1][o] = index;
                    index++;
                }
                return result;
            }
            if(col1==col2 && row1<=row2){
                for(int q = row1;q<=row2;q++){
                    result[q][col1] = index;
                    index++;
                }
                return result;
            }
            for(int i = col1;i<col2;i++){
                result[row1][i] = index;
                index++;
            }
            for(int j = row1;j<row2;j++){
                result[j][col2] = index;
                index++;
            }
            for(int k = col2;k>col1;k--){
                result[row2][k] = index;
                index++;
            }
            for(int l = row2;l>row1;l--){
                result[l][col1] = index;
                index++;
            }
            col1++;
            row1++;
            col2--;
            row2--;
        }
        return result;
    }
}
// @lc code=end


```
