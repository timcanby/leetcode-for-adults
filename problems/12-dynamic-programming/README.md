<p align="center">🌐 Language: &nbsp;<a href="README.md"><b>English</b></a> &nbsp;·&nbsp; <a href="README.zh.md">中文</a> &nbsp;·&nbsp; <a href="README.ja.md">日本語</a></p>

<p align="center"><a href="../README.md#-the-catalog">← Back to Catalog</a></p>

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
