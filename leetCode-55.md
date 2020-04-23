```
/*
 * @lc app=leetcode.cn id=55 lang=java
 *
 * [55] 跳跃游戏
 */

// @lc code=start
class Solution {
    public boolean canJump(int[] nums) {
        int n = nums.length;
        int maxRight = 0;
        for(int i = 0;i<n;i++){
            if(i<=maxRight){
                maxRight = Math.max(maxRight,nums[i]+i);
                if(maxRight>=n-1){
                    return true;
                }
            }
        }
        return false;
    }
}
// @lc code=end
贪心算法 维护一个maxRight 看maxRight是否能大于这个数组的长度

```
