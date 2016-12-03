### Assign Cookies

Assume you are an awesome parent and want to give your children some cookies. But, you should give each child at most one cookie. Each child i has a greed factor gi, which is the minimum size of a cookie that the child will be content with; and each cookie j has a size sj. If sj >= gi, we can assign the cookie j to the child i, and the child i will be content. Your goal is to maximize the number of your content children and output the maximum number.

* 假设你是一个真棒的父母，并想给你的孩子一些饼干。 但是，你应该给每个孩子最多一个cookie。 每个孩子i都有一个贪心因子gi，这是孩子将要拥有的cookie的最小大小; 并且每个cookie j具有大小sj。 如果sj> = gi，我们可以将cookie j分配给子i，子i将是内容。 您的目标是最大化您的内容孩子的数量，并输出最大数量。

```
Input: [1,2,3], [1,1]

Output: 1

Explanation: You have 3 children and 2 cookies. The greed factors of 3 children are 1, 2, 3. 
And even though you have 2 cookies, since their size is both 1, you could only make the child whose greed factor is 1 content.
You need to output 1.
```
```
Input: [1,2], [1,2,3]

Output: 2

Explanation: You have 2 children and 3 cookies. The greed factors of 2 children are 1, 2. 
You have 3 cookies and their sizes are big enough to gratify all of the children, 
You need to output 2.
```
* 将两个数组排序，如果当前饼干小于等于满足感，先满足期望值低的孩子，然后指针前移
``` java
public class Solution {
     public int findContentChildren(int[] g, int[] s) {
         Arrays.sort(g);
         Arrays.sort(s);
         int i=0;
         for(int j=0;i<g.length && j<s.length;j++){
             if(g[i]<=s[j]) i++;
         }
         return i;
     }
}
```
``` python
class Solution(object):
    def findContentChildren(self, g, s):
        """
        :type g: List[int]
        :type s: List[int]
        :rtype: int
        """
        g.sort()
        s.sort()
        i, j = 0, 0
        for n in s:
            if j==len(g):
                break
            if n>=g[i]:
                i+=1
                j+=1
        return i
                
```