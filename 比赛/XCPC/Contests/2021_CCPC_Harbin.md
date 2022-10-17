# [A.So Many Lucky Strings](https://codeforces.com/gym/103447/problem/A)

DP + KMP + Manacher

（挖坑）



# [B.Magical Subsequence](https://codeforces.com/gym/103447/problem/B)

DP

记 $A_{b_1} + A_{b_2} = A_{b_3} + A_{b_4} = ... = A_{b_{m - 1}} + A_{b_m} = s$ ，可以发现 $s <= 200$。

枚举 $s$ 的值， $dp[i]$ 表示两两和为 $s$ 的情况下，前 $i$ 个数的最长Magical序列长度。

$dp[i] = max(dp[i - 1], maxx[s - a[i]] + 2)$ ，其中 $maxx[x]$ 表示在 $i$ 之前值为 $x$ 的位置的最长Magical序列长度（该位置未被使用）。

时间复杂度： $O(200n)$

<details><summary>CODE</summary>
<p>
    
```
inline void solve() {
    read(n);
    for(int i = 1; i <= n; i++) read(a[i]);
    for(int s = 2; s <= 200; s++) {
        for(int i = 0; i <= 200; i++) maxx[i] = -inf;
        for(int i = 1; i <= n; i++) dp[i] = 0;
        maxx[a[1]] = 0;
        for(int i = 2; i <= n; i++) {
            dp[i] = dp[i - 1];
            if(a[i] >= s) continue;
            dp[i] = max(dp[i], maxx[s - a[i]] + 2);
            maxx[a[i]] = max(maxx[a[i]], dp[i - 1]);
        }
        ans = max(ans, dp[n]);
    }
    writeln(ans);
}
```

</p>
</details>



# [C.Colorful Tree](https://codeforces.com/gym/103447/problem/C)

dp 启发式合并 dsu on tree

（挖坑）



# [D.Math master](https://codeforces.com/gym/103447/problem/D)

数字最多 $\omega = 19$ 位，$2^{ \omega}$暴力枚举所有的数字组合，然后检验即可。

时间复杂度：$O(T \omega w^{ \omega})$



