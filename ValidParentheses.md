### Valid Partentheses

Given a string containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.

The brackets must close in the correct order, "()" and "()[]{}" are all valid but "(]" and "([)]" are not.

* 判断一个字符串里的括号能否正常关闭

``` java
public class Solution {
    public boolean isValid(String s) {
        Stack<Character> stack = new Stack<>();
        for(int i=0;i<s.length();i++){
            char temp = s.charAt(i);
            if(temp=='(' || temp =='[' || temp =='{'){
                stack.push(temp);
            }else if(temp==')' && !stack.empty() && stack.peek()=='('){
                stack.pop();
            }else if(temp==']' && !stack.empty() && stack.peek()=='['){
                stack.pop();
            }else if(temp=='}' && !stack.empty() && stack.peek()=='{'){
                stack.pop();
            }else{
                return false;
            }
        }
        return stack.empty();
    }
}              
``` 
``` python
class Solution(object):
    def isValid(self, s):
        """
        :type s: str
        :rtype: bool
        """
        stack=[]
        level = {')':'(', ']':'[','}':'{'}
        
        for char in s:
            if char in level.values():
                stack.append(char)
            elif char in level.keys():
                if stack==[] or stack.pop()!=level[char]:
                    return False
            else:
                return False
        return stack==[]
                    
```