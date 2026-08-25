<p align="center">🌐 Language: &nbsp;<a href="README.md"><b>English</b></a> &nbsp;·&nbsp; <a href="README.zh.md">中文</a> &nbsp;·&nbsp; <a href="README.ja.md">日本語</a></p>

<p align="center"><a href="../README.md#-the-catalog">← Back to Catalog</a></p>

---

### 32. Majority Element

> *Find the element that appears more than ⌊n/2⌋ times. You're guaranteed one exists.*

**🧩 Algorithm**
The naive approach: count every element's frequency in a hash map, then return the one with the highest count. $O(n)$ time, $O(n)$ space. It works. It's also doing more than you need.

Boyer-Moore does something stranger. It never counts. It **cancels**. Walk through the array holding a `candidate` and a `count`. When `count` hits zero, adopt the current element as the new candidate. When the current element matches the candidate, `count += 1`. When it doesn't, `count -= 1`. At the end, the candidate *is* the majority.

Why does this work? Because the majority appears more than half the time. Every time a non-majority element cancels a majority element, it also gets canceled — one-for-one. But the majority has *spares*. It has more than $n/2$ copies. So even after every cancellation pair is removed, the majority survives. It's not that the algorithm *finds* the majority — it's that the majority **cannot be canceled to zero**, because there are more of it than of everything else combined.

```python
class Solution:
    def majorityElement(self, nums: list[int]) -> int:
        candidate = None
        count = 0

        for x in nums:
            if count == 0:
                candidate = x

            count += 1 if x == candidate else -1

        return candidate
```

> Time $O(n)$ · Space $O(1)$

The deeper principle: **you don't find the majority by counting — you find it by canceling.** The hash map approach asks: "how many of each?" The cancellation approach asks: "what survives when opposites annihilate?" The majority is the element that *cannot be fully canceled* — not because it's the best, or the loudest, or the most visible, but because there's *more of it than of everything else put together*. It's not a popularity contest. It's a war of attrition, and the side with reserves wins.

And the guarantee is the hidden premise: **this only works if a majority exists.** If no element appears more than $n/2$ times, the algorithm returns *something* — but it's meaningless. The survivor of the cancellation isn't the "winner"; it's just the last one standing in a battle where nobody had the reserves. The algorithm doesn't check. It trusts the precondition. If the precondition is violated, the answer is garbage. The correctness of the method depends on the truth of the assumption.

**🏢 Workplace**
When you're trying to find the dominant opinion in a room, you don't need a poll. You need a **cancellation**. Pair each voice against its opposite. "We should ship" vs. "we should wait." "The feature is ready" vs. "it's not ready." Each pair cancels. What's left standing after all the pairs have annihilated — that's the true majority. Not because it's the smartest opinion, but because more than half the room holds it, and opinions that cancel against it also cancel *themselves*.

The Boyer-Moore wisdom: **you don't count votes — you cancel pairs.** The meeting that feels chaotic, with everyone shouting a different opinion — you don't need to tally every voice. You walk the room, and each time someone disagrees with the current leading opinion, the count drops. Each time someone agrees, it rises. When it hits zero, you switch candidates. At the end, whoever's left standing is the majority — the opinion that couldn't be canceled because more than half the room holds it.

And the guarantee — the trap: **this only works if a majority exists.** If the room is split 40/35/25 — no majority — the algorithm returns *someone*, but it's meaningless. The last one standing isn't the "consensus"; it's just the last survivor of a war nobody won. The Boyer-Moore meeting only produces a real answer when the room has a true majority. If it doesn't, you don't have a decision — you have a *false consensus*, and acting on it is worse than admitting the room is divided. The precondition — "a majority exists" — isn't a technicality. It's the *entire foundation*. Check it before you trust the result.

**🌍 Life**
The dominant force in your life — the habit that shapes more than half your days, the value that drives more than half your decisions, the relationship that occupies more than half your heart — isn't found by counting. It's found by **cancellation**.

Walk through your life. Each day that aligns with the dominant pattern adds to the count. Each day that contradicts it subtracts. When the count hits zero — when enough contradictions have piled up to cancel out the pattern — you switch candidates. You adopt a new dominant habit, a new primary value, a new central relationship. But the *true* majority — the force that's more than half of you — **cannot be fully canceled**. It has reserves. It survives every contradiction because there's more of it than of everything else combined.

The Boyer-Moore approach to self-knowledge: **you don't find your core by journaling every thought — you find it by canceling the noise.** Every day that's "not really me" cancels a day that is. Every habit that contradicts my core cancels a habit that expresses it. But the core — the thing that's more than half of who I am — survives. Not because it's the best or the loudest, but because it has reserves. There's more of it than of everything else put together. It's not a preference. It's a majority.

And the guarantee — the life trap: **if no single force is more than half of you, the result is meaningless.** If you're split — 40% career, 35% family, 25% self — there's no majority, and the "dominant force" the algorithm produces is a phantom. You don't have a core. You have a divided self, and the "answer" is just the last fragment standing after a war of attrition that nobody won. The precondition for self-knowledge is: **is there a majority?** Is there one force — one value, one person, one purpose — that's more than half of you? If yes, cancellation will find it. If no, the algorithm returns garbage, and you need to *build* a majority — not *find* one. The divided life doesn't need Boyer-Moore. It needs a *commitment* — the act of choosing something until it becomes more than half.

**⚠️ Anti-pattern**
*"I'll just count everything to find the most common element."*
That's the hash map — $O(n)$ space, $O(n)$ time — and it works even without the majority guarantee. But it's doing more work than the problem requires. You don't need to know *how many* of each. You need to know *what survives*. The cancellation approach costs $O(1)$ space — no hash map, no tally, no memory of the past — because the majority's survival is *guaranteed by mathematics*, not by record-keeping. The hash map answers "what's the most frequent?" The cancellation answers "what can't be eliminated?" — and the second question is deeper, because it reveals that the majority isn't just the most common thing. It's the *structurally inevitable* thing. The thing that survives not because it's popular, but because it's *uncancelable*. That's the difference between counting votes and fighting a war of attrition — and the difference between knowing your frequencies and knowing your *core*.
