# [一个数，由数组中两元素相加得到，返回这两个数的偏移量Two Sum](https://leetcode.com/problems/two-sum/description/)
-----------------------------

## 问题描述

给一组int类型数组，如[2,3,4]，在给出一个结果值，如6，求出数组中那两个偏移量的值，相加可以得到结果。

-----------------------------

### Example

    Given nums = [2, 7, 11, 15], target = 18,

    Because nums[1] + nums[2] = 7 + 11 = 18,
    return [1, 2].

### 思路：采用HashMap,
键为目标值减去当前元素值，索引为值，比如`i = 0`时，先判断 `nums[0] = 2`是否在map中，如果不存在，那么插入键值对，`(16,0)`,即 `key = 18-2,value = 0`,之后当`i = 1`时，判断  `nums[1] = 7`在不在map中，不在，则插入键值对`(11,1)`,即`key = 18-7,value = 1`;继续判断，`nums[2]=11`在不在map中，发现在，则返回`i=2`，以及`11`对应的`value`为1，所以输出结果为 `[1,2]`;

### code(java):

```java

    class Solution {
        public int[] twoSum(int[] nums, int target) {
            int len = nums.length;
            HashMap<Integer, Integer> map = new HashMap<>();
            for (int i = 0; i < len; ++i) {
                if (map.containsKey(nums[i])) {
                    return new int[]{map.get(nums[i]), i};
                }
                map.put(target - nums[i], i);
            }
            return null;
        }
    }
```