# [724. Find Pivot Index](https://leetcode.com/problems/find-pivot-index/description/)


### Description

数组nums,找出数组的"中心"的偏移量

元素的左边的总和等于数组右边的和

如果存在多个这样的值，返回左边的。如果没有，返回-1

### Example:
 
    Input: 
    nums = [1, 7, 3, 6, 5, 6]
    Output: 3
    显然1+7+3 = 11 =5+6 ——————>nums[3]返回3

    Input: 
    nums = [1, 2, 3]
    Output: -1
    Explanation: 不存在这样的中心


    Input: 
    nums = [1, 2, 3,4,4,3,2,1]
    Output: -1
    Explanation: 不存在这样的中心


### 方法一

如果第i个位置的元素值为0，下一个元素必然是1比特。

### 自己Code

```java

class Solution {
    public int pivotIndex(int[] nums) {
        int sum = 0, leftsum = 0;
        for (int x: nums) sum += x;
        for (int i = 0; i < nums.length; ++i) {
            if (leftsum == sum - leftsum - nums[i]) return i;
            leftsum += nums[i];
        }
        return -1;
    }
}

```


