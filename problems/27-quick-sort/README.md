<p align="center">🌐 Language: &nbsp;<a href="README.md"><b>English</b></a> &nbsp;·&nbsp; <a href="README.zh.md">中文</a> &nbsp;·&nbsp; <a href="README.ja.md">日本語</a></p>

<p align="center"><a href="../README.md#-the-catalog">← Back to Catalog</a></p>

---

### 27. Quick Sort

> *Pick a pivot, partition the array into "less than pivot" and "greater than pivot", then recurse on each side.*

**🧩 Algorithm**
Quick sort doesn't divide evenly. It **picks a pivot** — one element from the array — and uses it as a fulcrum. Everything smaller goes left. Everything larger goes right. The pivot ends up in its final position. Then it recurses on each side.

The pivot is not the smallest or the largest. It's not the best or the most important. It's just *a* value, chosen as the reference point. The magic isn't in the pivot — it's in the **partition**: the act of organizing everything relative to a single reference, so that the problem splits into two independent sub-problems.

```python
def quick_sort(nums):
    def sort(left, right):
        if left >= right:
            return

        pivot = nums[(left + right) // 2]
        i, j = left, right

        while i <= j:
            while nums[i] < pivot:
                i += 1
            while nums[j] > pivot:
                j -= 1

            if i <= j:
                nums[i], nums[j] = nums[j], nums[i]
                i += 1
                j -= 1

        sort(left, j)
        sort(i, right)

    sort(0, len(nums) - 1)
    return nums
```

> Time $O(n \log n)$ average, $O(n^2)$ worst · Space $O(\log n)$

The deeper principle: **progress doesn't require perfect balance — it requires a reference point.** Merge sort cuts perfectly in half every time — elegant, guaranteed, but it needs extra space to hold the halves. Quick sort picks a pivot and partitions in-place — messy, probabilistic, but it needs no buffer. It gambles on the pivot being roughly central, and most of the time, that's good enough.

The trade-off is the defining one: **quick sort is faster than merge sort in practice, but it can degrade to $O(n^2)$.** If the pivot is consistently the worst choice — the smallest or the largest — each "partition" peels off one element and recurses on the rest. $n$ levels of recursion, each doing $O(n)$ work. The worst case isn't rare in theory; it's rare in practice because most inputs are "random enough" that pivots land roughly in the middle. But it *can* happen, and when it does, the algorithm that was supposed to be fast becomes the slowest in the room.

The lesson is in the vulnerability: **quick sort's weakness is not the algorithm — it's the pivot.** A good pivot makes it $O(n \log n)$. A bad pivot makes it $O(n^2)$. The same algorithm, same code, same structure — different pivot, different performance. The pivot is the variable that determines whether the whole thing works or falls apart.

**🏢 Workplace**
Every reorganization needs a pivot — **a reference point that everything else rearranges around.** Not the most senior person. Not the most critical project. Just *a* person, *a* project, *a* value that you choose as the anchor, and then you partition: "does this report to the pivot or not? Does this align with the pivot or not?"

The quick sort wisdom: **you don't need perfect balance. You need a pivot and a partition.** Pick a team lead. Reorganize everything relative to them: who reports up, who reports sideways, who's independent. The pivot doesn't have to be the best lead — they have to be *good enough as a reference* that the partition is roughly even. If 80% of the org ends up on one side, the pivot was bad. If it's roughly 50/50, the pivot was good enough.

And the vulnerability: **quick sort degrades when the pivot is consistently bad.** In an org, this is the restructure where the "pivot" — the person, the project, the principle — is so extreme that everything ends up on one side. You picked the most junior person as the anchor, so everyone else is "above" them. You picked the most niche project, so nothing else "relates" to it. The partition fails, the recursion deepens, and each round peels off one person. That's the $O(n^2)$ reorganization: the one where every restructuring decision moves exactly one person and requires another full pass. A good pivot makes the reorg fast. A bad pivot makes it grind.

The fix is not a better algorithm — it's a **better pivot**. Pick the pivot that splits the problem roughly in half. Not the most extreme person. Not the most extreme project. The one in the middle — the one most others relate to, the one whose role most naturally divides the org into balanced halves. The pivot is the lever; the partition is the move; the balance is what makes it quick.

**🌍 Life**
Every major life decision needs a pivot — **a single value, a single priority, a single criterion that you organize everything else around.**

"Should I take this job?" The pivot isn't salary. The pivot isn't prestige. The pivot is the one value that, when you hold it up and partition everything else relative to it, splits your life roughly in half: "what matters most to me right now?" Pick that. Everything above it goes in the "yes" pile. Everything below it goes in the "no" pile. The pivot doesn't have to be the *best* value — it has to be *good enough as a reference* that the partition is balanced.

The quick sort approach to a decision: **don't weigh every factor equally. Pick the one that matters most, partition relative to it, and recurse on the rest.** The decision that felt like a million-factor optimization becomes a pivot + a partition + a recursion. You don't hold everything in your head. You hold one pivot, sort relative to it, and the rest falls into two smaller, more manageable piles.

And the vulnerability — the $O(n^2)$ life: **when your pivot is consistently extreme, every decision peels off one factor and recurses on the rest.** You pick the most extreme criterion — "must pay $500K, must be remote, must be a startup, must be in my exact city" — and everything fails the partition. Each factor gets handled one at a time, in isolation, with full recomputation. The decision takes months. A balanced pivot — "what matters most to me right now?" — splits the problem in half and recurses on two smaller piles. An extreme pivot — "the one perfect job" — peels off one factor per pass and never converges.

The wisdom: **your pivot is your priority.** Not your highest priority — your *most dividing* priority. The one that, when you hold it up, sorts the rest of your life into two roughly equal piles: "above this" and "below this." If everything falls on one side, your pivot is too extreme. If it splits roughly evenly, your pivot is right. The algorithm doesn't ask for a perfect pivot. It asks for a *good enough* one — and "good enough" means "divides the problem."

**⚠️ Anti-pattern**
*"I'll weigh every factor equally and find the optimal balance."*
That's not quick sort — that's the $O(n^2)$ approach: every factor compared against every other factor, every trade-off evaluated in full, every angle optimized simultaneously. The whole point of the pivot is that **you don't weigh everything equally.** You pick one reference point, sort relative to it, and trust that the partition will make the sub-problems smaller. If you refuse to pick a pivot — if every factor is equally weighted, every consideration equally important — you never partition. You just compare everything against everything forever. The pivot is not a compromise; it's a *commitment*. You commit to one reference point, partition around it, and accept that the partition is imperfect but *progress*. $O(n \log n)$ imperfect progress beats $O(n^2)$ perfect analysis — in sorting, in careers, and in life.
