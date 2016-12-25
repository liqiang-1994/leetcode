### Spiral Matrix

Given a matrix of m x n elements (m rows, n columns), return all elements of the matrix in spiral order.

* 给定一个m x n个矩阵，以螺旋顺序返回所有元素

```
[
 [ 1, 2, 3 ],
 [ 4, 5, 6 ],
 [ 7, 8, 9 ]
]
You should return [1,2,3,6,9,8,7,4,5].
```

``` java
public class Solution {
    public List<Integer> spiralOrder(int[][] matrix) {
        List<Integer> list = new ArrayList<>();
        if(matrix.length==0) return list;
        
        int rowBegin = 0;
        int rowEnd = matrix.length-1;
        int colBegin = 0;
        int colEnd = matrix[0].length-1;
        while(rowBegin<=rowEnd && colBegin<=colEnd){
            for(int i=colBegin;i<=colEnd;i++){  //往右走
                list.add(matrix[rowBegin][i]);
            }
            rowBegin++;
            for(int i=rowBegin;i<=rowEnd;i++){  //往下走
                list.add(matrix[i][colEnd]);
            }
            colEnd--;
            if(rowBegin<=rowEnd){ //没有行的判断
                for(int i=colEnd;i>=colBegin;i--){ //往左走
                    list.add(matrix[rowEnd][i]);
                }
            }
            rowEnd--;
            if(colBegin<=colEnd){  //没有列的判断
                for(int i=rowEnd;i>=rowBegin;i--){  //往上走
                    list.add(matrix[i][colBegin]);
                }
            }
            colBegin++;
        }
        return list;
    }
}
```

``` python
class Solution(object):
    def spiralOrder(self, matrix):
        """
        :type matrix: List[List[int]]
        :rtype: List[int]
        """
        ret = []
        while matrix:
            ret +=matrix.pop(0)
            if matrix and matrix[0]:
                for row in matrix:
                    ret.append(row.pop())
            if matrix:
                ret +=matrix.pop()[::-1]
            if matrix and matrix[0]:
                for row in matrix[::-1]:
                    ret.append(row.pop(0))
        return ret
```