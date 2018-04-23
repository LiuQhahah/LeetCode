## [27. Remove Element 给定数组以及值，移除在数组中的值 ](https://leetcode.com/problems/remove-element/description/)


### Example:


      nums = [1,2,2]，val = 1

      移除值为1的值，返回数组长度为 2



### 思路

错误思路：记数组长度为`n`,第0个以`val`比，相等，把`n--`,与第2个比，不等`n`不变。

思路：获取几个不同的值，将这些不同的值分别赋给[0],[1],[2],[3]





### code

```java
   class Solution {
    public int removeElement(int[] nums, int val) {
        int i = 0;
        for(int j = 0;j<length;j++){
            if(nums[j]!=val){
                nums[i] = nums[j];
                i++;
            }
        }
        return i;
    }
}
```

### 思路2 

[1,2,3,4,5] val = 1,逐一比较，相同的，n = nums.length就把nums[n-1]赋值给[i],并且n--，否则就是有效数据，那么i++.因为i是有效的数组长度，n为去除垃圾的数组长度，当i= n时，结束循环。

### code
```java
  class Solution {
   public int removeElement(int[] nums, int val) {
    int i = 0;
    int n = nums.length;
    while (i < n) {
        if (nums[i] == val) {
            nums[i] = nums[n - 1];
            // reduce array size by one
            n--;
        } else {
            i++;
        }
    }
       
       System.out.println("i: "+i+" ,n: "+n);
    return n;
}
}
```