<!-- Repository Banner -->
<p align="center">
  <img src="assets/banner.png" alt="LeetCode for Adults — Algorithms, office politics, and other things nobody warned you about." width="100%">
</p>

<h1 align="center">LeetCode for Adults</h1>

<p align="center">
  <strong>Algorithms, office politics, and other things nobody warned you about.</strong>
</p>

<p align="center">
  🌐 <b>Language:</b>
  &nbsp;<a href="README.md"><b>English</b></a>
  &nbsp;·&nbsp;<a href="README.zh.md">中文</a>
  &nbsp;·&nbsp;<a href="README.ja.md">日本語</a>
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

Copy this block, fill it in, and save it as `problems/NN-slug/README.md`:

```markdown
<p align="center">🌐 Language: &nbsp;<a href="README.md"><b>English</b></a> &nbsp;·&nbsp; <a href="README.zh.md">中文</a> &nbsp;·&nbsp; <a href="README.ja.md">日本語</a></p>

<p align="center"><a href="../README.md#-the-catalog">← Back to Catalog</a></p>

---

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
2. Create a new directory: `problems/NN-slug/` (e.g. `problems/13-valid-palindrome/`).
3. Copy the [blank template](#the-blank-template) above into `README.md`, `README.zh.md`, and `README.ja.md` — one per language.
4. Fill in all four required acts. Add **Power Struggle** only if it fits.
5. Add a row to the [Table of Contents](#-the-catalog) below with `#`, problem name, and a one-line core lesson.
6. Commit with message: `docs: add [Problem Name] entry`.

> **Rule of thumb:** if you can't fill all four acts with a concrete example, the problem isn't ready yet. Come back when the metaphor clicks.

---

## 📖 The Catalog

Each problem lives in its own directory (`problems/NN-slug/`) with three language versions. Click through to read the full breakdown.

### Table of Contents

| # | Problem | Core Lesson |
|---|---------|-------------|
| 1 | [Two Sum](problems/01-two-sum/README.md) | Find the complement, don't brute-force alone |
| 2 | [Container With Most Water](problems/02-container-with-most-water/README.md) | The bottleneck sets the ceiling |
| 3 | [Sliding Window](problems/03-sliding-window/README.md) | Your energy window is finite — evict the old |
| 4 | [Binary Search](problems/04-binary-search/README.md) | Don't re-investigate what you already ruled out |
| 5 | [Merge Intervals](problems/05-merge-intervals/README.md) | Overlapping responsibilities should be merged |
| 6 | [Top K Frequent](problems/06-top-k-frequent/README.md) | You don't need to answer every voice |
| 7 | [LRU Cache](problems/07-lru-cache/README.md) | Forgetting is fine if you can reload |
| 8 | [Graph / DFS](problems/08-graph-dfs/README.md) | Org charts are graphs, not trees |
| 9 | [Cycle Detection](problems/09-cycle-detection/README.md) | If you're fixing yesterday's mess, you're in a loop |
| 10 | [Union Find](problems/10-union-find/README.md) | Who is actually on whose side? |
| 11 | [Dijkstra](problems/11-dijkstra/README.md) | Shortest path ≠ most comfortable steps |
| 12 | [Dynamic Programming](problems/12-dynamic-programming/README.md) | The best move depends on where you already are |
| 13 | [Two Sum II](problems/13-two-sum-ii/README.md) | Establish order first, then adjust strategy |
| 14 | [Boats to Save People](problems/14-boats-to-save-people/README.md) | Handle the bottleneck first, save the flexible filler for last |
| 15 | [Move Zeroes](problems/15-move-zeroes/README.md) | Don't move the noise — compact what matters |
| 16 | [Remove Duplicates from Sorted Array](problems/16-remove-duplicates-from-sorted-array/README.md) | Sort first, deduplicate second |
| 17 | [Linked List Cycle](problems/17-linked-list-cycle/README.md) | You don't need memory to detect a cycle — you need dynamics |
| 18 | [3Sum](problems/18-3sum/README.md) | Once your thoughts are sorted, walk forward — don't look back |
| 19 | [Sliding Window](problems/19-sliding-window/README.md) | Right expands into the unknown; left repairs the known |
| 20 | [Find All Anagrams](problems/20-find-all-anagrams-in-a-string/README.md) | When the frame is fixed, don't resize it — slide and check |
| 21 | [Longest Repeating Character Replacement](problems/21-longest-repeating-character-replacement/README.md) | You don't need zero noise — you need noise within your budget |
| 22 | [Find First and Last Position](problems/22-find-first-and-last-position-in-sorted-array/README.md) | Finding the boundaries is not the same as finding the value |
| 23 | [Bubble Sort](problems/23-bubble-sort/README.md) | The biggest problems surface first — and the absence of friction is the signal you're done |
| 24 | [Selection Sort](problems/24-selection-sort/README.md) | See everything before committing — then commit irrevocably |
| 25 | [Insertion Sort](problems/25-insertion-sort/README.md) | You don't choose in isolation — you find your level among what's settled |
| 26 | [Merge Sort](problems/26-merge-sort/README.md) | Big problems are just small problems you haven't cut in half yet |
| 27 | [Quick Sort](problems/27-quick-sort/README.md) | Progress doesn't require perfect balance — it requires a pivot |
| 28 | [Heap Sort](problems/28-heap-sort/README.md) | You don't sort the data — you impose a structure, and the structure sorts for you |
| 29 | [Counting Sort](problems/29-counting-sort/README.md) | You don't need to compare what you can count — the range is the answer |
| 30 | [Bucket Sort](problems/30-bucket-sort/README.md) | Scatter before you sort — the decomposition makes the parts sortable |
| 31 | [Delete a Value from a Linked List](problems/31-delete-a-value-from-a-linked-list/README.md) | You don't destroy the node — you redirect the pointer that reached it |
| 32 | [Majority Element](problems/32-majority-element/README.md) | You don't find the majority by counting — you find it by canceling |

> 💡 Want to add a new problem? See [How to Add a New Entry](#-how-to-add-a-new-entry) above.

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
