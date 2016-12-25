### Combintaions

Given two integers n and k, return all possible combinations of k numbers out of 1 ... n.

* 给定两个正整数n和k，返回1...n中所有k个数的可能组合

```
If n = 4 and k = 2, a solution is:

[
  [2,4],
  [3,4],
  [2,3],
  [1,2],
  [1,3],
  [1,4],
]
```
``` java
public class Solution {
    public List<List<Integer>> combine(int n, int k) {
        if (k == n || k == 0) {
            List<Integer> row = new LinkedList<>();
            for (int i = 1; i <= k; ++i) {
                row.add(i);
            }
            return new LinkedList<>(Arrays.asList(row));
        }
        List<List<Integer>> result = this.combine(n - 1, k - 1);
        result.forEach(e -> e.add(n));
        result.addAll(this.combine(n - 1, k));
        return result;
    }
}
```
``` java
public class Solution {
    public List<List<Integer>> combine(int n, int k) {
        if(k==0 || k >n) return new LinkedList<>();
        List<List<Integer>> ret = combine(n-1,k-1);
        if(ret.size()==0) ret.add(new LinkedList<>(Arrays.asList(n)));
        else ret.forEach(e->e.add(n));
        ret.addAll(combine(n-1,k));
        return ret;
    }
}
```