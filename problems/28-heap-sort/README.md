<p align="center">🌐 Language: &nbsp;<a href="README.md"><b>English</b></a> &nbsp;·&nbsp; <a href="README.zh.md">中文</a> &nbsp;·&nbsp; <a href="README.ja.md">日本語</a></p>

<p align="center"><a href="../README.md#-the-catalog">← Back to Catalog</a></p>

---

### 28. Heap Sort

> *Build a heap from the array, then repeatedly extract the maximum to the end.*

**🧩 Algorithm**
Heap sort doesn't scan, swap, insert, select, merge, or pivot. It **organizes into a heap** — a structure where every parent is larger than its children — and then it *harvests*: pull the root (the maximum), swap it to the end, restore the heap property, repeat. The sorted region grows from the back, one extracted maximum at a time.

The heap is not the array. The heap is a *relationship* imposed on the array — a set of parent-child obligations where every parent outranks its children. The same elements, arranged differently, form a different heap. The structure isn't in the data; it's in the *rules between* the data.

```python
def heap_sort(nums):
    n = len(nums)

    def sift_down(i, size):
        while True:
            largest = i
            left = i * 2 + 1
            right = i * 2 + 2

            if left < size and nums[left] > nums[largest]:
                largest = left
            if right < size and nums[right] > nums[largest]:
                largest = right

            if largest == i:
                break

            nums[i], nums[largest] = nums[largest], nums[i]
            i = largest

    # Phase 1: build the heap — bottom-up, from the last parent to the root
    for i in range(n // 2 - 1, -1, -1):
        sift_down(i, n)

    # Phase 2: extract max, swap to end, restore heap, shrink
    for end in range(n - 1, 0, -1):
        nums[0], nums[end] = nums[end], nums[0]
        sift_down(0, end)

    return nums
```

> Time $O(n \log n)$ — always, guaranteed · Space $O(1)$

The deeper principle: **you don't sort the data directly — you impose a structure on the data, and the structure produces the order for you.** The heap is a set of local obligations: each parent must be larger than its children. No global knowledge. No comparison against every other element. Just: "are you bigger than your children?" answered at every node, from the bottom up.

Phase 1 — **build the heap** — starts from the bottom. The leaves are already heaps (trivially — they have no children). So you start from the last parent and work upward. Each `sift_down` pushes one element down to its level. By the time you reach the root, the whole array is a heap — every parent outranks its children, and the maximum sits at the top. You didn't sort the array. You imposed a *rule system* — and the rule system sorted it for you.

Phase 2 — **harvest** — is the payoff. The maximum is always at the root. You swap it to the end (its final position), then restore the heap property by sifting the new root down. The sorted region grows from the back. Each extraction is $O(\log n)$ — the displaced element walks down at most $\log n$ levels to its level. $n$ extractions → $O(n \log n)$. The structure does the work; you just harvest.

And the guarantee: **heap sort is $O(n \log n)$ in the worst case, in-place, with no extra space.** It has the guarantee of merge sort (no $O(n^2)$ degradation) and the space efficiency of quick sort (no buffer needed). The trade-off: it's less cache-friendly, less intuitive, and has worse constants than either. The heap's structure — implicit, array-based, parent-child relationships computed by index arithmetic — is efficient but opaque. You can't "read" a heap the way you can read a sorted array. The order is there, but it's *encoded* in the structure, not visible on the surface.

**🏢 Workplace**
You don't sort a team by comparing every person against every other person. You **impose a structure** — a reporting hierarchy where each manager outranks their reports — and the structure produces the order for you.

