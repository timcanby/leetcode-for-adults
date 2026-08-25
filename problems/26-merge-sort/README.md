<p align="center">🌐 Language: &nbsp;<a href="README.md"><b>English</b></a> &nbsp;·&nbsp; <a href="README.zh.md">中文</a> &nbsp;·&nbsp; <a href="README.ja.md">日本語</a></p>

<p align="center"><a href="../README.md#-the-catalog">← Back to Catalog</a></p>

---

### 26. Merge Sort

> *Split the array in half, sort each half, then merge the two sorted halves back together.*

**🧩 Algorithm**
Merge sort doesn't sort by scanning, swapping, inserting, or selecting. It sorts by **divide-and-conquer**: cut the problem in half, solve each half independently, then stitch the results together. And it does this *recursively* — each half gets cut into quarters, each quarter into eighths — until the pieces are trivially small (one element, already sorted). Then it merges back up the chain, two sorted halves at a time, until the whole array is one sorted whole.

```python
def merge_sort(nums):
    if len(nums) <= 1:
        return nums

    mid = len(nums) // 2
    left = merge_sort(nums[:mid])
    right = merge_sort(nums[mid:])

    ans = []
    i = j = 0

    while i < len(left) and j < len(right):
        if left[i] <= right[j]:
            ans.append(left[i])
            i += 1
        else:
            ans.append(right[j])
            j += 1

    ans.extend(left[i:])
    ans.extend(right[j:])
    return ans
```

> Time $O(n \log n)$ — always, guaranteed · Space $O(n)$

The deeper principle: **big problems are just small problems you haven't cut in half yet.**

The brilliance is in the recursion — the *self-similarity*. The function calls itself on a smaller version of the same problem. It doesn't need to know how to sort a million elements. It needs to know how to sort two elements (trivial: compare and order) and how to merge two sorted lists (walk both, pick the smaller). That's it. Cut → recurse → merge. The million-element sort takes care of itself through $\log_2(n)$ levels of halving.

And the guarantee: **merge sort's $O(n \log n)$ is not just typical — it's worst-case.** Unlike quicksort, which degrades to $O(n^2)$ on bad input, merge sort's performance is *structurally guaranteed* by the math. Each level does $O(n)$ work. There are exactly $\log_2(n)$ levels. No input can break it. The cost is fixed by the size, not by the arrangement. Chaos doesn't tax it. The guarantee comes from the structure — the divide is always in half, the merge is always linear — and structure doesn't lie.

The trade-off: **merge sort pays $O(n)$ space for its $O(n \log n)$ guarantee.** It needs a buffer to hold the merged result. Unlike in-place sorts that shuffle within the array, merge sort copies and combines. The guarantee costs memory. You pay for the certainty that no input will ever surprise you.

**🏢 Workplace**
The biggest projects don't get solved by one person at one desk. They get solved by **divide-and-conquer**: split the project in half, give each half to a team that can handle it independently, then merge the results.

The merge sort wisdom: **you don't need to know how to solve the whole problem. You need to know how to split it, and how to merge the solutions.** If you can split a problem into two independent sub-problems, and you can merge two sorted solutions into one coherent answer, then the size of the problem doesn't matter — it just adds one more level of recursion.

And the guarantee: **a well-structured team's performance is $O(n \log n)$ regardless of the project's difficulty.** If each level of your org can split work and merge results, the total cost is fixed by the structure, not by the content. A hard project takes more levels (deeper recursion), but each level does the same kind of work: split, solve, merge. No project — however chaotic — degrades the structure to $O(n^2)$ if the splits are clean and the merges are competent. The structure protects you from the chaos.

But the trade-off: **merge sort pays space for its guarantee.** In an org, "space" is coordination overhead — the communication cost of keeping two teams in sync, the documentation cost of making each half's output mergeable. Divide-and-conquer isn't free; it requires a buffer — meetings, specs, interfaces — to hold the merge. Skip the buffer, and you get two sorted halves that don't fit together. The merge fails not because the halves are wrong, but because they were built without knowing how they'd combine.

**🌍 Life**
The biggest life problems — "build a career," "raise a family," "find your purpose" — feel impossible because they're whole-array problems. You can't sort a million elements by comparing each pair. But you can sort a million elements if you cut the problem in half, and cut it again, and again, until each piece is small enough to hold in your hand.

The merge sort approach to life: **stop trying to solve the whole problem. Split it.** "Build a career" becomes "figure out what I'm good at" + "figure out what the market needs." Each of those splits again: "what I'm good at" becomes "what skills I have" + "what skills I want to learn." Keep splitting until each piece is a single decision: "take this course," "read this book," "apply to this role." Trivially solvable. Then merge back up: combine the skills into a profile, combine the profile with market needs into a career direction.

And the guarantee: **the structure protects you from the chaos.** No matter how overwhelming the problem feels, if you can split it in half and merge the solutions, the total cost is $O(n \log n)$ — not $O(n^2)$. You never face the whole problem at once. You face $\log_2(n)$ levels, each of which is just: split, solve a smaller piece, merge. The recursion is the protection. The levels are the buffer. You don't have to hold the whole problem in your head — you hold one level at a time, and the structure handles the rest.

And the trade-off — the space cost: **merge sort requires you to hold the intermediate results.** You can't just split and forget. Each half's solution must be *kept* — in memory, in notes, in a plan — until the merge happens. Splitting without remembering the intermediate solutions is not merge sort; it's just scattering. The space cost of divide-and-conquer in life is the cost of *tracking your progress*: journaling, planning, reviewing. You pay $O(n)$ space to hold the pieces so you can merge them. Skip it, and you have two sorted halves and no way to combine them — two halves of a life that don't fit into a whole.

**⚠️ Anti-pattern**
*"I'll just split the problem into smaller pieces and tackle them one by one."*
That's not merge sort — that's just... making a to-do list. The missing piece is the **merge**. Splitting a problem into sub-problems is only half the algorithm. The other half — the half that makes it $O(n \log n)$ instead of $O(n^2)$ — is *combining the solved sub-problems into a coherent whole*. If you split a project into tasks, solve each task, but never integrate the results, you have a pile of sorted fragments, not a sorted array. The merge is where most projects fail: not in the splitting, not in the solving, but in the *combining*. The merge requires knowing how the pieces fit together — what interfaces they share, what order they go in, what conflicts arise when two sorted halves meet. Splitting is easy. Merging is the art. If you can split but not merge, you're paying $O(n)$ to create fragments and $O(n^2)$ to clean up the mess. The merge is the algorithm's soul — and the project's, and the life's.
