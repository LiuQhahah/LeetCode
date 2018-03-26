# [ Roman to Integer 将罗马数字转化为整形](https://en.wikipedia.org/wiki/Roman_numerals)


## 罗马字母定义

罗马数字共有7个，即Ⅰ（1）、Ⅴ（5）、Ⅹ（10）、Ⅼ（50）、Ⅽ（100）、Ⅾ（500）和Ⅿ（1000）

## 运算规则，

- 重复数次，表示是这个数的几倍，如III为3
- 左减右加 ：

  - 在较大罗马数字右边记上较小的罗马数字表示大数字加小数字VI为5
  - 在较大的罗马数字的左边记上较小的罗马数字，表示大数字减小数字，如IV为4
  - 左减的数字有限制，仅限I，X,C,例如45 为XLV，不是VL


## 思路1 ：
规律：左边的数字如果小于右边的数字，= 右减左


从左边开始加，遇到了，右边的数大于左边的，那么就要用右边的数减去左边的。

`"DCLIV"`
- 500 + 100
- 600 + 50
- 650 + 1
- 651 + 5 - 1 -1
- 654

[come from ](https://www.youtube.com/watch?v=smZRSRSpe10)

    public static int romanToInt(String s){
      if(s ==null|| s.length() ==0) return 0;
      int res= toNumber(s.charAt(0));
      for(int i=1;i<s.length();i++){
        if(toNumber(s.charAt(i))>toNumber(s.charAt(i-1))){
          res += toNumber(s.charAt(i)) -2 * toNumber(s.charAt(i-1));
        }else{
          res += toNumber(s.charAt(i));
        }
      }
    }

    public static int toNumber(char c){
      int res=  0;
      switch(c){
        case 'I': return 1;
        case 'V': return 5;
        case 'X': return 10;
        case 'L': return 50;
        case 'C': return 100;
        case 'D': return 500;
        case 'M': return 1000;
      }

    }
## 思路2：

左边的和右边的比，

如果左边的大，那么就是加；

如果左边的小那么就是减

    class Solution{
      public int romanToInt(String s){
        Map<Character,Integer> map = HashMap<>();
        map.put('I',1);
        map.put('V',5);
        map.put('X',10);
        map.put('L',50);
        map.put('C',100);
        map.put('D',500);
        map.put('M',1000);

    int len = s.length();
    //从右向左比
    int sum = map.get(s.charAt(len - 1));
    for(int i =  len-2;i>=0;--i){
      //"DCLIV" 先比较I 与 V,左边的I小于V,因此是`减`
      if(map.get(s.charAt(i)<map.get(s.charAt(i+1)))){
        sum -= map.get(s.charAt(i));
      }else{
        sum+= map.get(s.charAt(i))
      }
    }
        return sum;
      }
    }
