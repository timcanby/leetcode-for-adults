<p align="center">🌐 Language: &nbsp;<a href="README.md"><b>English</b></a> &nbsp;·&nbsp; <a href="README.zh.md">中文</a> &nbsp;·&nbsp; <a href="README.ja.md">日本語</a></p>

<p align="center"><a href="../README.md#-the-catalog">← Back to Catalog</a></p>

---

### 30. Bucket Sort

> *Distribute elements into buckets by range, sort each bucket, then concatenate.*

**🧩 Algorithm**
Bucket sort doesn't sort the array — it **scatters** it into buckets, sorts each bucket individually, then **gathers** them back. The magic is in the scatter: elements are routed to buckets by their value range, so each bucket only holds a small, similar slice. The sorting inside each bucket is trivial — a few similar elements, easy to sort by any method. The hard part of sorting — comparing dissimilar elements across a vast range — is *eliminated by the scatter*.

```python
def bucket_sort(nums, bucket_size=5):
    if len(nums) < 2:
        return nums

    lo, hi = min(nums), max(nums)
    bucket_count = (hi - lo) // bucket_size + 1
    buckets = [[] for _ in range(bucket_count)]

    for x in nums:
        buckets[(x - lo) // bucket_size].append(x)

    ans = []
    for bucket in buckets:
        bucket.sort()
        ans.extend(bucket)

    return ans
```

> Time $O(n + k \cdot \frac{n}{k} \log \frac{n}{k})$ — $O(n)$ when evenly distributed · Space $O(n)$

The deeper principle: **you don't sort the whole — you sort the parts, and the scatter makes the parts sortable.**

The scatter is the algorithm's soul. Before any sorting happens, the array is already *partially ordered*: every element in bucket $i$ is smaller than every element in bucket $i+1$. That's not a result of sorting — it's a result of *routing*. The scatter imposes a coarse order using only the value (one arithmetic operation: which bucket does this belong to?), and the sort only needs to handle the *fine* order within each bucket. The hard problem — global sorting — is decomposed into many easy problems — local sorting — by the act of scattering.

And the beauty: **when the distribution is even, bucket sort is $O(n)$.** Each bucket holds $\approx n/k$ elements, and sorting each is fast because the range within each bucket is small. The total work is $n$ scatter + $k$ sorts of $\approx n/k$ each — which simplifies to $O(n)$ when the data is evenly spread. The evenness of the distribution *is* the performance guarantee. Chaotic data that clumps into one bucket degrades to $O(n \log n)$ — you're back to sorting one big bucket. The algorithm's efficiency is not in the code; it's in the *shape* of the data.

And the trade-off — the bucket size: **too few buckets and you're sorting one big array; too many buckets and you're paying overhead for empty containers.** The bucket size is the parameter that determines everything. Large buckets: less routing overhead but more sorting per bucket. Small buckets: more routing overhead but trivial sorting. The optimal is when the data is evenly distributed across the right number of buckets — and *that* depends on knowing your data. Bucket sort is the algorithm that rewards you for *understanding the distribution*. If you know the data is uniform, you can nail it. If you're blind to the distribution, you're guessing — and a bad guess means one overloaded bucket and $n - 1$ empty ones.

**🏢 Workplace**
You don't solve a company-wide problem by attacking it globally. You **scatter** — route each issue, each task, each decision to the team that owns its range — then let each team sort their own slice.

The scatter is the org design. Before any work happens, the issues are already *partially ordered*: every issue in team $i$'s domain is closer to team $i$ than to team $i+1$. That's not a result of collaboration — it's a result of *routing*. The org chart imposes a coarse order (which team owns which range?), and the teams only need to handle the *fine* order within their domain. The hard problem — global prioritization across all teams — is decomposed into many easy problems — local prioritization within each team — by the act of scattering.

