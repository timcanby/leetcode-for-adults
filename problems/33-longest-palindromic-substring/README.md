<p align="center">🌐 Language: &nbsp;<a href="README.md"><b>English</b></a> &nbsp;·&nbsp; <a href="README.zh.md">中文</a> &nbsp;·&nbsp; <a href="README.ja.md">日本語</a></p>

<p align="center"><a href="../README.md#-the-catalog">← Back to Catalog</a></p>

---

### 33. Longest Palindromic Substring

> *Find the longest substring that reads the same forward and backward.*

**🧩 Algorithm**
A brute force check of every substring is $O(n^3)$ — too slow. The DP insight: you don't prove a big substring is a palindrome from scratch. You prove it by checking two cheap things:

1. Do the two **ends** match? (`s[i] == s[j]`)
2. Is everything **between** them already a palindrome? (`dp[i+1][j-1]`)

If both are true, `s[i..j]` is a palindrome. The "inside is already solved" part is the recursion — you've already computed every shorter substring, so the answer for the middle is sitting there waiting.

```python
def longestPalindrome(s):
    n = len(s)
    dp = [[False] * n for _ in range(n)]
    start = 0
    best = 1
    for i in range(n - 1, -1, -1):
        for j in range(i, n):
            if s[i] == s[j] and (j - i <= 2 or dp[i+1][j-1]):
                dp[i][j] = True
                if j - i + 1 > best:
                    start = i
                    best = j - i + 1
    return s[start:start + best]
```

> Time $O(n^2)$ · Space $O(n^2)$

The deeper principle: **a long palindrome is just a short palindrome wearing matching ends.** You don't build the big symmetric thing directly. You build the small ones first, then ask: "if the inside is already whole, can I just wrap it in two matching characters?" That's the whole method. The inside does the hard work; the ends are a $O(1)$ check.

And the loop order matters — `i` goes **backwards** (`n-1 → 0`), `j` goes forwards from `i`. You can't fill `dp[i][j]` until `dp[i+1][j-1]` exists, so you must solve the *smaller* problems (shorter substrings, higher `i`) before the bigger ones. **You can't certify symmetry at a large scale until you've certified it at every smaller scale.** The order isn't cosmetic — it *is* the dependency.

**🏢 Workplace**
A "palindrome" in an organization is a decision or narrative that holds coherently from *both* directions — from the top-down story and the bottom-up reality. When leadership says one thing and the front line lives another, the substring isn't a palindrome. It's broken.

The DP lesson: **don't try to make the whole org coherent at once.** Build coherence locally first. Make the small teams palindromic — their stated purpose matches their actual behavior (`s[i] == s[j]`), and the team *between* them is already healthy (`dp[i+1][j-1]`). Once the inside is whole, the larger org only needs its two ends to match. The big palindrome is just small palindromes with matching boundaries — not a top-down rewrite.

And the loop order: **fix the inner dysfunction before asserting the outer narrative.** A reorg that declares "we're aligned now" while the middle teams are stillbroken is `dp[i][j] = False` — the `dp[i+1][j-1]` check fails. You can't certify org-wide symmetry until every smaller unit is already coherent. Start from the inside. Work outward. The ends are cheap once the middle holds.

**🌍 Life**
A life that reads the same forward and backward is a life with **integrity** — your stated values match your actual behavior, from every angle. The longest such substring is the longest stretch of your life where who you *say* you are and who you *are* line up.

The DP lesson: **you don't achieve integrity in one grand gesture.** You achieve it locally. Each small choice is a palindrome check: do my words match my action at this edge (`s[i] == s[j]`), and is the stretch of life between them already coherent (`dp[i+1][j-1]`)? If both hold, that segment is whole. The long unbroken stretch of integrity isn't built by a big resolution — it's built by thousands of small palindromes, each wrapping a previously-whole interior in two matching ends.

And the loop order — the most important part: **you build integrity from the inside out, small first.** You can't certify that your *whole life* is coherent (`dp[0][n-1]`) until the smaller stretches are already whole. The person who announces "I've completely changed" while the interior is still contradictory is checking `dp[i][j]` before `dp[i+1][j-1]` exists — it returns false. Change the inside first. Let the ends follow. The longest palindrome of a life is earned one small coherent segment at a time.

**⚠️ Anti-pattern**
*"I'll just rewrite my whole life / org to be coherent — start over from the outside."*
That's computing `dp[i][j]` before `dp[i+1][j-1]` exists. You declare the big palindrome — "new me," "aligned team," "transformed culture" — but the inside is still broken, so the check fails. The ends might even match (you *say* the right things now), but without a coherent middle, the whole thing is `False`. The DP method refuses this: it only extends symmetry over a substring whose interior is *already* a palindrome. You don't get a long palindrome by forcing the outer characters to match. You get it by making the inside whole, then wrapping it. Start small. Make the inside true. Let the length grow. Extending coherence outward is cheap — *earning* it inward is the work.
