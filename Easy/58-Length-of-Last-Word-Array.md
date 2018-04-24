## [58. Length of Last Word  ](https://leetcode.com/problems/length-of-last-word/description/)


### Description

给出字符串，求出最后一个单词的长度

### Example:

        Input: "Hello World"
        Output: 5



### 思路


先把字符串的首尾的空格去除，然后，从最后一个字符遍历，出现空格，就返回；

字符串为空，直接返回0



### Code

```java
class Solution {
    public int lengthOfLastWord(String s) {
        int pos = 0;
        s = s.trim();
        if(s==" ") return 0;
        int i = s.length();
        while(i!=0&&s.charAt(--i)!=' '){
           
            pos++;
        }

        return pos;
    }
}

```

### Code 2

```java
public int lengthOfLastWord(String s) {
    return s.trim().length()-s.trim().lastIndexOf(" ")-1;
}
```