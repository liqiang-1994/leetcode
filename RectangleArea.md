### Rectangle Area
Find the total area covered by two rectilinear rectangles in a 2D plane.
Each rectangle is defined by its bottom left corner and top right corner as shown in the figure.Assume that the total area is never beyond the maximum possible value of int.

* 找到2D平面中的两个矩形覆盖的总面积，假设总面积从不超过int的最大可能值

[图](http://ocx6qfmnn.bkt.clouddn.com/rectangle.png)
``` java
public class Solution {
     public int computeArea(int A, int B, int C, int D, int E, int F, int G, int H) {
         int area = (C-A) * (D-B) + (G-E)*(H-F);
         if(B>=H || F>=D || A>=G || E>=C) return area;
         return area - (Math.min(C, G) - Math.max(A, E)) * (Math.min(D, H) - Math.max(B,F));
     }
}
```
``` python
class Solution(object):
    def computeArea(self, A, B, C, D, E, F, G, H):
      """
        :type A: int
        :type B: int
        :type C: int
        :type D: int
        :type E: int
        :type F: int
        :type G: int
        :type H: int
        :rtype: int
        """
        return (C-A) * (D-B) +(G-E) * (H-F) -max(0, min(C,G) - max(A, E)) * max(0, min(D, H) - max(B ,F))
        
        
        
        
        
        
        
        
        
        
        
        
        
        
        
        
        
        
        
        
        
        
        
```