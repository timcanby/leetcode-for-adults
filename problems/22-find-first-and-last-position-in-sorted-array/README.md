<p align="center">🌐 Language: &nbsp;<a href="README.md"><b>English</b></a> &nbsp;·&nbsp; <a href="README.zh.md">中文</a> &nbsp;·&nbsp; <a href="README.ja.md">日本語</a></p>

<p align="center"><a href="../README.md#-the-catalog">← Back to Catalog</a></p>

---

### 22. Find First and Last Position in Sorted Array

> *Find the starting and ending index of a target value in a sorted array. If not found, return [-1, -1].*

**🧩 Algorithm**
You're not looking for *a* target — you're looking for the **edges** of the target's range. The array is sorted, so all occurrences of `target` are contiguous. The question isn't "does target exist?" — it's "where does the target *start* and where does it *end*?"

Two binary searches:
- `lower_bound(target)` → the first index where `nums[mid] >= target`. This is the **left edge** — where the target's range begins.
- `lower_bound(target + 1) - 1` → the last index where `nums[mid] < target + 1`. This is the **right edge** — where the target's range ends.

```python
class Solution:
    def searchRange(self, nums: list[int], target: int) -> list[int]:
        def lower_bound(x):
            left, right = 0, len(nums)

            while left < right:
                mid = left + (right - left) // 2

                if nums[mid] < x:
                    left = mid + 1
                else:
                    right = mid

            return left

        left_idx = lower_bound(target)

        if left_idx == len(nums) or nums[left_idx] != target:
            return [-1, -1]

        right_idx = lower_bound(target + 1) - 1

        return [left_idx, right_idx]
```

> Time $O(\log n)$ · Space $O(1)$

The deeper principle: **finding the boundaries is not the same as finding the value.** You could search for `target` and find it at index 5 — but that doesn't tell you whether the range is `[5, 5]` or `[3, 12]`. Finding *one* occurrence answers "does it exist?" Finding the *edges* answers "how far does it go?"

The trick is that `lower_bound` finds a *threshold*, not a *value*. `lower_bound(target)` doesn't find "where target is" — it finds "where the array first becomes ≥ target." That threshold is the left edge. And `lower_bound(target + 1)` finds "where the array first becomes ≥ target + 1" — the position right after the target's range. Subtract one, and you have the right edge.

You're not asking *"is this the target?"* You're asking *"is this the boundary where the target's territory begins and ends?"* The territory is defined by thresholds, not by individual hits.

**🏢 Workplace**
When you join a company, you don't need to find *a* project that uses your skill. You need to find the **edges of the territory** where your skill applies.

Finding one occurrence — one project, one team, one task that uses your expertise — is comforting but misleading. It tells you "yes, my skill is used here." It doesn't tell you whether that's a one-off assignment or a three-year mandate. It doesn't tell you where the territory starts and ends.

The `lower_bound` approach: find the *threshold* — the first project where your skill level becomes relevant. That's your left edge. Then find the threshold where your skill *stops* being the deciding factor — where the next tier of challenges begins, where senior+ expertise takes over. That's your right edge. The territory between is your operating range.

And here's the career insight: **if the left edge and right edge are the same — if `lower_bound(target) == lower_bound(target + 1)` — the target doesn't exist in the array.** You found a threshold but no territory. The company *needs* your skill level in theory, but no role *uses* it. That's the `[-1, -1]` of career: the skill is nominally required but the range is empty. Knowing the edges — not just one hit — tells you whether you're actually needed or just technically qualified.

**🌍 Life**
You don't need to find *a* moment of happiness. You need to find the **range** — the conditions under which happiness is sustainable.

Finding one good day — one moment of flow, one conversation that felt real — is a single hit. It tells you "happiness is possible." It doesn't tell you whether that happiness is a one-off or a recurring pattern. It doesn't tell you where the happiness territory *starts* and where it *ends*.

The `lower_bound` approach to your life: find the *threshold* — the first condition where happiness begins. Maybe it's: "when I sleep 7+ hours and see one close friend per week." That's the left edge. Then find where it ends — the condition where the happiness stops being stable, where the next tier of stress begins. Maybe it's: "when I take on more than 2 commitments per week." That's the right edge.

The territory between is your happiness range. Not a single peak to chase, but a **band of conditions** where happiness is sustainable. You're not looking for one target hit — you're looking for the edges of the range where the hit is *guaranteed*.

And the life insight: **if the left edge and right edge are the same — if the conditions for happiness are so narrow that the range is empty — the target doesn't exist in the array.** You found a threshold (happiness is *possible*) but no territory (happiness isn't *sustainable*). That's the `[-1, -1]` of life: theoretically achievable but practically unreachable. The fix isn't to chase the single hit harder. The fix is to **widen the range** — lower the threshold, broaden the conditions, expand the territory where happiness lives — so that the edges are far enough apart for a life to fit between them.

**⚠️ Anti-pattern**
*"I found one instance — that proves it's there."*
Finding one occurrence at index 5 tells you the target *exists*. It doesn't tell you the range is `[5, 12]` or `[5, 5]` or whether `5` was even the target and not a coincidence. The single hit answers "does it exist?" — the wrong question. The right question is "where does it *begin* and where does it *end*?" — the boundaries, not the middle. Finding the boundaries costs the same $O(\log n)$ as finding one hit — two binary searches instead of one — but it tells you the *shape* of the territory, not just that it's non-empty. And knowing the shape — the edges, the range, where things start and end — is what lets you decide whether the territory is worth inhabiting.
