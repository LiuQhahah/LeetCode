## [14. 返回两个字符串的公共前缀Longest Common Prefix](https://leetcode.com/problems/longest-common-prefix/description/)
------
从一组字符串中找到共有的最长前缀

### 思路1

第一个字符串的第i位与第二字符串的第i位，比较，若相同，i++，并将相同的i位记为`lcp`,使`lcp`与第三位进行比较。

![alt text](https://leetcode.com/media/original_images/14_basic.png "Logo Title Text 1")


//如果stri[i]不包含prefix,那么对prefix去掉没尾字符，再次判断，知道包含为止，此时公共的前缀位profix

    public String longestCommonPrefix(String[] strs) {
        if (strs.length == 0) return "";
        String prefix = strs[0];
        for (int i = 1; i < strs.length; i++)
            while (strs[i].indexOf(prefix) != 0) {
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


### 思路2   
#### 算法：垂直比较，先取string1[0],与string2[0],string3[0],,,,stringi[0]比较，将string1.substring(0,0)作为返回值；

#### 再次循环string1[1]与string2[1],string3[1],,,stringi[1]比较，如果i个都相等，则返回string1.substring(0,1);

#### 。。。。

#### 当string1[j]与string2[j],string3[j]，，，stringi[j]中的一个不等时，退出循环运行结束。

-------------------------

  string1 = "abcccc"

  string2 = "abcddd"

  string3 = "abcdeee"

  .....

  stringi = "abckkkkk"


----------------------------


#### code

>返回就意味着结束，本题当不相等时，就return


    class Solution {
      public String longestCommonPrefix(String[] strs) {
          for(int i = 0;i< strs[0].length();i++){
          char c =  strs[0].charAt(0);
          for(int j = 1;j<strs.length;j++){
            if(c != strs[j].charAt(i) || i == strs[j].length()){
              return strs[0].substring(0,i);
            }
          }
        }

        return strs[0];
    }
    }

**Note：** [字符串的长度strs[0].length()](https://docs.oracle.com/javase/7/docs/api/java/lang/String.html#method_summary)

**Note:**  [数组长度strs.length](https://stackoverflow.com/questions/8755812/array-length-in-java)




### 思路3

#### 算法：递归，4个字符串["leetcode","leet","lee","le"]，分成两组`left:`["leetcode","leet"],`right:`["lee","le"]，

#### 一组两个字符串进行比较，`left`得到["leet"],`right`得到["le"],将获取的再次比较得到["le"]
![alt text](https://leetcode.com/media/original_images/14_lcp_diviso_et_lmpera.png "Logo Title Text 1")

#### code


    public String longestCommonPrefix(String[] strs) {
        if (strs == null || strs.length == 0) return "";    
            return longestCommonPrefix(strs, 0 , strs.length - 1);
    }

    private String longestCommonPrefix(String[] strs, int l, int r) {
        if (l == r) {
            return strs[l];
        }
        else {
            int mid = (l + r)/2;
            String lcpLeft =   longestCommonPrefix(strs, l , mid);
            String lcpRight =  longestCommonPrefix(strs, mid + 1,r);
            return commonPrefix(lcpLeft, lcpRight);
       }
    }

    String commonPrefix(String left,String right) {
        int min = Math.min(left.length(), right.length());       
        for (int i = 0; i < min; i++) {
            if ( left.charAt(i) != right.charAt(i) )
                return left.substring(0, i);
        }
        return left.substring(0, min);
    }
