## [53. Maximum Subarray  ](https://leetcode.com/problems/maximum-subarray/description/)


### description

已知一个整型数组nums,找出子串中(至少一个元素)最大和


### Example:

    Input: [-2,1,-3,4,-1,2,1,-5,4],
    Output: 6
    Explanation: [4,-1,2,1] has the largest sum = 6.



### 思路






### code

```java
class Solution {
   public int maxSubArray(int[] nums) {
       //max 最大值为第一个元素的值
        int sum = 0, max = nums[0];
       //初始化
        for(int i = 0; i < nums.length; i++) {
            //和加上下一个位置的数组元素 
            sum += nums[i];
            //如果sum总和大于最大的值，那么就把总和给max.即加上nums[i]的sum,是否与之前的max的比较，
            if(sum > max) max = sum;
            //加了一个nums[i]后，sum小于0就重置
            if (sum < 0) sum = 0;
        }
        return max;
    }
}
```
