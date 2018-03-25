## [反整数Reverse Integer](https://leetcode.com/problems/reverse-integer/description/)

## 描述：

给出32位有符号整数，反转数字，

### Example

One:

    Input: 123
    Output:  321
Two:

    Input: -123
    Output: -321
Three:

    Input: 120
    Output: 21


**注：**当它的逆序整型数溢出的话，那么就返回 0

### 思路：123,除10余3，12除10余2，1除10余1,对于溢出情况，将数据类型保存为long,比较和整形的范围，超出为0

### code:
    class Solution {
        public int reverse(int x) {
            long res = 0;
            for (; x != 0; x /= 10)
                res = res * 10 + x % 10;
            return res > Integer.MAX_VALUE || res < Integer.MIN_VALUE ? 0 : (int) res;
        }
    }