The heap is the org chart. Not the *visual* org chart (that's a tree), but the *obligation structure*: every manager is responsible for their direct reports. The root — the CEO — is the maximum. The sorted region — the "completed projects" — grows from the back as the root is extracted: the top performer delivers, their result is locked in, and the remaining team reorganizes to fill the gap.

Phase 1 — **build the org**: you don't start at the top. You start at the bottom — the leaf nodes, the individual contributors — and work upward. Each layer of management is added from the bottom up. By the time you reach the root, every manager outranks their reports, and the best person is at the top. You didn't *compare* everyone. You imposed a *rule*: "each manager must be stronger than their reports" — and the rule produced the hierarchy.

Phase 2 — **harvest**: the top performer delivers a result. It's locked in — that project is done, that person's contribution is recorded. Then the team reorganizes: someone steps up to fill the gap, `sift_down` pushes them to their level, and the next-best person surfaces to the top. The sorted region — the completed projects — grows from the back. Each extraction is one project, and the heap reorganizes in $O(\log n)$ — not $O(n)$, because only one path through the tree needs adjusting, not the whole structure.

And the trade-off: **the heap structure is efficient but opaque.** You can't "read" the team's ranking by looking at the org chart the way you can read a sorted list. The hierarchy is there, but it's *encoded* in the reporting relationships, not visible on the surface. The CEO is the maximum — but the second-best person might be three levels down, buried in a subtree. The structure is correct (the maximum is always extractable), but it's not transparent. You trade readability for efficiency. For a team that needs to be *understood* by outsiders — investors, new hires, the public — a sorted array (a transparent ranking) is better. For a team that just needs to *produce* — extract the best, lock it in, reorganize, repeat — the heap is ideal.

**🌍 Life**
You don't sort your life by ranking every experience against every other experience. You **impose a structure** — a set of local obligations: "each day must be better than the days it produces" — and the structure produces the order for you.

The heap is your life's obligation system. Not the calendar (that's a sorted array), but the *relationship structure*: each commitment must be larger than the sub-commitments it creates. Your health is the root — it must be larger than (more important than) your work and your relationships, because if it collapses, everything below it collapses. Your work is a child of your health — it must be larger than your individual tasks. Your relationships are another child — they must be larger than your individual social commitments.

Phase 1 — **build the life-heap**: you don't start by deciding your life's purpose (the root). You start at the bottom — the daily habits, the individual commitments — and work upward. Each level: "is this habit bigger than the habits it produces? Is this commitment larger than the sub-commitments it creates?" By the time you reach the root — your health, your core — the whole structure is a heap. Every obligation is larger than the obligations it creates. The maximum — the thing that matters most — sits at the top.

Phase 2 — **harvest**: the top priority delivers. You extract it — you live that day, you complete that project, you honor that commitment — and it's locked in. The sorted region — your lived life — grows from the back. Then the remaining structure reorganizes: the next priority surfaces to the top, `sift_down` pushes the displaced element to its level, and the heap is restored. Each day is one extraction. The heap reorganizes in $O(\log n)$ — one path through your life's tree, not the whole structure.

And the trade-off: **a well-structured life is opaque to outsiders.** You can't "read" someone's priorities by looking at their calendar the way you can read a sorted list. The structure is there — the most important thing is always at the top — but it's *encoded* in the relationships between commitments, not visible on the surface. The person who looks "busy" might be extracting maximums efficiently. The person who looks "relaxed" might have a perfectly maintained heap. You can't judge the structure by the surface. The heap is efficient, guaranteed, and opaque — and that opacity is the price of the guarantee.

And the wisdom: **the heap doesn't require global knowledge.** Merge sort needs to see both halves. Quick sort needs to partition the whole array. Heap sort only needs to know: "are you bigger than your children?" — a *local* question, answered at every node, from the bottom up. You don't need to know how your life compares to everyone else's life. You don't need to rank yourself globally. You need to maintain one local obligation: **each priority must be larger than the priorities it creates.** Keep that rule at every level, and the maximum — the thing that matters most — will always surface to the top. Not because you searched for it. Because the structure *produced* it.

**⚠️ Anti-pattern**
*"I need to rank everything in my life by importance before I can start."*
That's sorting the array directly — comparing every element against every other, producing a total ordering, then acting on it. It's the most intuitive approach and the most paralyzing: you spend all your energy ranking and none acting. The heap says: **you don't need a total ordering. You need local obligations.** Don't rank everything against everything. Just maintain one rule at each level: "is this priority bigger than the priorities it creates?" Answer that locally — at each commitment, each day, each project — and the global order takes care of itself. The maximum surfaces not because you hunted for it, but because the structure *delivers* it. Skip the global ranking. Impose the local rule. Harvest what the structure produces. The heap's promise is that you never need to see the whole picture — you only need to honor the relationship between each layer and the one below it. $O(n \log n)$ guaranteed, in-place, no buffer — because the structure does the remembering for you.
