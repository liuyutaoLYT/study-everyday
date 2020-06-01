给定一个包含红色、白色和蓝色，一共 n 个元素的数组，原地对它们进行排序，使得相同颜色的元素相邻，并按照红色、白色、蓝色顺序排列。
/*
 * @lc app=leetcode.cn id=75 lang=java
 *
 * [75] 颜色分类
 */

// @lc code=start
class Solution {
    public void sortColors(int[] nums) {
        if(nums.length==0){
            return ;
        }
        int zeroNum = 0;
        int oneNum = 0;
        int twoNum = 0;
        for(int i =0;i<nums.length;i++){
            if(nums[i]==0){
                zeroNum++;
            }else if(nums[i]==1){
                oneNum++;
            }else{
                twoNum++;
            }
        }
        zeroNum--;
        for(int i = 0;i<nums.length;i++){
            if(i<=zeroNum){
                nums[i] = 0;
                continue;
            }
            if(i>zeroNum && i<=oneNum+zeroNum){
                nums[i] = 1;
                continue;
            }
            if(i>oneNum+zeroNum && i<=oneNum+zeroNum+twoNum){
                nums[i] = 2;
                continue;
            }
        }
    }
}
// @lc code=end

