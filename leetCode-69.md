/*
 * @lc app=leetcode.cn id=69 lang=java
 *
 * [69] x 的平方根
 */

// @lc code=start
class Solution {
    public int mySqrt(int x) {
        int l = 0, r = x, result = -1;
        while (l <= r) {
            int mid = l + (r - l) / 2;
            if ((long)mid * mid <= x) {
                result = mid;
                l = mid + 1;
            }
            else {
                r = mid - 1;
            }
        }
        return result;
    }
}
// @lc code=end

平方根
二分查找嘛
