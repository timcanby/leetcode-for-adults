<p align="center">🌐 Language: &nbsp;<a href="README.md"><b>English</b></a> &nbsp;·&nbsp; <a href="README.zh.md">中文</a> &nbsp;·&nbsp; <a href="README.ja.md">日本語</a></p>

<p align="center"><a href="../README.md#-the-catalog">← Back to Catalog</a></p>

---

### 2. Container With Most Water

> *Two lines form a container. Maximize the area between them.*

**🧩 Algorithm**
The area between any two lines is `(distance) × min(height[left], height[right])`. Two forces compete: wider is better, but the shorter line caps the water level.

Start from the widest pair. The width can only shrink from here. So the only question is: **which side to move?** Move the taller side and the width drops while the effective height stays capped — the area can only get worse. Move the shorter side and you lose width but *might* find a taller line. That's the only hope.

This isn't a guess. It's a proof: every combination that keeps the shorter line is already provably worse than what you have. You eliminate an entire row of the search space per step, collapsing $O(n^2)$ into $O(n)$.

```python
class Solution:
    def maxArea(self, height: list[int]) -> int:
        left, right = 0, len(height) - 1
        ans = 0

        while left < right:
            ans = max(ans, (right - left) * min(height[left], height[right]))

            if height[left] < height[right]:
                left += 1
            else:
                right -= 1

        return ans
```

> Time $O(n)$ · Space $O(1)$

**🏢 Workplace**
When a project stalls, don't keep polishing the part that's already good enough. Find the bottleneck — the person, the permission, the dependency — and address that. Everything else is decorative effort.

**🪞 Power Struggle**
If one person's authority gates whether something ships, everyone else's hustle is capped by that gate. You can double the team's speed, hire ten more engineers, and the output won't change — because the short wall is the sign-off, not the sprint velocity. The real problem is the permission structure, not the execution speed of the people waiting.

**🌍 Life**
You might have plenty of time in the day, but if your energy is low, that's the short wall. Your daily output is bounded by energy, not hours. Optimizing your calendar when you're exhausted is moving the wrong wall — you're shrinking the width without raising the bottleneck.

Here's the deeper personal truth: **the short wall decides your fate.** You can be brilliant in ten areas and still be defined by the one you're worst at — the one that caps your relationships, your career, or your health. The instinct to "keep adding to your strengths" is moving the tall wall. It feels productive. It isn't.

And if you manage a team: **a team's output is bounded by its weakest member, not its strongest.** No amount of star-player heroics compensates for the person who blocks the pipeline every sprint. You can celebrate the tall wall all you want — the water still spills over the short one. The only fix is to raise the short wall: train, pair, mentor, or restructure. Ignoring the bottleneck while cheering the peak is the most common — and most expensive — management mistake.

**⚠️ Anti-pattern**
*"Optimize whatever side looks most promising."*
Frequently wrong. You should optimize the variable that currently constrains the result. The promising-looking side is often the side that's already doing fine — it's the tall wall, and moving it changes nothing. The uncomfortable, unglamorous side — the one you'd rather not look at — is the short wall. That's the one that decides everything.
