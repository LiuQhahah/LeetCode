## [26. Remove Duplicates from Sorted Array 对重复元素的排序的序列，用后面的元素顶替掉重复的元素 ](https://leetcode.com/problems/remove-duplicates-from-sorted-array/description/)


### Example:


      nums = [1,2,2]

      返回值为 2

### 思路

循环，第一个与第0个比，相等进入下一循环，再比，第2与第1比，不等，把第2的值赋给第1个
#### 算法：nums[1,1,2,2,3,4,4,5]

##### nums[1] == nums[0] i = 0 , j = 2 ,nums = [1,1,2,2,3,4,4,5]
##### nums[2] != nums[0] i = 1 , j = 3 ,nums = [1,2,2,2,3,4,4,5]
##### nums[3] == nums[1] i = 1 , j = 4 ,nums = [1,2,2,2,3,4,4,5]
##### nums[4] != nums[1] i = 2 , j = 5 ,nums = [1,2,3,2,3,4,4,5]
##### nums[5] != nums[2] i = 3 , j = 6 ,nums = [1,2,3,4,3,4,4,5]
##### nums[6] == nums[3] i = 3 , j = 7 ,nums = [1,2,3,4,3,4,4,5]
##### nums[7] != nums[3] i = 4 , j = 8 ,nums = [1,2,3,4,5,4,4,5]


### code
    class Solution {
     public int removeDuplicates(int[] nums) {
     if (nums.length == 0) return 0;
        int i = 0;
        for (int j = 1; j < nums.length; j++) {
            if (nums[j] != nums[i]) {
                i++;
                nums[i] = nums[j];
            }

             for(int m = 0;m<nums.length;m++){
         System.out.print(nums[m]+" ");

         }
             System.out.println();
        }

        return nums.length;
    }
    }
