# [A.So Many Lucky Strings](https://codeforces.com/gym/103447/problem/A)

DP + KMP + Manacher

（挖坑）

# [B.Magical Subsequence](https://codeforces.com/gym/103447/problem/B)

DP

、、、
    inline void solve() {
    //    into();
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
、、、
