<p align="center">🌐 Language: &nbsp;<a href="README.md"><b>English</b></a> &nbsp;·&nbsp; <a href="README.zh.md">中文</a> &nbsp;·&nbsp; <a href="README.ja.md">日本語</a></p>

<p align="center"><a href="../README.md#-the-catalog">← Back to Catalog</a></p>

---

### 21. Longest Repeating Character Replacement

> *Find the longest substring you can make all-same-letter by replacing at most `k` characters.*

**🧩 Algorithm**
You're not looking for a window that's *already* valid. You're looking for a window you can *make* valid — where "valid" means "all one letter, with at most `k` replacements."

The key insight: a window `[left, right]` can be made all-same-letter if and only if `(window length) - (frequency of the most common character in the window) ≤ k`. The "waste" is everything that isn't the dominant letter. If the waste fits within your `k` replacement budget, the window is feasible.

So: expand `right` adding characters. Track `max_freq` — the count of the most frequent character in the current window. When `(right - left + 1) - max_freq > k`, the window has too much waste. Shrink `left` until the waste fits back inside `k`.

```python
from collections import defaultdict

class Solution:
    def characterReplacement(self, s: str, k: int) -> int:
        count = defaultdict(int)
        left = 0
        max_freq = 0
        ans = 0

        for right, ch in enumerate(s):
            count[ch] += 1
            max_freq = max(max_freq, count[ch])

            while (right - left + 1) - max_freq > k:
                count[s[left]] -= 1
                left += 1

            ans = max(ans, right - left + 1)

        return ans
```

> Time $O(n)$ · Space $O(k)$ where $k$ = character set size

The deeper principle: **you don't need everything to be the same — you need the *differences* to fit within your budget.** The dominant character is what you're betting on. `max_freq` is your anchor — the thing that's already working. Everything else is noise. The question isn't "is this window perfect?" The question is "is the noise small enough that I can absorb it?"

And here's the subtle beauty: **`max_freq` only ever increases.** You don't shrink it when `left` moves, because you don't need to. A higher `max_freq` means a stricter constraint — but you're looking for the *longest* window, so a stricter constraint can only make you *more confident* in your current answer, never less. The window never needs to be smaller than what you've already found. `ans` only grows. `max_freq` only grows. The algorithm is monotonic — it moves forward and never retreats.

**🏢 Workplace**
You don't need a perfect team. You need a team where the **noise fits within your budget**.

Your `max_freq` is your strongest contributor — the person who carries the core load, the skill that anchors the team, the process that already works. Everything else is variance: the junior who needs guidance, the tool that occasionally breaks, the stakeholder who needs extra communication.

`k` is your management budget: your coaching capacity, your technical-debt tolerance, your patience for friction. The window — your team's productive scope — is valid when `(total scope) - (what the anchor already handles) ≤ k`. When the noise exceeds your budget, you don't fire the anchor. You shrink the scope — drop the side project, reduce the meeting load, narrow the sprint — until the variance fits within what you can absorb.

And the monotonic insight: **your strongest contributor's best streak only goes up.** You don't recalibrate `max_freq` downward when things get messy. You remember the peak — the time your best person carried a whole sprint — and you use that as your anchor. A lower anchor would make you shrink prematurely. The memory of the peak keeps you expanding.

**🌍 Life**
You don't need a perfect life. You need a life where the **differences from what you want fit within your tolerance**.

Your `max_freq` is your dominant thread — the person, the habit, the value, the activity that occupies the most space in your life and already works. Everything else is variance: the days you don't exercise, the meals that aren't healthy, the conversations that don't go deep. `k` is your self-compassion budget — the slack you allow yourself, the imperfections you tolerate, the "good enough" you accept.

The window of your life is valid when `(everything you're doing) - (what's already aligned) ≤ k`. When the noise — the misaligned habits, the energy drains, the commitments that don't match your core — exceeds your tolerance, you don't abandon your anchor. You shrink the window: drop the misaligned commitment, let go of the energy drain, narrow the scope — until the variance fits within the life you can absorb.

And here's the liberating insight: **`max_freq` only grows.** You don't downgrade your best self when you have a bad week. You remember your peak — the version of you that ran every morning, that read every night, that showed up for every friend — and you use that as your anchor. A lower anchor would shrink your window prematurely. The memory of the peak keeps you expanding, keeps you reaching, keeps the window growing.

The longest valid life isn't the one with zero noise. It's the one where the noise fits within `k` — where the differences between what you are and what you want are small enough to absorb. Don't demand perfection. Demand that the variance fits the budget. Then expand.

**⚠️ Anti-pattern**
*"I need to fix everything before I can expand."*
That's setting `k = 0` — zero tolerance for noise, zero budget for variance. The window shrinks to `max_freq` itself — only the dominant character, nothing else. No project, no life, no team is a single letter repeated. The whole point of `k` is that **some noise is absorbable** — the budget exists to be spent, not hoarded. If you refuse to expand until everything is aligned, you never expand at all. The longest window isn't the one with zero replacements; it's the one where the replacements fit. Spend the budget. Expand. Shrink only when the noise genuinely overflows.