And the beauty: **when the workload is evenly distributed, the org runs in $O(n)$.** Each team holds $\approx n/k$ issues, and sorting within each team is fast because the range is narrow. The total work is $n$ routing + $k$ teams each sorting their slice. When the distribution is even — no team is overloaded, no team is idle — the whole org moves at the speed of the slowest team, which is fast. When the distribution is chaotic — one team holds 90% of the issues, the other $k-1$ teams are empty — the org degrades to the overloaded team's $O(n \log n)$ sort. The bottleneck isn't the algorithm; it's the *clump*.

And the trade-off — the team size: **too few teams and each is sorting one big backlog; too many teams and you're paying coordination overhead for empty teams.** The bucket size — the team scope — determines everything. Large teams: less routing overhead (fewer hand-offs) but more internal sorting. Small teams: more routing overhead (more hand-offs) but trivial internal sorting. The optimal is when the workload is evenly distributed across the right number of teams — and *that* depends on knowing your org's problem distribution. Bucket sort rewards you for *understanding the distribution of your work*. If you know the issues cluster in one domain, you allocate more teams there. If you're blind, you create equal-sized teams and one of them drowns.

**🌍 Life**
You don't solve your whole life by attacking it globally. You **scatter** — route each commitment, each project, each relationship to the "bucket" it belongs to — then sort within each bucket.

The scatter is the life design. Before any sorting happens, your life is already *partially ordered*: every commitment in the "health" bucket is closer to "health" than to anything in the "career" bucket. That's not a result of prioritizing — it's a result of *routing*. You impose a coarse order (which life domain does this belong to?), then sort *within* each domain. The hard problem — "what's the single most important thing in my life?" — is decomposed into many easier problems — "what matters most in my health / career / relationships / finances?" — by the act of scattering.

And the beauty: **when your life is evenly distributed, it runs in $O(n)$.** Each domain holds a manageable number of commitments. Sorting within each domain is fast because the range is narrow. The total effort is $n$ routing + sorting within each bucket. When no domain is overloaded and none is empty — when your energy, time, and attention are spread across domains roughly evenly — life feels $O(n)$. Smooth, linear, manageable. When one domain clumps — work takes 90% and health, relationships, and finances are empty — life degrades to $O(n \log n)$ in the overloaded bucket. You're spending all your effort sorting one giant work bucket while the others gather dust. The bottleneck isn't your effort; it's the *clump*.

And the trade-off — the bucket size: **too few life domains and each is an overloaded backlog; too many and you're paying overhead maintaining empty categories.** The bucket size — how granular your life domains are — determines everything. Coarse buckets ("work" vs. "life"): less overhead but each bucket is heavy. Fine buckets ("morning routine" vs. "exercise" vs. "meal prep"): more overhead but each is trivially manageable. The optimal is when your life's commitments are evenly distributed across the right number of domains — and *that* depends on knowing *your* distribution. Bucket sort rewards you for *understanding the shape of your life*. If you know work clumps, you allocate more buckets there. If you're blind, you create equal buckets and one of them drowns you.

And the wisdom: **the scatter comes before the sort.** Before you prioritize, before you optimize, before you try to "sort your life out" — scatter. Route each thing to its bucket. *Then* sort within each. The act of scattering is the act of *understanding* — it requires knowing the range, knowing the distribution, knowing which things belong together. Skip the scatter and you're sorting one giant undifferentiated pile, paying $O(n \log n)$ for what should cost $O(n)$. Scatter first. Sort second. The scatter is not a warm-up; it's the algorithm.

**⚠️ Anti-pattern**
*"I'll just sort everything by priority in one big list."*
That's comparison sort on the whole array — one giant bucket, $O(n \log n)$, and the range is the full span of your life. You're comparing a dentist appointment against a career decision against a text to a friend, all in the same list, all weighted the same way. The scatter is what *prevents* this absurdity: route each to its bucket first (health, career, relationships), then sort within each. The dentist appointment is only compared against other health tasks — not against your five-year plan. The career decision is only compared against other career moves — not against whether to text back today. The scatter eliminates the cross-domain comparisons that make a single priority list insane. Without it, you're comparing apples and cities and dentist appointments in one $O(n \log n)$ pile, and the "priority" you compute is meaningless because the domains aren't comparable. Scatter first. Then sort. The decomposition *is* the solution.
