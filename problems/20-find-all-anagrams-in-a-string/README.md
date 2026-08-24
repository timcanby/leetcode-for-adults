<p align="center">🌐 Language: &nbsp;<a href="README.md"><b>English</b></a> &nbsp;·&nbsp; <a href="README.zh.md">中文</a> &nbsp;·&nbsp; <a href="README.ja.md">日本語</a></p>

<p align="center"><a href="../README.md#-the-catalog">← Back to Catalog</a></p>

---

### 20. Find All Anagrams in a String

> *Find all starting indices in `s` where a substring is an anagram of `p`.*

**🧩 Algorithm**
An anagram means: same characters, same counts, different order. So you don't need to match *content* — you need to match *frequency*. The window isn't expanding or shrinking to find an optimum; it's **fixed-size**, sliding across `s` at exactly `len(p)` wide.

Each step: `right` advances by one, adding a character. If the window exceeds `len(p)`, `left` advances by one, removing the oldest character. The window is always exactly `len(p)` wide — a fixed frame sliding across the string.

At each position, compare the window's frequency count to `p`'s. If they match — same characters, same counts — that's an anagram. Record the starting index.

```python
from collections import Counter

class Solution:
    def findAnagrams(self, s: str, p: str) -> list[int]:
        need = Counter(p)
        window = Counter()
        ans = []
        left = 0

        for right, ch in enumerate(s):
            window[ch] += 1

            if right - left + 1 > len(p):
                window[s[left]] -= 1
                if window[s[left]] == 0:
                    del window[s[left]]
                left += 1

            if right - left + 1 == len(p) and window == need:
                ans.append(left)

        return ans
```

> Time $O(n \cdot k)$ where $k$ = character set size · Space $O(k)$

The deeper principle: **when the frame size is fixed, the only question is what's inside the frame right now.** You're not optimizing length — you're checking identity at each position. The window doesn't flex; it slides. And at each stop, it asks one question: *"does what I'm looking at right now match what I'm looking for?"* Not "could it match if I adjusted?" — just "does it match, yes or no?"

**🏢 Workplace**
Some problems aren't about optimization — they're about **pattern matching at fixed positions**. You have a template: a job spec, a project checklist, a team composition requirement. And you have a stream of candidates — resumes, projects, team configs — flowing past you. Your job isn't to find the longest or shortest fit. It's to slide a fixed-size frame across the stream and ask, at each position: *"does this match the spec?"*

The mistake is trying to flex the frame. "Well, this candidate has 4 out of 5 required skills, so maybe I should widen the requirement..." — no. The spec is the spec. The window is `len(p)` wide. Slide it, check it, move on. If the current position doesn't match, don't negotiate the frame — advance to the next position.

The anagram insight is sharper: **content match ≠ order match.** The right candidate might not list skills in the "right order" — their resume might look different from what you expected, the project might not follow your preferred sequence — but if the *set* of capabilities matches, it's an anagram. Don't reject a match because the order differs. The frequency count is what matters, not the arrangement.

**🌍 Life**
Most of life's sliding windows are variable-size — you flex the frame to find the longest or shortest fit. But some situations give you a **fixed frame**: a job that requires exactly 3 years of experience, a lease that's exactly 12 months, a budget that's exactly $5,000, a deadline that's exactly 2 weeks. The frame doesn't flex. You slide it across your options and ask at each position: *"does what's inside this frame right now match what I need?"*

Here's the insight: **stop trying to resize the frame when the frame is fixed.** When the constraint is rigid — the budget is $5,000, the timeline is 2 weeks, the team is 3 people — don't waste energy negotiating the constraint. Slide across your options, check each one against the spec, and collect every match. Some positions will match; most won't. That's fine. The goal isn't to make every position match; it's to **find every position that does**.

And the anagram wisdom: **the right life might not look like the life you pictured — but if the components match, it's a fit.** You imagined: city job, downtown apartment, 2 kids, dog. What you found: remote job, suburban house, 2 kids, cat. Different order, different arrangement — but the frequency count matches. Same characters, same counts, different sequence. Don't reject it because it doesn't match the order you expected. It's an anagram of the life you wanted.

**⚠️ Anti-pattern**
*"Let me adjust the window size to see if I can find a match."*
That's treating a fixed-window problem like a variable-window problem. The window is `len(p)` — it doesn't flex. If the current position doesn't match, the answer isn't to resize the frame; it's to slide forward. Resizing a fixed frame to force a match is like rewriting the job spec to fit the candidate: you'll find a "match," but it won't be the match you were looking for. The spec defines the frame. Don't let the data redefine the spec. Slide, check, record matches, move on — the frame stays fixed, and every anagram you find is real.
