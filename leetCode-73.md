给定一个 m x n 的矩阵，如果一个元素为 0，则将其所在行和列的所有元素都设为 0。请使用原地算法。
```
/*
 * @lc app=leetcode.cn id=73 lang=java
 *
 * [73] 矩阵置零
 */

// @lc code=start
class Solution {
    public void setZeroes(int[][] matrix) {
        Set<Integer> rows = new HashSet<Integer>();
        Set<Integer> cols = new HashSet<Integer>();
        for(int i = 0 ; i<matrix.length;i++){
            for(int j =0;j<matrix[0].length;j++){
                if(matrix[i][j]==0){
                    rows.add(i);
                    cols.add(j);
                }
            }
        }
        for(int i = 0 ; i<matrix.length;i++){
            for(int j =0;j<matrix[0].length;j++){
                if(rows.contains(i) || cols.contains(j)){
                    matrix[i][j]=0;
                }
            }
        }
        
    }
}
// @lc code=end


```
