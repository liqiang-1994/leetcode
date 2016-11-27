###  Pascal's Triangle

Given numRows, generate the first numRows of Pascal's triangle

* 给定numRows，生成一个杨辉三角形

```
Given numRows =5, return 
[
     [1],
    [1,1],
   [1,2,1],
  [1,3,3,1],
 [1,4,6,4,1]
]
```
``` java
public class Solution {
    public List<List<integer>> generate(int numRows) {
        List<List<Integer>> lists = new ArrayList<>();
        List<Integer> row = new ArrayList<>();
        for(int i=0;i<numRows;i++){
            row.add(0, 1); //每增加一行，在数组头加上一个1
            for(int j=1;j<i;j++){
                row.set(j, row.get(j)+row.get(j+1));
            }
            lists.add(new ArrayList<>(row));
          }
          return lists
      }
}
```
``` python
class Solution(object):
    def generate(self, numRows):
        """
        :type numRows: int
        :rtype: List[List[int]]
        """
        n, nex, res = 0, [1], []
        while n <numRows:
            res.append(nex)
            nex = [1] +[[nex[i] +nex[i+1] for i in xrange(len(res)-1)] +[1]
            n+=1
        return res
```