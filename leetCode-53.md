```
/*
 * @lc app=leetcode.cn id=53 lang=java
 *
 * [53] 最大子序和
 */

// @lc code=start
class Solution {
    public int maxSubArray(int[] nums) {
        if(nums.length==1){
            return nums[0];
        }
        int left = 0;
        int right = nums.length;
        int result = nums[0];
        
        while(left < right){
            int num = 0;
            for(int i = left;i<right;i++){
                num+= nums[i];   
                if(num>result){
                    result = num;
                }             
            }
            left++;
        }
        return result;
    }
}
// @lc code=end

//暴力法
```
```
//动态规划
class Solution {
    public int maxSubArray(int[] nums) {
        if(nums.length==0){
            return 0;
        }
        int []dp = new int[nums.length];//动态规划数组，记录前i个连续数字的最大值
        int result = nums[0];
        dp[0] = nums[0];
        for(int i = 1;i<nums.length;i++){
            int dppre = dp[i-1]>0?dp[i-1]:0;
            dp[i] = dppre+nums[i];
            result = result>dp[i]?result:dp[i];
        }
        return result;
    }
}
```
