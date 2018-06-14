## [66. Plus One  ](https://leetcode.com/problems/plus-one/description/)


### Description

给出字符串，求出最后一个单词的长度

### Example:
 
    Input: [1,2,3]
    Output: [1,2,4]
    Explanation: The array represents the integer 123.

    Input: [4,3,2,9]
    Output: [4,3,3,0]
    Explanation: The array represents the integer 4330.


### 错误思路


读取最后一位的值，加1输出，
如果最后一位为9，那么最后一位置0，倒数第二位++；
问题，数组只有一位，如9，倒数第二位溢出，出现异常。


首先判断数组长度，只有一位,可以增加数组的长度，再次输出。

如果是99呢，

### 参考思路

三种可能性，

123——>124；

129——>130;

999——1000；




### 参考Code

```java
class Solution {
    public int[] plusOne(int[] digits) {
           
      
        for(int i = digits.length;i>0;i--){
            if(digits[i-1]<9){
                digits[i-1]++;
                return digits;
            }else{
                digits[i-1] = 0;
                
            }
        }
        int[] newarray = new int[digits.length+1];
        newarray[0]=  1;
        return newarray;
        
        
        
    }
}

```
