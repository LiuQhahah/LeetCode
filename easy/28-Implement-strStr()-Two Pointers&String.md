## [28. Implement strStr()  ](https://leetcode.com/problems/implement-strstr/description/)


### Example:


    Input: haystack = "hello", needle = "ll"
    Output: 2



### 思路

整体比较





### code

```java
 class Solution {
    public int strStr(String haystack, String needle) {
        if(needle.length()==0) return 0;
        for(int i = 0;i <= haystack.length()-needle.length();i++){
            if(haystack.substring(i,i+needle.length()).equals(needle)) return i;
        }
        
         return -1;
    }
   
}
}
```

