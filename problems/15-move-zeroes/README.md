<p align="center">🌐 Language: &nbsp;<a href="README.md"><b>English</b></a> &nbsp;·&nbsp; <a href="README.zh.md">中文</a> &nbsp;·&nbsp; <a href="README.ja.md">日本語</a></p>

<p align="center"><a href="../README.md#-the-catalog">← Back to Catalog</a></p>

---

### 15. Move Zeroes

> *Move all zeroes to the end of the array, in-place, preserving the relative order of non-zero elements.*

**🧩 Algorithm**
The naive instinct is "push zeroes to the back." That's the wrong framing. The right one: **place each non-zero element where it belongs — at the front, in order.**

Two pointers, same direction, different jobs:
- `read` scans left to right, looking for non-zero values.
- `write` marks where the next non-zero element should go.

Every time `read` finds a non-zero, it writes it to `write`'s position, then `write` advances. The zeroes? They don't need to be "moved" at all — they're what's left behind once the non-zeroes are compacted forward. Fill the rest with zeroes at the end.

The loop invariant: `nums[0:write]` always contains every non-zero element seen so far, in original order. That invariant holds at the start (empty), holds after each step, and holds at the end (complete).

```python
class Solution:
    def moveZeroes(self, nums: list[int]) -> None:
        write = 0

        for read in range(len(nums)):
            if nums[read] != 0:
                nums[write] = nums[read]
                write += 1

        while write < len(nums):
            nums[write] = 0
            write += 1
```

> Time $O(n)$ · Space $O(1)$

The deeper principle: **don't move what you want gone — compact what you want kept.** The zeroes aren't the problem; the non-zeroes are the solution. Focus on getting the real content into the right place, and the noise falls to the back automatically.

**🏢 Workplace**
When a project has noise — legacy code that should be deprecated, meetings that should be cancelled, tasks that should be dropped — the instinct is to "deal with the noise." Schedule the deprecation meeting, file the removal ticket, plan the cleanup sprint.

That's pushing zeroes. It's exhausting, repetitive, and worst-case $O(n^2)$ — every cleanup task creates more cleanup.

The better move: **focus on what you want to keep.** Get the real work — the features that matter, the people who deliver, the processes that work — into the right place first. Once the signal is compacted to the front, the noise naturally falls to the back. You don't need a "zero removal committee" — you need a "non-zero compaction pass" that identifies and preserves what matters, and lets the rest settle where it settles.

**🌍 Life**
Your life has noise — habits that waste time, commitments that drain you, obligations that add nothing. The instinct is to go after the noise: quit the bad habit, cancel the draining commitment, prune the dead weight.

But here's the thing: **you don't need to move the zeroes. You need to compact the non-zeroes.**

Put the things that matter — your core relationships, your real work, your genuine interests — into the front of your life, in the order they deserve. Give them the best slots, the prime hours, the first attention. Once they're compacted into the positions they belong in, the noise doesn't need to be "removed" — it naturally occupies whatever space is left.

This is the loop invariant of a well-lived life: `life[0:write]` always contains what matters most, in the right order. The zeroes — the time-wasters, the energy-drains, the low-value commitments — fall to the back not because you heroically fought them, but because you never gave them the front slots in the first place.

**⚠️ Anti-pattern**
*"I need to eliminate my bad habits one by one."*
That's pushing zeroes to the back — addressing each noise element individually, which is $O(n^2)$ effort and fragile. Instead, compact what you want to keep into the front of your life. The non-zeroes — your real priorities, your genuine interests, your actual relationships — are the solution, not the problem. Get them placed correctly, and the noise takes care of itself. You don't declutter a room by throwing out clutter; you declutter by deciding what deserves space and letting the rest settle.
