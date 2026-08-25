<p align="center">🌐 Language: &nbsp;<a href="README.md"><b>English</b></a> &nbsp;·&nbsp; <a href="README.zh.md">中文</a> &nbsp;·&nbsp; <a href="README.ja.md">日本語</a></p>

<p align="center"><a href="../README.md#-the-catalog">← Back to Catalog</a></p>

---

### 24. Selection Sort

> *Find the minimum element, swap it into position, repeat. Each pass locks one element into its final place.*

**🧩 Algorithm**
Selection sort is the algorithm of **deliberate commitment**. It scans the entire unsorted region, finds the single smallest element, and places it at the front — irrevocably, permanently, in its final position. Then it does it again with the rest. And again. Until everything is in place.

No hedging. No "I'll come back and adjust this later." Each pass makes exactly one decision — the minimum — and commits to it fully. The element placed at position `i` will never move again. It's done. Settled. Final.

```python
def selection_sort(nums):
    n = len(nums)

    for i in range(n):
        min_idx = i

        for j in range(i + 1, n):
            if nums[j] < nums[min_idx]:
                min_idx = j

        nums[i], nums[min_idx] = nums[min_idx], nums[i]

    return nums
```

> Time $O(n^2)$ — always, no best-case shortcut · Space $O(1)$

The deeper principle: **see everything before committing to anything.** Unlike bubble sort — which acts on local friction as it encounters it — selection sort refuses to act until it has surveyed the *entire* remaining field. It won't swap the first out-of-order pair it sees. It waits. It checks every candidate. Only when it has seen all of them does it make its choice — and that choice is the best one, not the first one.

The trade-off is cost: selection sort is $O(n^2)$ *even when the array is already sorted*, because it still scans the full remaining region each pass. It never gets the "free" early exit that bubble sort enjoys. Deliberateness has a price: you always pay the full cost of looking, even when looking confirms what you already knew.

**🏢 Workplace**
Some decisions deserve the selection sort treatment: **survey everything, then commit to the best option, irrevocably.**

Hiring is the textbook case. You don't hire the first candidate who seems decent — that's bubble sort, acting on the first local friction that resolves. You survey the entire candidate pool. You interview all of them. You compare. Only when you've seen every candidate do you make an offer — and that offer goes to the best person, not the first person who seemed fine. And once you've made the hire, they're in position. Final. You don't "come back and re-sort them later."

The discipline is the **irrevocability**. When selection sort places an element at position `i`, it's done — it will never be revisited. The settled region grows one element at a time, each addition permanent. In hiring, this means: don't keep a "maybe" pile of backup candidates while you're already making decisions. Survey the full field first, pick the best, commit, and move on to the next position with the remaining candidates. The commitment frees you from the cognitive load of revisiting settled decisions — but only if you actually refuse to revisit them.

And the cost: selection sort is $O(n^2)$ even when the team is already good. You still survey the full candidate pool every time, even if the first candidate was great. This is the "you still have to do the full interview round even when your gut says the first one is perfect" tax. It feels wasteful. It's not. The full survey is what gives you the confidence to commit irrevocably. If you didn't survey everything, you'd hedge — and hedging is the opposite of commitment.

**🌍 Life**
Your life's biggest decisions deserve selection sort: **survey everything, choose the best, commit irrevocably, and never look back.**

Where to live. Who to build a life with. What career to commit to. These are not bubble sort problems — you don't fix the first friction you encounter and hope the rest settles. These are selection sort problems: you survey the field — every city, every serious relationship option, every career path that's realistic — and you pick the *best* one, not the first one that seems acceptable.

And here's the life lesson that the algorithm encodes: **once you've placed it, it's final.** The element at position 0 never moves. The decision you made — this city, this person, this career — is settled. You don't keep a "what if I'd chosen differently?" pile. You don't re-survey the field after you've committed. The settled region is settled. The remaining decisions are about the *next* position, using the *remaining* options, not revisiting the ones you've already placed.

The cost: this means living with the knowledge that you surveyed everything available *at that time* — and the world may have new options now that weren't available then. Selection sort doesn't re-scan the already-sorted region. It only looks forward, at what's left. The discipline is: don't re-survey the settled past. Don't reopen the "what if I'd chosen a different city / person / career" question every year. You scanned the full field at the time. You picked the best. It's placed. Move forward with what remains.

And the wisdom: **selection sort never gets a shortcut.** Even if your life is already well-sorted — the right city, the right person, the right career — you still pay the cost of *confirming* it. You don't get to skip the full survey just because things feel right. The full survey is what *earns* you the right to commit irrevocably. Skip it, and you're not committing — you're guessing. Pay the full cost of looking. Then commit. Then don't look back.

**⚠️ Anti-pattern**
*"I'll just pick the first option that seems good enough and adjust later."*
That's bubble sort applied to a selection sort problem — acting on the first acceptable thing instead of surveying the full field and committing to the best. For small decisions (what to eat, which task to do next), bubble sort is fine: act on local friction, fix it, move on. But for irrevocable decisions — where to live, who to commit to, what to build — acting on the first acceptable option is a trap. You're not "staying flexible"; you're refusing to do the work of surveying the field, and the cost of that refusal is choosing worse than you could have. Selection sort says: look at everything, pick the best, commit fully, and accept that the cost of looking is the price of choosing well. There is no shortcut. There is only the full survey or the regret of not doing one.
