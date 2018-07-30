[50. Pow(x, n)](https://leetcode-cn.com/problems/powx-n/description/)

ACM时快速幂都快用烂了。。。此题思路类似

假如 n = 13，13在二进制中表示为：00001101，那么13 = 2^3 + 2^2 + 2^0
![](https://images2018.cnblogs.com/blog/653667/201807/653667-20180722172132867-839514732.png)

```
class Solution {
    public double myPow(double x, int n) {
        int m = n < 0 ? -n - 1 : n;  //如果是n负数，要避免溢出
        double p = 1;
        for(double q = x; m > 0; m /= 2) {  
            if((m & 1) != 0) p *= q;  //一旦该位为1，那么将q乘入p中
            q *= q;  //m每次除2，q就要变为平方
        }
        return n < 0 ? 1 / p / x : p;
    }
}
```


参考:[参考](https://blog.csdn.net/happyaaaaaaaaaaa/article/details/51655964)