<p align="center">🌐 Language: &nbsp;<a href="README.md"><b>English</b></a> &nbsp;·&nbsp; <a href="README.zh.md">中文</a> &nbsp;·&nbsp; <a href="README.ja.md">日本語</a></p>

<p align="center"><a href="../README.md#-the-catalog">← Back to Catalog</a></p>

---

### 16. Remove Duplicates from Sorted Array

> *Remove duplicates in-place from a sorted array. Return the count of unique elements.*

**🧩 Algorithm**
The array is sorted. That means duplicates are always adjacent — you don't need to track what you've seen, only compare what's next to what you last kept. Sorting turns global deduplication into a local comparison.

Two pointers, same direction: `read` scans forward, `write` marks the last confirmed unique element. Each time `read` finds a value different from `nums[write]`, that's a new unique — advance `write`, write it in. Duplicates are skipped not because they're "deleted" but because they're never written to the valid zone.

The loop invariant: `nums[0 : write + 1]` always contains every unique element seen so far, in original order. The sorted front stays clean. Everything past `write` is irrelevant — it's the scrap pile, and nobody cares what's on it.

```python
class Solution:
    def removeDuplicates(self, nums: list[int]) -> int:
        if not nums:
            return 0

        write = 0

        for read in range(1, len(nums)):
            if nums[read] != nums[write]:
                write += 1
                nums[write] = nums[read]

        return write + 1
```

> Time $O(n)$ · Space $O(1)$

The key insight: **sort first, deduplicate second.** If the array were unsorted, you'd need a hash set — $O(n)$ extra space — because any new element might be a repeat of anything seen before, and you'd have to remember all of them. Sorting makes duplicates adjacent, so the problem collapses from *"have I seen this anywhere?"* to *"is this different from the one right before me?"* — a local question that costs $O(1)$ to answer.

**🏢 Workplace**
When you inherit a mess — a bloated codebase, a sprawling team structure, a tangled set of overlapping responsibilities — the instinct is to start cutting: remove the duplicates, merge the redundancies, clean up the sprawl.

But here's the thing: **you can't deduplicate chaos.** If nothing is sorted, every piece might be a copy of any other piece. You'd need to hold the entire system in your head — a mental hash set — just to spot the redundancies. That's $O(n)$ brain-space and $O(n^2)$ comparison effort, and you'll miss things anyway.

The smart move: **sort first.** Group related work, align adjacent responsibilities, arrange the mess into clusters where similar things sit next to each other. Once the system is sorted — by team, by domain, by ownership — duplicates become obvious because they're *adjacent*. The question stops being *"is this duplicated somewhere in the org?"* and becomes *"is this the same as what I just looked at?"* — which you can answer in one glance.

Sorting is not a waste of time. It's the precondition that makes deduplication $O(1)$ per step instead of $O(n)$. Without it, you're scanning the whole org chart every time you find a potential duplicate. With it, you compare with your neighbor and move on.

**🌍 Life**
**Sort the orderly things first, then tidy up the chaos.**

Your life has both: the sorted parts — habits that are already in a rhythm, relationships that are already in their lanes, routines that already flow — and the chaotic parts — the sprawling to-do list, the half-finished projects, the commitments that overlap and duplicate and contradict.

The instinct is to attack the chaos directly: prune the redundant commitments, merge the overlapping projects, remove the duplicate obligations. But deduplicating an unsorted life means holding everything in your head at once — checking each new item against every prior one — because in a chaotic life, anything might be a duplicate of anything.

The mature approach: **establish order first.** Sort your commitments by category. Sort your goals by domain. Sort your relationships by proximity. Once similar things are adjacent — the three volunteer commitments that overlap, the two side projects that serve the same goal, the five social obligations that drain the same energy — the duplicates become visible without effort. You don't need a grand audit; you need the items sorted so that "is this the same as what's next to it?" answers itself.

And here's the deeper truth: **the sorted part of your life doesn't need fixing.** The habits that are already in rhythm, the relationships that already work, the routines that already flow — those are the `nums[0:write+1]` that are already clean. Don't waste energy reorganizing what's already sorted. Spend it on sorting the chaotic part so its redundancies become locally visible — then compact the uniques forward and let the noise settle to the back.

**⚠️ Anti-pattern**
*"I need to audit everything to find what's redundant."*
That's running deduplication on an unsorted array. It costs $O(n^2)$ comparisons and $O(n)$ memory — you're holding the entire system in your head, checking each element against every prior one, and you'll still miss things. Sort first. Once similar items are adjacent, redundancy becomes a local question — *"is this the same as its neighbor?"* — not a global one. The sort costs $O(n \log n)$ upfront but turns the dedup from a marathon into a walk down the block. Auditing chaos without sorting it first is the most expensive way to find what you already could have seen.
