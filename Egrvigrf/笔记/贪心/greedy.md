# 反悔贪心
[Money Buys Less Happiness Now](https://codeforces.com/contest/1974/problem/G)

幸福永远买不够，所以我们又来了！在这个版本中，你每个月只能买到 $h_i = 1$ 个单位的幸福，但月数却大大增加了。我们进入了量子幸福和时间膨胀的领域。

作为一名物理学家，查理喜欢用简单精确的语言来规划自己的生活。

在接下来的 $m$ 个月里，从没有钱开始，查理将努力工作，每月赚取 $x$ 英镑。在 $i$ 个月的 $(1 \le i \le m)$ 里，将有一次机会，付出 $c_i$ 英镑的代价，获得一个单位的幸福。每月不能购买超过一个单位。

不允许借贷。在 $i$ 月赚到的钱只能在之后的 $j$ 月使用。

既然物理学家不会编码，那就帮查理找出可达到的最大幸福单位吧。

用优先队列实现反悔贪心
能买就买，钱不够了就反悔使用更优买法。
```c++
if (left - a[i] >= 0) {
    left -= a[i];
    q.push(a[i]);
    ans++;
} else if (!q.empty() && a[i] < q.top()) {
    left += q.top();
    q.pop();
    left -= a[i];
    q.push(a[i]);
}
```