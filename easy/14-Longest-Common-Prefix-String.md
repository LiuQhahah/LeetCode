## [14. Longest Common Prefix](https://leetcode.com/problems/longest-common-prefix/description/)
------
从一组字符串中找到共有的最长前缀

### 思路1

第一个字符串的第i位与第二字符串的第i位，比较，若相同，i++，并将相同的i位记为`lcp`,使`lcp`与第三位进行比较。

![alt text](https://leetcode.com/media/original_images/14_basic.png "Logo Title Text 1")



    public String longestCommonPrefix(String[] strs) {
        if (strs.length == 0) return "";
        String prefix = strs[0];
        for (int i = 1; i < strs.length; i++)
            while (strs[i].indexOf(prefix) != 0) {//如果stri[i]不包含prefix,那么对prefix去掉没尾字符，再次判断，知道包含为止，此时公共的前缀位profix
                prefix = prefix.substring(0, prefix.length() - 1);
                if (prefix.isEmpty()) return "";
            }        
        return prefix;
    }


- [public int indexOf(String str)
](https://docs.oracle.com/javase/7/docs/api/java/lang/String.html#indexOf(java.lang.String)
返回第一次出现str的位置(index)，如果不包含则返回-1,此题判断条件为是否等于0，如果为0即包含(0以为着有相同的前缀)，("hello,helloo"),`strs[1].indexOf(prefix)==0`

如果不包含，例["hello","hell"]，那就让profix("hello")从没尾减1成"hell"，再次判断，直到包含共同的prefix为止。

- [public String substring(int beginIndex,int endIndex)](https://docs.oracle.com/javase/7/docs/api/java/lang/String.html#substring(int,%20int))

在原有的字符串上返回新的字符串，本题利用的是，自动减末尾的效果
