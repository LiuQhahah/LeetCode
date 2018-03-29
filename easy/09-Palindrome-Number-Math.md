# [Palindrome Number 判断是否为回文数](https://leetcode.com/problems/palindrome-number/description/)


## 描述
判断是回文数的整数

- Example 1:


    Input: 1221
    Output: True
- Example 2:


    Input: -1221
    Output: False

### [定义：](https://zh.wikipedia.org/wiki/%E5%9B%9E%E6%96%87%E6%95%B0)


是指一个像14641这样“对称”的数，即：将这个数的数字按相反的顺序重新排列后，所得到的数和原来的数一样。负数不是回文数


### 思路

- 反转后和自身比较，

- 我的代码：

根据定义先判断是否大于等于0，小于0为假，
根据回文数的定义，将整数的顺序调整，然后与原数据进行比较。

    class Solution {
        public boolean isPalindrome(int x) {
    int before_x = x;
     int result = 0;
    if(x>=0){

        for(;x != 0;x/=10){
            result = result * 10 + x%10;
        }

    }else{
        return false;
    }

    if(result == before_x){
        return true;
    }else{
        return false;
    }
}
}

- [别人的改进代码](https://github.com/Blankj/awesome-java-leetcode/blob/master/note/009/README.md)：

1 变量命名：不是`before_x`而是`copyX`

2 省去result与copyX的判断语句，通过两者运算直接作为return值


膜拜下：

    class Solution {
        public boolean isPalindrome(int x) {
            if (x < 0) return false;
            int copyX = x, reverse = 0;
            while (copyX > 0) {
                reverse = reverse * 10 + copyX % 10;
                copyX /= 10;
            }
            return x == reverse;
        }
    }
