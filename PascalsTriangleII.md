### Pascal's Triangle II

Given an index k, return the kth row of the Pascal's triangle.

For example, given k = 3,
Return [1,3,3,1].

* 给定指定行数的杨辉三角形的第k行

``` java
public class Solution {
    public List<Integer> getRow(int rowIndex) {
        List<Integer> lists = new ArrayList<>();
        if(rowIndex < 0) return lists;
        for(int i=0;i<rowIndex+1;i++) {
            lists.add(0,1);
            for(int j=1;j<i;j++) {
                lists.set(j, lists.get(j) +lists.get(j+1));
             }
        }
        return lists;
    }
}
```
``` python
class Solution(object):
    def getRow(self, rowIndex):
        """
        :type rowIndex: int 
        :rtype: List[int]
        """
        n, ret = 0, [1]
        while n < rowIndex:
             ret = [1] + [ret[i] +ret[i+1] for i in xrange(n)] + [1]
             n+=1
        return ret
```