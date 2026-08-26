<p align="center">🌐 Language: &nbsp;<a href="README.md"><b>English</b></a> &nbsp;·&nbsp; <a href="README.zh.md">中文</a> &nbsp;·&nbsp; <a href="README.ja.md">日本語</a></p>

<p align="center"><a href="../README.md#-the-catalog">← Back to Catalog</a></p>

---

### 34. Trapping Rain Water

> *Compute how much water is trapped between bars after it rains.*

**🧩 Algorithm**
At any position `i`, the water that can sit there is decided by two things: the tallest bar to the **left** of `i`, and the tallest bar to the **right** of `i`. Water fills up to the **shorter** of those two walls — because the shorter wall is the one that spills over. So:

$$\text{water}[i] = \min(\text{left\_max}[i],\ \text{right\_max}[i]) - \text{height}[i]$$

You precompute `left_max` (running max scanning left→right) and `right_max` (running max scanning right→left), then sum the trapped water at every index.

```python
def trap(height):
    n = len(height)
    if n == 0:
        return 0
    left = [0] * n
    right = [0] * n
    left[0] = height[0]
    for i in range(1, n):
        left[i] = max(left[i - 1], height[i])
    right[-1] = height[-1]
    for i in range(n - 2, -1, -1):
        right[i] = max(right[i + 1], height[i])
    return sum(min(left[i], right[i]) - height[i] for i in range(n))
```

> Time $O(n)$ · Space $O(n)$

The deeper principle: **the water a position holds is decided by its *weaker* side.** Not the taller wall. Not the average. The **minimum** of the two. The taller wall is irrelevant to how much water sits at `i` — you could make it infinitely tall and the trapped water wouldn't change by a drop. Only the shorter wall sets the ceiling. This is the bottleneck principle, but inverted into a question of *holding capacity*: capacity = min(left, right), and the stronger wall contributes nothing beyond the weaker one.

And the structure: **you must see in *both* directions before you know what's held.** The water at `i` depends on the best wall to the left *and* the best wall to the right. A single-direction view — only the left, only the past — tells you nothing about capacity. You need the right max too. To know what a moment can hold, you need to know the highest support on *both* sides of it, not just the side you've already lived.

**🏢 Workplace**
A project's capacity to hold value — revenue, impact, learning — is bounded by its weaker boundary, not its stronger one. If the technical team is world-class (tall left wall) but the go-to-market motion is weak (short right wall), the project holds only what the weak GTM allows. Pouring more engineering into it doesn't raise the water — the GTM ceiling spills it straight out.

The trap: **organizations over-invest in their strength.** The strong side is visible, celebrated, easy to fund. The weak side is invisible, unglamorous, hard to admit. But capacity = min(left, right). The strong side is already above the ceiling; every dollar there is wasted. The weak side *is* the ceiling. Fix the GTM. The engineering was never the bottleneck.

And the structure: **you must assess in both directions.** A project's true capacity needs the best of what's behind it (the team, the tech, the history) *and* the best of what's ahead (the market, the demand, the timing). Looking only at the left — "we have great tech!" — blinds you to the right-wall ceiling. You need both maxima to know what the project can actually hold.

**🌍 Life**
The "water" you hold — well-being, capacity, peace, accumulated joy — is bounded by your *weaker* limit, not your stronger one. If your earning ceiling is sky-high but your health floor is low, you don't hold the sky-high income's worth. You hold only what the health floor permits. The shorter wall is the ceiling on your life.

The trap: **people build the tall wall taller.** More income, more status, more skill — while the short wall (health, rest, relationships) stays where it is. The extra income doesn't raise your held well-being by a drop, because the health wall spills it. You feel it: the raise that bought nothing, the promotion that brought no peace. That's min(left, right) in action — the strong side contributing nothing past the weak one.

And the structure: **you must see both directions of your life.** What you can hold depends on the best support behind you *and* ahead of you. "I have a great past / great skills" (left wall) tells you nothing if the right wall — your future capacity for health, for rest, for connection — is short. To know what your life can hold, you need the maximum on both sides. The weaker one is the ceiling. Raise *that*.

**⚠️ Anti-pattern**
*"To hold more, build the tall wall taller."*
That's raising `left[i]` when `right[i]` is already the minimum. The trapped water is `min(left, right) - height` — increasing the already-taller side changes nothing. The water level doesn't move. You've spent effort on a wall that was never the ceiling. The only move that raises capacity is raising the *shorter* wall. Optimize the constraint, not the strength. The taller wall is a vanity metric; the shorter wall is the truth. Find the minimum. Raise that.
