### Gray Code

The gray code is a binary numeral system where two successive values differ in only one bit.Given a non-negative integer n representing the total number of bits in the code, print the sequence of gray code. A gray code sequence must begin with 0.

* 格雷码是二进制数字系统，其中两个连续值仅在一个位不同
``` 
For example, given n = 2, return [0,1,3,2]. Its gray code sequence is:

00 - 0
01 - 1
11 - 3
10 - 2
```

For a given n, a gray code sequence is not uniquely defined.

For example, [0,2,3,1] is also a valid gray code sequence according to the above definition.

For now, the judge is able to judge based on one instance of gray code sequence. Sorry about that.

* G：格雷码 B：二进制码 G(N) = (B(n)/2) XOR B(n)
[Wikipedia](https://zh.wikipedia.org/wiki/格雷码)
``` java
public class Solution {
    public List<Integer> grayCode(int n) {
        List<Integer> ret = new LinkedList<>();
        for(int i=0;i<1<<n;i++) ret.add(i^(i>>1));
        return ret;
       }
 }
```

``` java
public class Solution {
    public List<Integer> grayCode(int n) {
        ArrayList<Integer> ret = new ArrayList<>();
        ret.add(0);
        for(int i=0;i<n;i++){
            int temp=1<<i;
            for(int j=ret.size()-1;j>=0;j--) ret.add(ret.get(j)+temp);
        }
        return ret;
    }
}
```