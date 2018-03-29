## [20. 判断括号是否成对出现Valid Parentheses](https://leetcode.com/problems/valid-parentheses/description/)

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


### 思路2

根据，括号顺序先是`(,{,[`,先把这些内容放到栈里，然后遇到`)}]`时，就出栈，判断栈中内容是不是`({[`

    public boolean isValid(String s) {
        Stack<Character> stack = new Stack<>();
        for (int i = 0; i < s.length(); i++) {
            switch (s.charAt(i)) {
                case '(':
                    stack.push('(');
                    break;
                case '{':
                    stack.push('{');
                    break;
                case '[':
                    stack.push('[');
                    break;
                case ')':
                    if (stack.size() == 0 || stack.pop() != '(')
                        return false;
                    break;
                case '}':
                    if (stack.size() == 0 || stack.pop() != '{')
                        return false;
                    break;
                case ']':
                    if (stack.size() == 0 || stack.pop() != '[')
                        return false;
                    break;
            }
        }
        return stack.isEmpty();
    }

### 再次减少代码量


    public class Solution {
        public boolean isValid(String s) {
            if(s==null||s.length()%2==1)
                return false;
            Stack<Character> stack = new Stack<>();
            for(int i=0;i<s.length();i++){
                char c = s.charAt(i);
                if(c=='['||c=='{'||c=='(')
                    stack.push(c);
                else{
                    if(stack.isEmpty())
                        return false;
                    else if(c==']' && stack.pop()!='[')
                        return false;
                    else if(c==')' && stack.pop()!='(')
                        return false;
                    else if(c=='}' && stack.pop()!='{')
                        return false;
                }
            }
            return stack.isEmpty();
        }
    }
