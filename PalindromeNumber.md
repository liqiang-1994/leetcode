### Palindrome Number

Determine whether an integer is a palindrome. Do this without extra space.

* 确定是否是回文数

``` java
public class Solution {
    public boolean isPalindrome(int x) {
        if(x<0 || (x!=0 && x%10==0)) return false;
        int ret =0 ;
        while(x>ret){
            ret = ret *10 +x%10;
            x/=10;
        }
        return (x==ret || x==ret/10);
    }
}
```

``` python
class Solution(object):
    def isPalindrome(self, x):
        """
        :type x: int
        :rtype: bool
        """
        ret = 0
        temp=x
        while x>0:
            ret=ret*10 +x%10
            x/=10
        return temp==ret
        
```