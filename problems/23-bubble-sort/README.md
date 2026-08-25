<p align="center">🌐 Language: &nbsp;<a href="README.md"><b>English</b></a> &nbsp;·&nbsp; <a href="README.zh.md">中文</a> &nbsp;·&nbsp; <a href="README.ja.md">日本語</a></p>

<p align="center"><a href="../README.md#-the-catalog">← Back to Catalog</a></p>

---

### 23. Bubble Sort

> *Repeatedly compare adjacent pairs and swap them into order. The largest unsorted element "bubbles up" to its correct position each pass.*

**🧩 Algorithm**
Bubble sort is the most derided algorithm in computer science — $O(n^2)$, naive, the thing you learn first and then immediately learn to never use. But its mechanics hold a lesson that quicksort doesn't.

Each pass: walk left to right. Compare each pair of neighbors. If they're out of order, swap them. After one full pass, the largest element has "bubbled up" to the end — it's in its final position. The next pass handles one fewer element. Repeat until a pass makes no swaps — meaning everything is already in order.

```python
def bubble_sort(nums):
    n = len(nums)

    for end in range(n - 1, 0, -1):
        swapped = False

        for i in range(end):
            if nums[i] > nums[i + 1]:
                nums[i], nums[i + 1] = nums[i + 1], nums[i]
                swapped = True

        if not swapped:
            break

    return nums
```

> Time $O(n^2)$ worst, $O(n)$ best (already sorted) · Space $O(1)$

The deeper principle: **the biggest problems surface first.** Each pass pushes the largest unsorted element to the end — the most out-of-place thing gets exposed and corrected first. You don't hunt for the problem; you walk the sequence, and the big ones reveal themselves by colliding with their neighbors.

And the `swapped` flag is the secret wisdom: **if a full pass produces no swaps, you're done.** You don't need to know that you're done in advance. You just keep making passes, and the absence of conflict *is* the signal that the order has been achieved. The sorted state is detected not by checking every element — but by observing that the friction has stopped.

**🏢 Workplace**
The biggest organizational problems surface first. You don't need a grand audit to find them — you walk the team, person by person, comparing adjacent relationships. Wherever there's friction — a pair that's out of order, a role that's larger than its neighbor — that's where the biggest unsorted element lives. Swap them: realign the reporting structure, clarify the responsibility boundary, move the overloaded person.

After each pass, the biggest misalignment has bubbled to its final position — settled, sorted, no longer creating friction with its neighbors. Then you make another pass, and the next-largest misalignment surfaces.

And the `swapped` flag is the leadership insight: **if a full pass through the org produces no conflicts, you're sorted.** You don't need to check every report, every metric, every process. If a full walk-through finds nothing out of order — no friction, no misalignment, no pair that needs swapping — the organization is stable. The absence of friction *is* the proof. Stop auditing. Stop optimizing. You're done — until the next restructuring introduces new unsorted elements.

The trap is that bubble sort is $O(n^2)$ — each pass is expensive, and you might need $n$ passes. In an organization, this means: don't restructure the whole company every week. But also don't skip the pass entirely. The healthy pattern: walk the team regularly, let the biggest conflicts surface, resolve them, and stop when a pass produces no friction. The organization that does this — regular passes, small swaps, early stopping — is healthier than the one that does one massive reorg every two years or the one that never checks at all.

**🌍 Life**
Your life's biggest problems surface first — if you let them. You don't need to hunt for them. Walk your life day by day, comparing adjacent moments: yesterday vs. today, this week vs. last week, this commitment vs. the next one. Wherever there's friction — a relationship that's out of order, a habit that's bigger than its slot, a commitment that's pressing against its neighbor — that's where the biggest unsorted element lives.

The bubble sort approach to life: **don't try to fix everything at once. Fix the biggest friction, let it settle, then make another pass.** Each pass moves the largest misalignment to its right place. Then the next-largest surfaces. You don't solve the small problems first — you solve the big ones first, because they're the ones that collide with their neighbors and create visible friction.

And the `swapped` flag is the life wisdom: **if a full pass through your life produces no friction, you're sorted.** You don't need to journal every detail, audit every habit, optimize every hour. If a full walk-through of your week finds nothing out of order — no relationship straining, no habit overflowing, no commitment pressing against its neighbor — your life is stable. The absence of friction *is* the proof. Stop optimizing. Stop journaling about problems that don't exist. Go live.

The discipline is knowing that bubble sort is not about efficiency — it's about **honesty**. It's the algorithm that refuses to pretend. It walks the actual sequence, looks at actual neighbors, and only acts when something is genuinely out of order. No clever partitioning, no divide-and-conquer, no skipping ahead. Just: walk it, see it, fix it, and stop when the friction stops. That's not the fastest way to sort an array. But it might be the most honest way to sort a life.

**⚠️ Anti-pattern**
*"I'll just fix the small things first and the big ones will sort themselves out."*
That's insertion sort, not bubble sort — and it's backwards. The small things *won't* fix the big ones; the big ones will keep colliding with their neighbors and creating friction until you address them directly. Bubble sort works because the biggest unsorted element *must* surface — it can't hide, because it's larger than everything around it and keeps pressing against its neighbors until it reaches its level. The small problems can hide indefinitely; the big ones can't. Fix the biggest friction first, let it settle, and repeat. The small problems either resolve themselves in the process or surface when they become big enough to create friction. Don't sort from the bottom up — sort from the top down, and let the small ones find their own level.
