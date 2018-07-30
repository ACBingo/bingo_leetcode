[28. 实现strStr](https://leetcode-cn.com/problems/implement-strstr/description/)

字符串匹配水题，边界条件需要考虑清楚。
差点想上kmp

```
class Solution {
    public int strStr(String haystack, String needle) {
        int ans = -1;
        int p = 0;

        if (haystack.length() == 0 && needle.length() == 0) {
            return 0;
        }
        if (haystack.length() == 0) {
            return -1;
        }
        if (needle.length() == 0) {
            return 0;
        }
        if (haystack.equals(needle)) {
            return 0;
        }

        for (int i = 0; i < haystack.length(); i++) {
            if (haystack.charAt(i) != needle.charAt(0)) {
                continue;
            }
            while (p < needle.length() && (i + p) < haystack.length() && needle.charAt(p) == haystack.charAt(i + p)) {
                p++;
            }
            if (p >= needle.length()) {
                return i;
            }
            p=0;
        }

        return ans;
    }
}
```