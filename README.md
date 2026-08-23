<!-- Repository Banner -->
<p align="center">
  <img src="assets/banner.png" alt="LeetCode for Adults — Algorithms, office politics, and other things nobody warned you about." width="100%">
</p>

<h1 align="center">LeetCode for Adults</h1>

<p align="center">
  <strong>Algorithms, office politics, and other things nobody warned you about.</strong>
</p>

<p align="center">
  <a href="#-what-is-this"><b>What is this?</b></a> &nbsp;·&nbsp;
  <a href="#-the-template"><b>The Template</b></a> &nbsp;·&nbsp;
  <a href="#-how-to-add-a-new-entry"><b>Add an Entry</b></a> &nbsp;·&nbsp;
  <a href="#-the-catalog"><b>The Catalog</b></a> &nbsp;·&nbsp;
  <a href="#-license"><b>License</b></a>
</p>

---

## 🧠 What is this?

**LeetCode is not an algorithm problem set — it's a survival simulator for adults.**

Every classic problem encodes a pattern that shows up long after the interview ends: in how you manage a team, how you negotiate with a bottleneck, how you triage a week of meetings, and how you decide what to forget.

This repo reframes well-known algorithm problems as **workplace lessons, life lessons, and anti-patterns** — using one repeatable template. The structure stays the same every time so your brain can pattern-match instead of memorize. New entries can be added by anyone, anytime, by filling in the template below.

---

## 📐 The Template

Every entry follows the **same four-act structure** — plus an optional bonus act:

| Act | Required? | Emoji | Question it answers |
|-----|-----------|-------|---------------------|
| **Algorithm** | ✅ Yes | 🧩 | What does the algorithm actually do? |
| **Workplace** | ✅ Yes | 🏢 | Where does this pattern show up at work? |
| **Life** | ✅ Yes | 🌍 | Where does it show up in everyday life? |
| **Anti-pattern** | ✅ Yes | ⚠️ | What's the seductive but wrong way people apply it? |
| **Power Struggle** | ⬜ Optional | 🪞 | Use when the workplace dynamic is juicy enough to deserve its own section (e.g. authority, gatekeeping, faction dynamics) |

### The blank template

Copy this block, fill it in, and paste it under `## 📖 The Catalog`:

```markdown
### N. [Problem Name]

> *[One-sentence problem description.]*

**🧩 Algorithm**
[Explain what the algorithm does, plainly. Mention complexity if it adds intuition.]

**🏢 Workplace**
[Where does this pattern appear at work? Be specific — name the scenario, not just the vibe.]

**🪞 Power Struggle**  <!-- optional: include only when the power dynamic is the real story -->
[When authority, permission, or faction structure is the bottleneck, call it out here.]

**🌍 Life**
[Where does it show up outside work? Keep it relatable — energy, relationships, habits, time.]

**⚠️ Anti-pattern**
[What do people instinctively do that sounds right but is wrong? Frame it as a quote, then debunk it.]
```

### How to fill it well

- **Algorithm** → Plain English first, complexity notation second. The reader should understand the *idea* before the Big-O.
- **Workplace** → Name a concrete scenario ("two recurring meetings covering the same agenda") not a vibe ("communication is hard").
- **Life** → One relatable example. Not a list. The reader should nod, not take notes.
- **Anti-pattern** → Start with the wrong instinct in quotes, then explain *why* it's wrong. The format is: *"Wrong instinct."* → why it's wrong → what to do instead.
- **Power Struggle** → Only when the real bottleneck is *power*, not *effort*. Skip it for problems where the workplace lesson is about process, not politics.

---

## ➕ How to Add a New Entry

