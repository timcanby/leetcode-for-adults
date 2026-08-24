<p align="center">🌐 Language: &nbsp;<a href="README.md"><b>English</b></a> &nbsp;·&nbsp; <a href="README.zh.md">中文</a> &nbsp;·&nbsp; <a href="README.ja.md">日本語</a></p>

<p align="center"><a href="../README.md#-the-catalog">← Back to Catalog</a></p>

---

### 19. Sliding Window

> *Find the longest substring without repeating characters (#3). Find the shortest substring that covers all required characters (#76).*

**🧩 Algorithm**
A sliding window is a continuous interval `[left, right]` that moves across the data. The two pointers aren't opposite — they're **cooperative**: `right` expands, `left` repairs. Right pushes forward into new territory. Left contracts when the window breaks the rules.

There are two flavors, and the difference is the whole insight:

**Longest valid window (#3):** Expand `right` until the window becomes illegal (a duplicate appears). Then shrink `left` until it's legal again. Update the answer *after* repairing. The mantra: **expand greedily, shrink when broken.**

```python
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        seen = set()
        left = 0
        ans = 0

        for right in range(len(s)):
            while s[right] in seen:
                seen.remove(s[left])
                left += 1
            seen.add(s[right])
            ans = max(ans, right - left + 1)

        return ans
```

**Shortest satisfying window (#76):** Expand `right` until the window *satisfies* the requirements (all characters covered). Then shrink `left` greedily — while it's still valid — to find the tightest fit. Update the answer *during* the shrink. The mantra: **expand until satisfied, then squeeze.**

```python
from collections import Counter, defaultdict

class Solution:
    def minWindow(self, s: str, t: str) -> str:
        need = Counter(t)
        window = defaultdict(int)
        left = 0
        valid = 0
        start = 0
        min_len = float("inf")

        for right, ch in enumerate(s):
            if ch in need:
                window[ch] += 1
                if window[ch] == need[ch]:
                    valid += 1

            while valid == len(need):
                if right - left + 1 < min_len:
                    min_len = right - left + 1
                    start = left

                if s[left] in need:
                    if window[s[left]] == need[s[left]]:
                        valid -= 1
                    window[s[left]] -= 1
                left += 1

        return s[start:start + min_len] if min_len != float("inf") else ""
```

> Time $O(n)$ — `left` and `right` each walk rightward at most $n$ steps · Space $O(k)$ where $k$ = character set size

The deeper principle: **right expands into the unknown; left repairs the known.** Right is the explorer — it always moves forward, never looking back, always adding new territory. Left is the fixer — it only acts when something breaks, and it only removes, never adds. They cooperate without coordination: right doesn't wait for left, left doesn't anticipate right. The window's validity is the invariant that connects them — right may break it, left must restore it, and the answer is only safe to update when the invariant holds.

**🏢 Workplace**
A project is a sliding window. `right` is your growing scope — new features, new requirements, new stakeholders arriving each sprint. `left` is your cleanup — deprecating old code, removing stale documentation, sunsetting legacy systems.

The two flavors map directly:

**Longest window (#3):** You want maximum scope — more features, more coverage, more delivered value. Expand aggressively. But when a new addition creates a conflict (two teams own the same domain, two features overlap), *shrink immediately* until the conflict is gone. Don't keep expanding while broken. Fix the overlap, then keep going. The answer — your maximum productive scope — is only valid when the window is clean.

**Shortest window (#76):** You want minimum cost — the smallest team, the tightest budget, the leanest process that *still covers everything required*. Expand until all requirements are met, then *squeeze* — while everything is still covered, trim left: remove redundant meetings, cut overlapping responsibilities, drop the third approval that the first two already cover. The answer — your minimum viable process — is found *during* the squeeze, not after the expand.

And here's the discipline: **right never looks back.** Right doesn't revisit territory it already scanned. Left doesn't either. Both pointers walk forward only. In practice: once you've added a stakeholder, a feature, a process step, you don't "undo" it — you let left remove what's stale, and right keeps pushing into what's new. No backtracking. The window slides forward, one direction, never reversing.

**🌍 Life**
Your attention is a sliding window. `right` is the new thing — the new interest, the new obligation, the new person who just entered your life. `left` is what you let go — the old commitment that no longer serves, the stale habit that no longer fits, the energy drain you've been tolerating.

**Longest window (#3):** You want the longest stretch of focused, undistracted flow. Expand `right` — let new experiences in, take on new challenges. But when a conflict appears — a duplicate commitment, a repeating obligation, something that breaks your flow — *shrink `left` immediately*. Drop the old thing that's creating the collision. Don't tolerate duplicates in your life. The longest stretch of unbroken focus comes from expanding aggressively and repairing instantly.

**Shortest window (#76):** You want the leanest life that still covers everything that matters. Expand until all your needs are met — health, relationships, work, meaning. Then *squeeze* — while everything is still covered, trim the excess: the social obligation that no longer adds value, the hobby you maintain out of guilt, the commitment that overlaps with three others. The answer — your minimum viable life — isn't found by expanding forever. It's found by expanding until satisfied, then squeezing until tight.

And the universal principle: **right never looks back.** You don't re-enter territory you've already passed. You don't "go back" to an old version of yourself. `right` pushes forward into what's new, and `left` drops what's stale. The window of your life slides in one direction — forward — and the art is knowing when to expand and when to contract, not when to reverse.

The two mantras, for life:
- **Longest flow:** expand until it breaks, then shrink until it's fixed. Don't tolerate duplicates.
- **Leanest life:** expand until it's enough, then squeeze until it's tight. Don't carry redundancy.

**⚠️ Anti-pattern**
*"I'll just add one more thing to the window — it's probably fine."*
That's expanding `right` without ever shrinking `left`. The window grows until it breaks — and then keeps growing, because you never repair. The longest-window problems require you to shrink when broken; the shortest-window problems require you to squeeze when satisfied. If you only expand and never contract, you get neither the longest valid window nor the shortest satisfying one — you get an overflowing, bloated, invalid window that satisfies nothing and maximizes nothing. The discipline isn't in the expansion; it's in the contraction. Right is easy — it's just "add more." Left is the art — it's knowing what to drop and when.
