## [20. Valid Parentheses](https://leetcode.com/problems/valid-parentheses/description/)

### 括号要成对出现，否则为错
``'(', ')', '{', '}', '[' and ']'``


### 思路
我们可以用栈来解决这个问题，当出现左括号的时候入栈，当遇到右括号时，判断栈顶的左括号是否何其匹配，不匹配的话直接返回 false 即可，
[参考](https://github.com/Blankj/awesome-java-leetcode/blob/master/note/020/README.md)


[API:stack](https://docs.oracle.com/javase/8/docs/api/java/util/Stack.html#method.summary)

    class Solution {
        public boolean isValid(String s) {

         if(s.length() % 2 == 1)
            return false;

         Stack<Character> stack = new Stack<Character>();
    	 for(int i = 0; i < s.length(); i++)
    	 {
    		if(s.charAt(i) == '(')
    		{
    			stack.push(')');
    		}
    		else if(s.charAt(i) == '{')
    		{
    			stack.push('}');
    		}
    		else if(s.charAt(i) == '[')
    		{
    			stack.push(']');
    		}
    		else if(stack.isEmpty() || stack.pop() != s.charAt(i))
    			return false;
    	 }
    	 return stack.isEmpty();
    }
    }
