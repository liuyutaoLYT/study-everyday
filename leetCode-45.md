给定一个非负整数数组，你最初位于数组的第一个位置。

数组中的每个元素代表你在该位置可以跳跃的最大长度。

你的目标是使用最少的跳跃次数到达数组的最后一个位置。


```
/*
 * @lc app=leetcode.cn id=45 lang=java
 *
 * [45] 跳跃游戏 II
 */

// @lc code=start
class Solution {
    public int jump(int[] nums) {
        
        int result = 0;
        int i = 0;
        if(nums.length==1){
            return result;
        }
        while(i<nums.length){
            int max = 0;
            int index = i+1;
            if(i+nums[i]+1>=nums.length){
                result++;
                return result;
            }
            for(int j = i+1;j<=i+nums[i];j++){
                if(j+nums[j]>=max){
                    max = j+nums[j];
                    index = j;
                }
            }
            i = index;
            result++;
        }
        return result;
    }
}
// @lc code=end
```
贪心算法 尽可能的往前走
