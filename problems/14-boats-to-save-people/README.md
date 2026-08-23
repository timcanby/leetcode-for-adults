<p align="center">🌐 Language: &nbsp;<a href="README.md"><b>English</b></a> &nbsp;·&nbsp; <a href="README.zh.md">中文</a> &nbsp;·&nbsp; <a href="README.ja.md">日本語</a></p>

<p align="center"><a href="../README.md#-the-catalog">← Back to Catalog</a></p>

---

### 14. Boats to Save People

> *Each boat carries at most two people and cannot exceed a weight limit. Find the minimum number of boats.*

**🧩 Algorithm**
Sort the weights. Place one pointer at the lightest, one at the heaviest. Each round, the heaviest person **must** get on a boat — they always take a slot, no matter what. The only question is: can the lightest person squeeze in with them?

- If `lightest + heaviest ≤ limit` → both board together. `left += 1, right -= 1, boats += 1`.
- If `lightest + heaviest > limit` → the heaviest can't pair with *anyone* (the lightest was their best shot). Heaviest goes alone. `right -= 1, boats += 1`.

The heaviest is the "must-handle-now" protagonist. The lightest is just checking: *"can I tag along?"* Every round eliminates at least one endpoint, collapsing the decision tree from exponential to linear.

```python
class Solution:
    def numRescueBoats(self, people: list[int], limit: int) -> int:
        people.sort()

        left, right = 0, len(people) - 1
        boats = 0

        while left <= right:
            if people[left] + people[right] <= limit:
                left += 1
            right -= 1
            boats += 1

        return boats
```

> Time $O(n \log n)$ (sort dominates) · Space $O(1)$

The deeper principle: **handle the hardest constraint first.** The heaviest person is the bottleneck — they're the hardest to pair, the most likely to need a boat alone, and the one who blocks the most options. By dealing with them immediately, you simplify everything downstream. The lightest person — the easy case — becomes a flexible filler, slotted in wherever capacity allows.

**🏢 Workplace**
When you face a resource allocation problem — budgets, headcount, deadlines — your instinct might be to handle the easy tasks first, get momentum going, feel productive. **Don't.**

The hard constraint is the heaviest person in the boat. It's the project that needs three approvals, the client with the strictest deadline, the dependency that blocks everything else. Deal with it first. It *must* be handled — there's no scenario where it goes away. The only question is whether something easy can ride along.

Once the bottleneck is resolved, the remaining tasks — the light ones — are trivially flexible. They slot into whatever capacity is left. But if you spend the easy ones first, you might waste the only resource that could have paired with the bottleneck, leaving the hard problem stranded and alone.

**🌍 Life**
**Face the constraint first, then solve the bottleneck. After that, easy things become flexibly plannable — rather than using up flexibility before the constraint is addressed.**

Here's the instinct: clear the easy stuff first. Knock out the small tasks, get the inbox to zero, feel the momentum. It feels responsible. It isn't.

The hard problem — the heaviest person — is the one that actually decides how many boats you need. No amount of easy-task clearing changes that. What *does* change is whether the easy tasks are still available as flexible fillers once the hard problem is handled. If you've already "used up" your lightest people — your spare energy, your free afternoon, your goodwill buffer — on easy wins, you've lost the only resource that might have paired with the heavy constraint to save a boat.

The mature move: sort your constraints by severity. Handle the heaviest first. Then let the light, flexible tasks fill whatever capacity remains. Not only does this minimize total boats — it also means the easy part is genuinely easy, because the shadow of the unsolved hard problem isn't hanging over it.

**⚠️ Anti-pattern**
*"Let me clear the easy tasks first to build momentum."*
That's pairing the two lightest people together. It feels productive — you see boats filling up, tasks getting done. But you've just wasted the lightest person — the only one who might have paired with the heaviest — on a pairing that could have been handled later. Now the heaviest is alone, and you're one boat over. The easy tasks were never the problem; they were the *solution* — the flexible filler that makes the hard problem solvable in fewer boats. Use them last, not first.