1. Pick an algorithm problem (classic LeetCode, textbook, or real-world).
2. Copy the [blank template](#the-blank-template) above.
3. Fill in all four required acts. Add **Power Struggle** only if it fits.
4. Add a row to the [Table of Contents](#-the-catalog) with `#`, problem name, and a one-line core lesson.
5. Commit with message: `docs: add [Problem Name] entry`.

> **Rule of thumb:** if you can't fill all four acts with a concrete example, the problem isn't ready yet. Come back when the metaphor clicks.

---

## 📖 The Catalog

### Table of Contents

| # | Problem | Core Lesson |
|---|---------|-------------|
| 1 | [Two Sum](#1-two-sum) | Find the complement, don't brute-force alone |
| 2 | [Container With Most Water](#2-container-with-most-water) | The bottleneck sets the ceiling |
| 3 | [Sliding Window](#3-sliding-window) | Your energy window is finite — evict the old |
| 4 | [Binary Search](#4-binary-search) | Don't re-investigate what you already ruled out |
| 5 | [Merge Intervals](#5-merge-intervals) | Overlapping responsibilities should be merged |
| 6 | [Top K Frequent](#6-top-k-frequent) | You don't need to answer every voice |
| 7 | [LRU Cache](#7-lru-cache) | Forgetting is fine if you can reload |
| 8 | [Graph / DFS](#8-graph--dfs) | Org charts are graphs, not trees |
| 9 | [Cycle Detection](#9-cycle-detection) | If you're fixing yesterday's mess, you're in a loop |
| 10 | [Union Find](#10-union-find) | Who is actually on whose side? |
| 11 | [Dijkstra](#11-dijkstra) | Shortest path ≠ most comfortable steps |
| 12 | [Dynamic Programming](#12-dynamic-programming) | The best move depends on where you already are |

<!-- ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ -->
<!--  Entries below. Copy the blank template from "The Template"   -->
<!--  section, fill it in, and add it above the meta-lesson.        -->
<!-- ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ -->

---

### 1. Two Sum

> *Find two numbers in an array that add up to the target.*

**🧩 Algorithm**
Brute force checks every pair — $O(n^2)$. The smart approach uses a hash map: for each number, ask *"do I already have the complement?"* If yes, you're done. $O(n)$.

**🏢 Workplace**
Don't try to solve everything alone. Your job is to maintain a mental map of *"who complements what I'm missing"* — then ask for help. Finding the right person is faster than brute-forcing it yourself.

**🌍 Life**
Every strength has a complementary weakness. Instead of grinding your weak spots to mediocrity, find someone whose strengths overlap your gaps. Two average people who fit together outperform one exhausted generalist.

**⚠️ Anti-pattern**
*"If I just work harder and longer, I'll eventually find the answer."*
Sometimes. But most of the time the answer is sitting in the next office. The cost of searching alone scales quadratically; the cost of asking scales constantly.

---

### 2. Container With Most Water

> *Two lines form a container. Maximize the area between them.*

**🧩 Algorithm**
Start with the widest possible container and move the **shorter** line inward. Moving the taller line never increases the area — the shorter line is the bottleneck.

**🏢 Workplace**
When a project stalls, don't keep polishing the part that's already good enough. Find the bottleneck — the person, the permission, the dependency — and address that. Everything else is decorative effort.

**🪞 Power Struggle**
If one person's authority gates whether something ships, everyone else's hustle is capped by that gate. The real problem is the permission structure, not the execution speed of the people waiting.

**🌍 Life**
You might have plenty of time in the day, but if your energy is low, that's the short wall. Your daily output is bounded by energy, not hours. Optimizing your calendar when you're exhausted is moving the wrong wall.

**⚠️ Anti-pattern**
*"Optimize whatever side looks most promising."*
Frequently wrong. You should optimize the variable that currently constrains the result. The promising-looking side is often the side that's already doing fine.

---

### 3. Sliding Window

> *Maintain a dynamic sub-array; add elements on the right, evict from the left.*

**🧩 Algorithm**
Expand the window until a constraint is violated, then shrink from the left until it's satisfied again. The window slides — it doesn't grow forever.

**🏢 Workplace**
Your capacity — attention, focus hours, meeting slots — is the window. When a new priority arrives, an old one must leave. If you keep expanding the window without evicting, you violate the constraint and quality collapses.

**🌍 Life**
Your energy and attention have a fixed size. Saying "yes" to everything is an unbounded window. Healthy adulting is knowing what to drop so the current priorities actually fit.

**⚠️ Anti-pattern**
*"I can just add one more thing."*
You can — once. Do it every week for a year and your window overflows. The art is not in adding; it's in evicting on time.

---

### 4. Binary Search

> *Find a target in a sorted array by halving the search space each step.*

**🧩 Algorithm**
Compare the middle element to the target. Discard the half that can't contain the answer. Repeat. $O(\log n)$ instead of $O(n)$.

**🏢 Workplace**
Don't re-investigate everything from scratch each time. Ask: *"Which half of the problem can I eliminate right now?"* Bisect the incident. Bisect the bug. Bisect the org chart to find who actually owns the decision.

**🌍 Life**
When something breaks — a relationship, a habit, a project — don't start from the beginning. Ask *"is the problem in the first half or the second half?"* then zoom in. Most debugging is people-debugging, and people-debugging benefits from bisection too.

**⚠️ Anti-pattern**
*"Let me just re-read the whole thing from the top."*
That's linear search. You're paying $O(n)$ for what should cost $O(\log n)$. Before reading everything, ask which half you can safely ignore.

---

### 5. Merge Intervals

> *Given overlapping intervals, merge them into non-overlapping ranges.*

**🧩 Algorithm**
Sort by start time. If the next interval overlaps the current merged range, extend it. Otherwise start a new range. The output is a clean, non-overlapping set.

**🏢 Workplace**
Meetings, responsibilities, and ownership zones that heavily overlap should be merged. Two recurring meetings covering the same agenda? Merge them. Two people owning adjacent scopes with fuzzy boundaries? Clarify or combine. Otherwise the coordination tax explodes.

**🌍 Life**
If your "catch up with friends," "Sunday planning," and "grocery run" all collapse into the same afternoon, treat them as one block. Scheduling them as separate intervals when they're geographically and energetically adjacent is just creating overhead.

**⚠️ Anti-pattern**
*"More structure = more clarity."*
Only if the structures don't overlap. Five overlapping structures create more confusion than zero. Merge first, then split only when the merged scope genuinely outgrows one container.

---

### 6. Top K Frequent

> *Return the K most frequent elements in an array.*

**🧩 Algorithm**
Count frequencies, then pick the top K — often via a heap or bucket sort. You don't sort everything; you only extract the K that matter.

**🏢 Workplace**
You don't need to respond to every voice in the room. Identify the high-frequency, high-impact signals — the stakeholders who show up every cycle, the issues that recur every sprint — and prioritize those. The long tail can wait.

**🌍 Life**
Most of your happiness comes from a small number of relationships and habits. Most of your stress comes from a small number of recurring issues. Find the top K of each. Double down on the first; defuse the second.

**⚠️ Anti-pattern**
*"Treat all feedback equally."*
Treat all *feedback* respectfully, but don't treat all *issues* equally. The issue raised once by one person is not the same priority as the issue raised every week by ten people. Rank before you react.

---

### 7. LRU Cache

> *A cache of fixed size that evicts the least recently used item when full.*

**🧩 Algorithm**
Maintain a bounded store. On access, mark the item as recently used. When the store is full and a new item arrives, evict the least recently used one. Capacity is fixed; recency is the policy.

**🏢 Workplace**
Your working memory for context is finite. You can't hold every project, every colleague's preference, every API quirk simultaneously. The healthy move: let the stale stuff fade, and **build a system to reload it fast when needed**. Docs, wikis, and bookmarks are your eviction-aware reload mechanism.

**🌍 Life**
Forgetting is not a failure — it's garbage collection. The skill isn't never forgetting; it's knowing where to look it up. A well-organized note system means "I forgot" costs $O(1)$ to fix instead of $O(\text{awkward})$.

**⚠️ Anti-pattern**
*"I should remember everything."*
No. You should remember the *index* and reload the *content*. People who try to hold everything in their head either burn out or freeze when the cache overflows.

---

### 8. Graph / DFS

> *Traverse all reachable nodes from a starting point via depth-first search.*

**🧩 Algorithm**
From a start node, go as deep as possible along each branch before backtracking. You visit every node reachable through the edges — not just the ones in your immediate tree.

**🏢 Workplace**
Org charts are trees; actual relationships are graphs. You think A reports to B, but A also lunches with C, went to school with D, and owes E a favor. To understand how information and decisions actually flow, traverse the graph — the hidden edges are where the real influence lives.

**🌍 Life**
Your social world is not a tree. Your friend's friend's colleague is two hops away and might be exactly the connection you need. Depth-first exploration of your network — following one thread to its end before backtracking — surfaces opportunities that breadth-first scrolling never will.

**⚠️ Anti-pattern**
*"The org chart tells me who talks to whom."*
It tells you who *reports* to whom. It does not tell you who *trusts* whom. Trust edges are invisible in the chart and decisive in reality. Map the graph, not the tree.

---

### 9. Cycle Detection

> *Detect whether a traversal enters a node it has already visited — a cycle.*

**🧩 Algorithm**
Use fast and slow pointers (Floyd's algorithm) or a visited set. If the fast pointer catches the slow one, or a node reappears in the visited set, a cycle exists.

**🏢 Workplace**
If you spend every Monday fixing what broke on Friday — the same outage, the same conflict, the same miscommunication — you're not solving problems. You're traversing a cycle. Detect it: mark the nodes, watch for repeats, and **break the loop** instead of re-walking it.

**🌍 Life**
Recurring arguments with the same person about the same thing are cycles. The way out is not "try harder this time"; it's changing the graph so the edge that creates the loop no longer exists. That might mean a new process, a new boundary, or a new conversation entirely.

**⚠️ Anti-pattern**
*"This time it'll be different."*
If the inputs are the same and the structure is the same, the output will be the same. You're not solving — you're iterating. Break the cycle or accept that it will repeat.

---

### 10. Union Find

> *Track which elements belong to the same disjoint set; merge sets on demand.*

**🧩 Algorithm**
Each element starts in its own set. `Union` merges two sets. `Find` tells you which set an element belongs to (with path compression for efficiency). Over time, individual sets merge into larger clusters.

**🏢 Workplace**
Office politics, partly: who and whom are actually in the same faction. Two people who seem independent may share a mentor, a budget line, or a history of mutual promotion. Union-Find models this: you keep merging sets until the real clusters emerge — and the "surprising" alliances make sense.

**🌍 Life**
Communities form by union. Your gym friend and your work friend seem unrelated until you discover they went to the same college. The sets keep merging, and suddenly your world is smaller and more connected than you thought. That's not coincidence — that's the graph contracting.

**⚠️ Anti-pattern**
*"Everyone is independent until proven otherwise."*
Most people are already in a set you haven't detected yet. Assume hidden union edges exist and probe for them — it's faster than discovering them during a conflict.

---

### 11. Dijkstra

> *Find the shortest path in a weighted graph where edges have non-negative costs.*

**🧩 Algorithm**
Maintain a priority queue of unvisited nodes keyed by current best-known distance. Repeatedly pick the closest unvisited node, relax its edges, update neighbors. Guaranteed to find the minimum total cost path.

**🏢 Workplace**
The fastest career path is rarely the sequence of most comfortable steps. Sometimes the shortest route goes through a stretch assignment that costs more *now* but shortens the total distance dramatically. Dijkstra optimizes **cumulative cost**, not per-step comfort.

**🌍 Life**
The shortest path to a goal — a skill, a relationship, a savings target — often includes an uncomfortable edge early. Taking the comfortable route every step of the way tends to produce a long path with high total cost. The algorithm is telling you: minimize the sum, not the current step.

**⚠️ Anti-pattern**
*"Always pick the easiest next step."*
That's greedy, not Dijkstra. Greedy gets stuck in local minima. Dijkstra is willing to take a costly step now because it knows the *total* will be lower. Optimize the path, not the step.

---

### 12. Dynamic Programming

> *Break a problem into overlapping sub-problems; store results to avoid recomputation.*

**🧩 Algorithm**
The key insight: many problems aren't *"what do I choose now?"* but *"given that I'm in this state, what's the best outcome I can achieve from here?"* You fill a table of sub-answers; each cell depends on earlier cells. The final answer is one cell in that table.

**🏢 Workplace**
Career decisions are DP, not greedy. "Should I take this job?" is the wrong question. The right question is: *"Given where I am now — my skills, network, savings, and energy — what's the best outcome reachable from this state?"* Your current state encodes every past decision. The next move is just the transition function.

**🌍 Life**
Most life problems are state-based, not step-based. *"Should I move / switch careers / start now?"* only makes sense relative to where you already are. Two people standing at the same crossroads face different optimal moves because their *states* — savings, dependents, health, support network — differ. The same step from different states leads to different outcomes.

**⚠️ Anti-pattern**
*"What's the right choice in general?"*
There is no right choice in general. There is a right choice *from your current state*. Asking the question without the state is like running DP without the table — you're recomputing from scratch every time and getting a worse answer.

<!-- ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ -->
<!--  Add new entries above this line.                              -->
<!--  Don't forget to update the Table of Contents.                 -->
<!-- ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ -->

---

## 🧭 The Meta-Lesson

> **Algorithms are not about code. They're about the shape of decisions.**

Every problem above has a structure — and that structure recurs in meetings, in relationships, in how you spend a Sunday afternoon. The interview is over. The patterns are not.

---

## 📄 License

[MIT](LICENSE) — because survival tips should be open source.

---

<p align="center">
  <sub>Built with caffeine, graph theory, and mild organizational trauma.</sub>
</p>
