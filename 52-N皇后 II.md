[52. N皇后 II](https://leetcode-cn.com/problems/n-queens-ii/description/)

跟上个题一模一样，现在只需输出个数即可

```
class Solution {
    public int totalNQueens(int n) {
        boolean[] row = new boolean[n];
        boolean[] h = new boolean[2 * n];
        boolean[] r = new boolean[2 * n];

        List<List<String>> ans = new ArrayList<>();
        dfs(n, row, h, r, new ArrayList<>(), 0, ans);
        return ans.size();
    }

    public void dfs(int n, boolean[] row, boolean[] h, boolean[] r, List<Integer> curList, int curK, List<List<String>> ans) {
        if (curK == n) {
            List<String> tmp = new ArrayList<>();
            for (Integer integer : curList) {
                String st = "";
                for (int i = 0; i < n; i++) {
                    if (i == integer) {
                        st += "Q";
                    } else {
                        st += ".";
                    }
                }
                tmp.add(st);
            }
            ans.add(tmp);
        }

        for (Integer i = 0; i < n; i++) {
            if (!row[i] && !h[curK + i] && !r[curK - i + n]) {
                row[i] = true;
                h[curK + i] = true;
                r[curK - i + n] = true;
                curList.add(i);
                dfs(n, row, h, r, curList, curK + 1, ans);
                curList.remove(i);
                row[i] = false;
                h[curK + i] = false;
                r[curK - i + n] = false;
            }
        }
    }
}
```