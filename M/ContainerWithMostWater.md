### Container With Most Water

Given n non-negative integers a1, a2, ..., an, where each represents a point at coordinate (i, ai). n vertical lines are drawn such that the two endpoints of line i is at (i, ai) and (i, 0). Find two lines, which together with x-axis forms a container, such that the container contains the most water.

Note: You may not slant the container.

* 在二维坐标中，（i , ai)表示从(i, 0)到（i, ai)的一条线段，任意的两条这样的线段和x轴围城的容器，找出能够盛水的最大容积,不能倾斜容器

``` java
public class Solution {
    public int maxArea(int[] height) {
        if(height.length<2) return 0;
        int max = 0;
        int l=0;
        int r = height.length - 1;
        while(l<r){
            int v = (r-l)*Math.min(height[l], height[r]);
            if(v>max) max =v;
            if(height[l]<height[r]) l++;
            else r--;
        }
        return max;
     }
}
```