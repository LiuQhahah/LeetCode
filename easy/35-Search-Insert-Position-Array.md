## [35. Search Insert Position  ](https://leetcode.com/problems/search-insert-position/description/)


### description

输入排好序的数组，以及一个int类型值，如果int值在数组中，则返回所在位置，如果不在，返回应该插入的位置
### Example:


    Input: [1,3,5,6], 5
    Output: 2

    Input: [1,3,5,6], 2
    Output: 1

    Input: [1,3,5,6], 7
    Output: 4

    Input: [1,3,5,6], 0
    Output: 0


### 思路






### code

```java
class Solution {
    public int searchInsert(int[] nums, int target) {

        int pos = 0;

         if(target<nums[0]){
                pos = 0;

            }else  if(target>nums[nums.length-1]){
                pos = nums.length;

            }else{
        for(int i = 0;i<nums.length;i++){
            if(target == nums[i]){
                pos = i;
                break;
            }else if(target > nums[i]){
               pos = i;

            }else if(target <nums[i]){
                pos = i;
                break;
            }

        }
         }
        return pos;
    }
}
```


### code 2 二分法


```java

class Solution {
       public int searchInsert(int[] A, int target) {
        int low = 0, high = A.length-1;
        while(low<=high){
            int mid = (low+high)/2;
            if(A[mid] == target) return mid;
            else if(A[mid] > target) high = mid-1;
            else low = mid+1;
        }
        return low;
    }
}
```
