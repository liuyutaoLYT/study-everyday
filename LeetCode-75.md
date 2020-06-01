给定一个包含红色、白色和蓝色，一共 n 个元素的数组，原地对它们进行排序，使得相同颜色的元素相邻，并按照红色、白色、蓝色顺序排列。
```
/*
 * @lc app=leetcode.cn id=75 lang=java
 *
 * [75] 颜色分类
 */

// @lc code=start
class Solution {
    public void sortColors(int[] nums) {
        int p = 0;
        int max = nums.length-1;
        int curr = 0;
        int temp=0;
        while(curr<=max){
            if(nums[curr]==0){
                temp = nums[p];
                nums[p++] = nums[curr];
                nums[curr++] = temp;
            }else if(nums[curr]==2){
                temp = nums[curr];
                nums[curr] = nums[max];
                nums[max--] = temp;
            }else{
                curr++;
            }
        }
    }

}
// @lc code=end


```
