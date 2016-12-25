### Spiral Matrix II

Given an integer n, generate a square matrix filled with elements from 1 to n2 in spiral order.

* 给定整数n, 生成以螺旋顺序填充从1到n*2 的方形矩阵

```
Given n = 3,

[
 [ 1, 2, 3 ],
 [ 8, 9, 4 ],
 [ 7, 6, 5 ]
]
```

``` java
public class Solution {
    public int[][] generateMatrix(int n) {
        int[][] matrix = new int[n][n];
        if(n==0) return matrix;
        int rowBegin=0,rowEnd=n-1, colBegin=0,colEnd=n-1,num=1;
        
        while(rowBegin<=rowEnd && colBegin<=colEnd){
            for(int i=colBegin;i<=colEnd;i++){
                matrix[rowBegin][i]=num++;
            }
            rowBegin++;
            for(int i=rowBegin;i<=rowEnd;i++){
                matrix[i][colEnd]=num++;
            }
            colEnd--;
            for(int i=colEnd;i>=colBegin;i--){
                if(rowBegin<=rowEnd){ //因为是方形矩阵，可以不加判断，但是这样也适用于n*m矩阵
                    matrix[rowEnd][i]=num++;
                }
            }
            rowEnd--;
            for(int i=rowEnd;i>=rowBegin;i--){
                if(colBegin<=colEnd){
                    matrix[i][colBegin]=num++;
                }
            }
            colBegin++;
    }
    return matrix;
    }
}
```

[Python的奇妙解法](https://discuss.leetcode.com/topic/19130/4-9-lines-python-solutions/2)