### Plus One 

Given a non-negative number represented as an array of digits, plus one to the number.

The digits are stored such that the most significant digit is at the head of the list.

* 给定一个非负的数字各位表示的数组，加上1后，返回一个新的数形成的数组

``` java
public class Solution {
    public int[] plusOne(int[] digits) {
        for(int i=digits.length-1;i>=0;i--) {
            if(digits[i] < 9) {
                digits[i]++;
                return digits; //加1后没有进位直接返回
            }
            digits[i]=0; //进位设0
         }
         int[] ret = new int[digits.length+1]; //超出范围如9，99，999 ，return 10, 100, 1000...
         ret[0]=1;
         return ret;
     }
}  
```
* 利用Python便捷的函数，将List[int] 转化成int型加1后再返回List[int]
``` python
class Solution(object):
    def plusOne(self, digits):
        """
        :type digits: List[int]
        :rtype: List[int]
        """
        nums = 0
        for i in range(len(digits)):
            nums+=digits[i] * pow(10, len(digits)-i-1)
        return [int(n) for n in str(nums+1)]
```