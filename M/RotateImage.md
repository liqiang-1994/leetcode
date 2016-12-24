### Rotate Image

You are given an n x n 2D matrix representing an image.

Rotate the image by 90 degrees (clockwise).

* 将一个n x n的2维矩阵表示的图象顺时针旋转90度

```
1  2  3              1  4  7            7  4  1
4  5  6        =>    2  5  8     =>     8  5  2 
7  8  9              3  6  9            9  6  3
```
``` java
public class Solution {
    public void rotate(int[][] matrix) {
        for(int i=0;i<matrix.length;i++){
            for(int j=i;j<matrix[0].length;j++){
                int temp = matrix[i][j];
                matrix[i][j]=matrix[j][i];
                matrix[j][i]=temp;
            }
        }
        for(int i=0;i<matrix.length;i++){
            for(int j=0;j<matrix[0].length/2;j++){
                int temp=matrix[i][j];
                matrix[i][j]=matrix[i][matrix.length-j-1];
                matrix[i][matrix.length-j-1]=temp;
            }
        }
    }
}
                
```
```
  1 2 3            7 8 9           7 4 1
  4 5 6  =>        4 5 6  =>       8 5 2
  7 8 9            1 2 3           9 6 3
```

```python 
class Solution(object):
    def rotate(self, matrix):
        """
        :type matrix: List[List[int]]
        :rtype: void Do not return anything, modify matrix in-place instead.
        """
        matrix.reverse()
        for i in range(len(matrix)):
            for j in range(i):
                matrix[i][j], matrix[j][i] = matrix[j][i], matrix[i][j]
```