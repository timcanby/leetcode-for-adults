<p align="center">🌐 Language: &nbsp;<a href="README.md"><b>English</b></a> &nbsp;·&nbsp; <a href="README.zh.md">中文</a> &nbsp;·&nbsp; <a href="README.ja.md">日本語</a></p>

<p align="center"><a href="../README.md#-the-catalog">← Back to Catalog</a></p>

---

### 13. Two Sum II

> *Given a sorted array, find two numbers that add up to the target.*

**🧩 Algorithm**
The array is sorted. That's not a detail — it's the entire algorithm.

Place one pointer at the left (smallest), one at the right (largest). Compute the sum. There are only three outcomes:

- `sum == target` → done.
- `sum < target` → the sum is too small. Moving `right` leftward only makes it smaller (the values decrease). So every combination pairing the current `left` with any other right endpoint is provably too small. Eliminate `left`. Move it right.
- `sum > target` → the sum is too large. Moving `left` rightward only makes it bigger. So every combination pairing the current `right` with any other left endpoint is provably too large. Eliminate `right`. Move it left.

Each step doesn't just check one pair — it **eliminates an entire row of the search space**. $O(n^2)$ collapses to $O(n)$.

```python
class Solution:
    def twoSum(self, numbers: list[int], target: int) -> list[int]:
        left, right = 0, len(numbers) - 1

        while left < right:
            current_sum = numbers[left] + numbers[right]

            if current_sum == target:
                return [left + 1, right + 1]
            elif current_sum < target:
                left += 1
            else:
                right -= 1

        return []
```

> Time $O(n)$ · Space $O(1)$

The key insight: **order creates determinism.** Because the array is sorted, "move left" always means "increase the sum" and "move right" always means "decrease it." That predictability is what lets you safely discard an endpoint — you *know* the other direction is hopeless, so the remaining one is the only candidate.

Without sorting, you'd need a hash map and $O(n)$ space — because in a chaotic array, no direction is safe to eliminate. You can't discard, so you must remember everything.

**🏢 Workplace**
When you walk into a messy situation — a tangled codebase, a disorganized team, an unclear decision tree — your first instinct might be to start making decisions immediately. Don't. **Establish order first.** Sort the information. Understand what increases and what decreases. Map the dependencies.

Once the landscape is ordered — priorities ranked, constraints identified, relationships clarified — your decisions stop being guesses. You can look at the current state and say: *"this is too small, move toward larger values"* or *"this is too much, move toward smaller values."* Each step eliminates a whole class of wrong moves.

Rushing into strategy before establishing order is the hash-map approach: it works, but it costs $O(n)$ memory and $O(n^2)$ comparison effort. You're holding everything in your head because you haven't built the structure that would let you safely forget.

**🌍 Life**
**Establish order first, then adjust strategy — it's more rational than blindly choosing in chaos.**

When life feels overwhelming — too many options, too many obligations, no clear priority — the instinct is to grab the nearest option and run. But that's brute-forcing a chaotic array. Every choice feels equally valid because nothing is sorted; every direction feels equally plausible because there's no monotonicity.

The mature move: sort first. Rank your options by what matters. Once the array is ordered — priorities from most to least important, energies from highest to lowest, deadlines from nearest to furthest — the two-pointer approach becomes available. You can look at both ends and say: *"this combination is too much, drop the heavier one"* or *"this is too little, move toward more."* Each decision eliminates an entire branch of bad moves.

The act of sorting is not wasted time. It's the precondition for confident, low-cost decisions. Without it, every choice is a hash-map lookup — expensive, exhaustive, and anxiety-inducing. With it, every choice is a pointer move — $O(1)$, deliberate, and safe.

**⚠️ Anti-pattern**
*"Just start trying combinations and see what works."*
That's brute force on an unsorted array. It costs $O(n^2)$ comparisons and $O(n)$ memory because you can't eliminate anything — every direction might be the right one, so you hold everything in your head simultaneously. The sort costs $O(n \log n)$ up front but saves $O(n^2)$ downstream. Skipping the sort to "save time" is the most expensive false economy in problem-solving — and in life.
