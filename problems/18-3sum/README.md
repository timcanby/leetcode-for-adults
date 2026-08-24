<p align="center">🌐 Language: &nbsp;<a href="README.md"><b>English</b></a> &nbsp;·&nbsp; <a href="README.zh.md">中文</a> &nbsp;·&nbsp; <a href="README.ja.md">日本語</a></p>

<p align="center"><a href="../README.md#-the-catalog">← Back to Catalog</a></p>

---

### 18. 3Sum

> *Find all unique triplets that sum to zero. No duplicates in the output.*

**🧩 Algorithm**
Three numbers, one constraint. The naive approach is three nested loops — $O(n^3)$, every combination checked, duplicates dehashed with a set. Brute force doesn't use the structure; it just churns.

The key move: **reduce dimensions.** Don't think about three numbers at once. Fix one, and the remaining problem is Two Sum on a sorted range — something you already know how to solve in $O(n)$ with two pointers.

Sort the array. Fix `nums[i]`. Set `left = i + 1`, `right = n - 1`. Now it's: *"find two numbers in a sorted sub-array that sum to `-nums[i]`."* The monotonicity from sorting means `sum < target → move left`, `sum > target → move right`, and each step eliminates an entire row of the search space. $O(n^3)$ collapses to $O(n^2)$.

Duplicates are handled by skipping: if `nums[i] == nums[i-1]`, this `i` was already fixed — skip it. After finding a triplet, skip repeated `left` and `right` values too.

```python
class Solution:
    def threeSum(self, nums: list[int]) -> list[list[int]]:
        nums.sort()
        ans = []
        n = len(nums)

        for i in range(n - 2):
            if i > 0 and nums[i] == nums[i - 1]:
                continue

            if nums[i] > 0:
                break

            left, right = i + 1, n - 1

            while left < right:
                total = nums[i] + nums[left] + nums[right]

                if total < 0:
                    left += 1
                elif total > 0:
                    right -= 1
                else:
                    ans.append([nums[i], nums[left], nums[right]])

                    left += 1
                    right -= 1

                    while left < right and nums[left] == nums[left - 1]:
                        left += 1
                    while left < right and nums[right] == nums[right + 1]:
                        right -= 1

        return ans
```

> Time $O(n^2)$ · Space $O(1)$ (excluding sort and output)

The deeper principle: **once your thoughts are sorted, move forward and don't look back.** Sorting the array gives you a direction — each step forward is a commitment, and the monotonicity guarantees you never need to reverse. You fix `i`, you scan `left` and `right` inward, and you never revisit a combination you've already eliminated. The pointers only move in one direction. There is no backtracking, no undo, no "what if I chose wrong?" The sort made the path linear, and linear means forward-only.

**🏢 Workplace**
A complex problem lands on your desk — three teams, three constraints, three stakeholders, and it has to all align. The instinct is to tackle all three simultaneously, juggling everything in parallel. That's the $O(n^3)$ approach: every combination of three people, three timelines, three budgets, all checked against each other. It's exhausting, it's slow, and it produces duplicates — the same conversation had three times with slightly different people.

The smarter move: **reduce dimensions.** Fix one variable — the most constrained one, the one that's hardest to move — and now the problem is simpler. You're not managing three teams' alignment; you're managing two teams' alignment *given* that the third team's constraint is fixed. Sort your constraints by which is most rigid, fix the most rigid, and the remaining problem is one you already know how to solve.

And here's the discipline: **once you've sorted your thoughts and committed to a direction, move forward — don't keep looking back.** In the algorithm, `left` only moves right, `right` only moves left, and `i` never revisits a value it's already fixed. Each step is a commitment. In the workplace, this means: once you've decided on a direction — picked the constraint to fix first, chosen the team to align first — don't keep second-guessing it while scanning forward. The sort gave you the confidence that the direction is right. Revisit only when you've fully scanned the current layer and found nothing — not mid-scan, not halfway through, not every time you feel anxious.

**🌍 Life**
Life's hardest decisions feel like 3Sum: three factors that all have to align — career, relationship, location. Or: energy, time, money. Or: what you want, what you can afford, what's available. The instinct is to hold all three in your head simultaneously and brute-force every combination — $O(n^3)$ mental effort, producing mostly duplicates of the same anxious calculation.

The mature approach: **sort your priorities first, then fix the most constrained one and reduce the rest to a simpler problem.**

What's the most rigid constraint? The one that's hardest to change? Fix it. Maybe it's your location — you can't move this year. Now the problem isn't "career + relationship + location all align" — it's "given this location, what career + relationship combination works?" That's a two-variable problem on a sorted range, and the two-pointer approach applies: scan your options for each remaining variable, and the monotonicity of "what's available given this fixed constraint" tells you which direction to move.

And here's the feeling you're chasing: **once your thoughts are sorted, you move forward without looking back.** You don't revisit the fixed variable while scanning. You don't keep asking "but what if I chose the wrong constraint to fix?" while you're scanning the remaining two. You committed to a direction — the sort gave you that confidence — and now your job is to scan forward, eliminate impossibilities, and trust that the direction was right. If you've sorted correctly and the monotonicity holds, the answer will surface. If it doesn't, you'll know when the scan completes — not by looking back mid-scan, but by reaching the end with no answer found.

That's the discipline: **sort → commit → scan forward → don't look back until the layer is done.** Each layer has its own complete scan. Only after the scan is done do you step to the next `i`, the next fixed variable, the next layer of commitment. The beauty is that this structure — sort, fix, scan, never reverse — works for 3Sum, 4Sum, and for life's hardest multi-variable decisions. The algorithm is telling you: *don't hold everything at once. Fix what's rigid, sort what's flexible, and walk forward in one direction.*

**⚠️ Anti-pattern**
*"I need to consider every possible combination to make sure I don't miss the best one."*
That's the $O(n^3)$ brute-force mindset — and it's worse than slow, it's *paralyzing*. When you try to hold three free variables in your head simultaneously, you're not exploring the space efficiently — you're drowning in it. Every "what about this combination?" is a step that doesn't use monotonicity, doesn't eliminate, doesn't commit. The sort exists precisely so you don't have to do this. Fix one variable, sort the rest, and scan forward. The direction is given to you by the sort — trust it, walk forward, and don't look back until the layer is complete. Holding everything open is not thoroughness; it's the refusal to commit, disguised as diligence.
