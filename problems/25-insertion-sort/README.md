<p align="center">🌐 Language: &nbsp;<a href="README.md"><b>English</b></a> &nbsp;·&nbsp; <a href="README.zh.md">中文</a> &nbsp;·&nbsp; <a href="README.ja.md">日本語</a></p>

<p align="center"><a href="../README.md#-the-catalog">← Back to Catalog</a></p>

---

### 25. Insertion Sort

> *Pick each element and insert it into its correct position among the already-sorted elements to its left.*

**🧩 Algorithm**
Insertion sort doesn't sort by scanning, swapping, or selecting. It sorts by **inserting** — taking each element and gently sliding it leftward through the already-sorted region until it finds its level, like a book being slotted onto a shelf in the right place.

The sorted region grows from the left. Each step: grab the next unsorted element, walk it leftward past anything larger, and drop it where it belongs. Everything above it shifts right by one — a nudge, not a swap. The element isn't "moved to the end" (bubble) or "chosen from the whole field" (selection). It's **placed where it fits** — relative to what's already been settled.

```python
def insertion_sort(nums):
    for i in range(1, len(nums)):
        cur = nums[i]
        j = i - 1

        while j >= 0 and nums[j] > cur:
            nums[j + 1] = nums[j]
            j -= 1

        nums[j + 1] = cur

    return nums
```

> Time $O(n^2)$ worst, $O(n)$ best (nearly sorted) · Space $O(1)$

The deeper principle: **you don't choose in isolation — you choose relative to what's already settled.** The element doesn't have a "correct position" in the abstract. Its position depends on everything to its left — the context that's already been built. Insert it into a different sorted region and it lands somewhere different. The same element, different context, different placement.

And the beauty: **insertion sort is $O(n)$ when the array is nearly sorted.** It doesn't pay the full $O(n^2)$ cost unless the array is truly chaotic. When things are *almost* in order — just a few elements slightly out of place — insertion sort glides. It walks each out-of-place element a short distance to its level and stops. The cost is proportional to how far each element is from where it belongs, not to the total size of the array. Small disruptions, small cost.

**🏢 Workplace**
When you join a team, you don't get to rebuild the org chart. You get **inserted** — into an existing sorted structure, among people who are already in position. Your placement depends on where you fit *relative to the people already there*. The same person, inserted into a different team, lands in a different role. Your "correct position" isn't absolute — it's contextual.

Insertion sort's workplace wisdom: **you don't need to re-sort everything. You need to find your level among what's already settled.** Walk leftward through the existing hierarchy — past the people whose seniority, expertise, or ownership clearly exceeds yours — and stop where you belong. Don't try to jump past everyone (that's not insertion; that's re-sorting). Don't shrink to the bottom (that's not insertion either; that's self-demotion). Walk until you find the level where everything to your left is larger and everything to your right is smaller. That's your position.

And the "nearly sorted" insight: **when a team is already mostly well-organized, a new hire doesn't cause $O(n^2)$ disruption.** One new person joins, walks past the few people they outrank, and slots in. The team doesn't reorganize. The settled region doesn't change. Only the boundary shifts — by one — and the cost is proportional to how far the new person walked, not to the team size. A well-run team absorbs new members gracefully. A chaotic team — where every insertion requires walking past half the org — pays the full $O(n^2)$ cost every time. The lesson: **keep your team nearly-sorted, and every insertion is cheap. Let it drift into chaos, and every new hire triggers a re-sort.**

**🌍 Life**
You don't enter a new city, a new community, or a new phase of life with a blank slate. You get **inserted** — into an existing social structure, among people who are already settled, into a context that's already been built. Where you land depends on where you fit *relative to what's already there*.

The same you — same skills, same personality, same values — inserted into a different city lands in a different social position. In one city you're the newcomer who's slightly behind the established friend group. In another you're the expert who outranks the locals. Your "correct position" isn't a property of you — it's a property of *you in this context*. The element doesn't choose its position. The sorted region around it determines where it fits.

And the "nearly sorted" wisdom for life: **when your life is already mostly in order, each new phase — a new job, a new relationship, a new city — is an $O(n)$ insertion, not an $O(n^2)$ re-sort.** You walk into the new context, shift past the few things that outrank you, slot into your level, and the rest of your life barely moves. The cost is small because the sorted region was already stable. You didn't have to reorganize everything — you just found where the new piece fits among the settled pieces.

But when your life is chaotic — when every new phase requires re-sorting everything — each transition is $O(n^2)$. Every new job forces you to rethink your whole routine. Every new relationship forces you to renegotiate every existing commitment. The lesson: **keep your life nearly-sorted.** Maintain the settled region — the habits, relationships, and routines that already work — so that each new insertion costs only what it needs to cost: the distance from where you are to where you fit, not the full cost of rebuilding from scratch.

And the gentlest insight: **insertion sort doesn't ask the new element to be better than everything to its left. It asks it to find its level.** You don't have to outrank everyone. You don't have to be the best. You have to walk past the things that are clearly larger than you, stop where you belong, and let the sorted region absorb you. The goal isn't to be at the front. The goal is to be *in order* — which means being exactly where you fit, no higher and no lower.

**⚠️ Anti-pattern**
*"I need to rebuild everything from scratch when I join a new context."*
That's not insertion — that's re-sorting the entire array. Insertion sort's whole premise is that the sorted region is *already settled* and the new element just finds its place within it. If you treat every transition as a full re-sort — rebuilding your routine, renegotiating every relationship, redefining every role — you're paying $O(n^2)$ for what should cost $O(n)$. The sorted region exists for a reason: it's the accumulated order that prior insertions built. Respect it. Walk into it. Find your level. Shift what you need to shift — and only what you need to shift — and let the rest stay settled. The cost of inserting into a nearly-sorted life is small. The cost of re-sorting a chaotic life is everything.
