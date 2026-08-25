<p align="center">🌐 Language: &nbsp;<a href="README.md"><b>English</b></a> &nbsp;·&nbsp; <a href="README.zh.md">中文</a> &nbsp;·&nbsp; <a href="README.ja.md">日本語</a></p>

<p align="center"><a href="../README.md#-the-catalog">← Back to Catalog</a></p>

---

### 29. Counting Sort

> *Count how many times each value appears, then reconstruct the array in order.*

**🧩 Algorithm**
Counting sort doesn't compare. It doesn't swap, partition, merge, pivot, or heapify. It **counts** — tallies the frequency of each value, then walks the tally from smallest to largest, writing each value the recorded number of times. The result is sorted. No comparison ever happened.

The entire algorithm is two passes: first, count each value's frequency into a `count` array indexed by `value - min`. Second, walk the `count` array and overwrite the original array in order. That's it. The order isn't *discovered* by comparing elements — it's *inherent* in the structure of the count array, which is indexed by value.

```python
def counting_sort(nums):
    if not nums:
        return nums

    lo = min(nums)
    hi = max(nums)
    count = [0] * (hi - lo + 1)

    for x in nums:
        count[x - lo] += 1

    idx = 0
    for offset, freq in enumerate(count):
        value = offset + lo
        for _ in range(freq):
            nums[idx] = value
            idx += 1

    return nums
```

> Time $O(n + k)$ where $k$ = range of values · Space $O(k)$

The deeper principle: **when the structure is already there, you don't need to discover it — you just need to count it.**

Comparison-based sorts — bubble, selection, insertion, merge, quick, heap — all assume ignorance. They don't know what the values are, so they compare pairs to *discover* the order. Counting sort assumes knowledge: the values come from a *known range*, so the order is already encoded in the values themselves. You don't need to compare `3` against `7` to know which is smaller. You just count: "how many 3s? how many 7s?" — and write them in order.

The trade-off is the range. Counting sort is $O(n + k)$ where $k$ is the spread between min and max. If the values are ages ($k \approx 100$) or test scores ($k \approx 100$), it's blazing fast — $O(n)$, linear, unbeatable. If the values are 64-bit integers ($k = 2^{64}$), it's unusable — the count array alone would exceed all memory. Counting sort is fast when the value range is small and slow when it's vast. The algorithm doesn't degrade gracefully — it either works spectacularly or doesn't work at all.

And the wisdom: **you don't need to compare what you can count.** The comparison-based approach — weighing every element against every other — is the *general* solution for when you know nothing about the data. But when you *do* know something — when the values come from a bounded range, when the categories are finite, when the structure is visible — the general solution is wasteful. You're paying $O(n \log n)$ comparisons for an answer that's already encoded in the frequency of the values. Count the frequencies. Walk the range. You're done in $O(n)$. The knowledge of the range *is* the algorithm.

**🏢 Workplace**
Most organizational problems are treated as comparison problems: "is person A better than person B? Is project X more important than project Y?" — endless pairwise comparisons, performance reviews, priority matrices. That's the $O(n \log n)$ approach: compare everyone against everyone, discover the ranking.

But sometimes you don't need to compare. Sometimes the structure is already visible. "How many people are at each level? How many projects are in each category? How many tasks are in each priority bucket?" — if the values come from a known, bounded range (3 seniority levels, 5 priority tiers, 4 project types), counting is enough.

The counting sort approach to org management: **stop comparing individuals when you can count categories.** Instead of ranking 50 engineers against each other ($O(n \log n)$ comparisons, expensive and political), count: "how many are senior? How many are mid-level? How many are junior?" Walk the count array: fill the senior slots first, then mid-level, then junior. No one was compared. The structure of the levels *produced* the order.

And the trade-off — the range: **counting sort only works when the range is bounded and known.** If the org has 3 levels, counting is instant. If the org tries to rank every engineer on a unique 50-point scale, counting is useless — $k = 50$ in a population of 50, so you're back to comparison. The insight: **don't create fine-grained distinctions when coarse categories suffice.** If 5 priority tiers are enough, use 5. Don't invent a 50-point scoring rubric that forces you back into $O(n \log n)$ comparison territory. The bounded range is the gift. Unbounded comparison is the tax. Preserve the range; resist the urge to differentiate beyond it.

**🌍 Life**
Most life decisions are treated as comparison problems: "is option A better than option B? Is city X better than city Y? Is career path P better than career path Q?" — endless weighing, ranking, optimization. That's the $O(n \log n)$ life: every option compared against every other, the "best" choice always just out of reach because there's one more comparison to make.

But sometimes you don't need to compare. Sometimes the categories are already visible. "How many cities are in my price range? How many careers match my top 3 skills? How many relationships are at the depth I need?" — if the values come from a bounded range (affordable cities, matching careers, compatible people), counting is enough.

The counting sort approach to life: **stop comparing every option when you can count the categories that matter.** You don't need to rank 100 cities against each other. You need to count: "how many are affordable? How many have my industry? How many feel like home?" Walk the count array: the cities that match all three categories are your range. No comparison needed. The structure of the categories *produced* the answer.

And the wisdom — the one that frees you from decision paralysis: **you don't need to find the best. You need to count what fits.** The comparison approach demands: "which is *the best* city, *the best* career, *the best* partner?" — an $O(n^2)$ or $O(n \log n)$ question with no guaranteed answer, because "best" is a moving target. The counting approach asks: "how many are good enough? How many fit my categories?" — an $O(n)$ question with a concrete answer. Count the frequencies. Walk the range. The answer isn't "the one best option" — it's "the set of options that fit." And when you realize the set isn't empty — that there are 7 cities you could live in, 12 careers you could pursue, 5 people you could build a life with — the comparison anxiety dissolves. You weren't looking for *the best*. You were looking for *enough good ones*. Counting tells you the count. And the count is the answer.

**⚠️ Anti-pattern**
*"I need to compare every option to find the absolute best."*
That's comparison sort applied to a counting sort problem — paying $O(n \log n)$ comparisons for an answer that's already encoded in the categories. If the options come from a bounded range — affordable cities, matching careers, compatible people — the "best" is a phantom. There's no single best. There's a *range of good-enough options*, and counting gives you the range in $O(n)$. The obsession with "the best" is what makes decisions $O(n^2)$: every option compared against every other, no option ever sufficient because there might be a marginally better one. Count the options that fit. Walk the range. Pick one from the set. The counting sort wisdom is: **the range is the answer.** Not the maximum — the set of values that fit within the bounds. When you stop looking for the best and start counting what fits, decisions go from $O(n^2)$ to $O(n)$. The categories you chose — the bounds you set — *are* the algorithm. Choose good bounds, count what's inside, and the "best" takes care of itself.
