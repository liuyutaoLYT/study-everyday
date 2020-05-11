# 给定一个包含非负整数的 m x n 网格，请找出一条从左上角到右下角的路径，使得路径上的数字总和为最小;说明：每次只能向下或者向右移动一步。
```/*
 * @lc app=leetcode.cn id=64 lang=java
 *
 * [64] 最小路径和
 */

// @lc code=start
class Solution {
    public int minPathSum(int[][] grid) {
        int m = grid.length;
        int n = grid[0].length;
        int [][] dp = new int [m][n];
        dp[0][0] = grid[0][0];
        for(int i =1;i<m;i++){
            dp[i][0] = dp[i-1][0]+grid[i][0];
        }
        for(int j = 1;j<n;j++){
            dp[0][j] = dp[0][j-1] + grid[0][j];
        }
        for(int i=1;i<m;i++){
            for(int j =1;j<n;j++){
                if(dp[i-1][j]<dp[i][j-1]){
                    dp[i][j] = dp[i-1][j]+grid[i][j];
                }else{
                    dp[i][j] = dp[i][j-1]+grid[i][j];
                }
            }
        }
        return dp[m-1][n-1];
    }
}
// @lc code=end
//动态规划问题，每走一步都找最小的值 到最后肯定是最小的

```
