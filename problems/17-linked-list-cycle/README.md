<p align="center">🌐 Language: &nbsp;<a href="README.md"><b>English</b></a> &nbsp;·&nbsp; <a href="README.zh.md">中文</a> &nbsp;·&nbsp; <a href="README.ja.md">日本語</a></p>

<p align="center"><a href="../README.md#-the-catalog">← Back to Catalog</a></p>

---

### 17. Linked List Cycle

> *Determine whether a linked list has a cycle — without storing every visited node.*

**🧩 Algorithm**
The naive approach: record every node you visit in a hash set. If you see the same node twice, there's a cycle. It works, it's $O(n)$ time — but it costs $O(n)$ space, because you're holding the entire history in memory.

Floyd's approach: drop two pointers into the list, one moving at 1 step per turn, the other at 2. If there's no cycle, the fast one simply exits the list first. If there *is* a cycle, both pointers enter it — and now it's a pursuit problem on a finite track. The fast pointer gains 1 step per round. On a finite track of $m$ positions, gaining 1 per round guarantees it catches the slow one in at most $m$ rounds. Not "might" — *must*.

```python
class Solution:
    def hasCycle(self, head) -> bool:
        slow = fast = head

        while fast and fast.next:
            slow = slow.next
            fast = fast.next.next

            if slow is fast:
                return True

        return False
```

> Time $O(n)$ · Space $O(1)$

The key insight: **you don't need to remember the past to detect a cycle.** Two things moving at different speeds on a closed track *must* meet — not because they're lucky, but because the relative speed is constant and the track is finite. The memory of "have I been here before?" is replaced by the physics of "if two things chase on a loop, the faster one catches up."

The hash set approach asks: *"Did I keep records?"* Floyd asks: *"Do the dynamics guarantee a collision?"* One needs memory; the other needs only math.

**🏢 Workplace**
You know the pattern: every Monday you're fixing what broke on Friday. The same outage, the same conflict, the same miscommunication. You're not solving problems — you're walking a cycle.

The naive approach is to keep a log of every issue you've encountered, and check each new one against the history. That's a hash set — $O(n)$ mental space, and you're constantly maintaining it. It works, but it's exhausting: you're carrying the entire incident archive in your head.

Floyd's approach: **stop recording. Start watching the dynamics.** If the same two teams keep colliding, if the same escalation path keeps recurring, if the same bottleneck reappears each sprint — you don't need a comprehensive audit to prove it's a cycle. You need two things moving at different speeds: the fast one (the person who escalates quickly) and the slow one (the process that grinds slowly). If they keep meeting at the same point, you have your proof.

The cycle isn't detected by exhaustive memory. It's detected by the *shape* of the motion — repetition without progress. Two velocities on a finite track, meeting again and again. That's a cycle, and the fix isn't to log it harder. The fix is to **break the edge** — change the structure so the loop no longer exists.

**🌍 Life**
The hash-set approach to life: journal every conflict, log every argument, track every recurring pattern. Build a comprehensive record of "things that have happened before" so you can spot when they happen again. It works. It also means you're carrying the entire emotional history of every relationship in your head — $O(n)$ space, forever.

Floyd's approach: **you don't need to remember every argument to detect a cycle. You need to watch the dynamics.**

Here's the insight: **repetition doesn't require memory to prove — it requires different speeds.** Put two things in motion: your reaction (fast) and the underlying pattern (slow). If your reaction keeps arriving at the same place as the pattern — the same fight, the same resentment, the same retreat — you're in a cycle. Not because you catalogued the history, but because the dynamics make it inevitable.

And here's the deeper truth: **in a cycle, moving faster doesn't help.** The fast pointer doesn't escape the cycle by being fast — it just laps the slow one. Working harder inside the cycle, reacting faster, pushing more intensity — none of it breaks the loop. The fast pointer meets the slow one *because* the track is closed, not because it's slow.

The only way out is to **break the edge** — change the structure so the loop no longer exists. That might mean a new conversation, a new boundary, a new process, or walking away from the track entirely. Inside the cycle, every step forward is another step around the loop. The exit isn't a step — it's a structural change.

**⚠️ Anti-pattern**
*"I'll just keep better records next time."*
That's the hash-set approach: $O(n)$ memory to detect cycles by brute recall. It works, but it's a tax you pay forever — you're maintaining a growing archive of every conflict, every pattern, every "this has happened before." Floyd tells you that you don't need the archive. You need the dynamics. If two things in your life keep meeting at the same point, that *is* the proof — no log required. Spending energy on better record-keeping instead of breaking the cycle is the most expensive form of denial: it feels like diligence, but it's just faster walking on a closed track.
