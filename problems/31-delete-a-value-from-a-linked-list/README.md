<p align="center">🌐 Language: &nbsp;<a href="README.md"><b>English</b></a> &nbsp;·&nbsp; <a href="README.zh.md">中文</a> &nbsp;·&nbsp; <a href="README.ja.md">日本語</a></p>

<p align="center"><a href="../README.md#-the-catalog">← Back to Catalog</a></p>

---

### 31. Delete a Value from a Linked List

> *Find and remove the first node whose value equals `target`. Return the new head.*

**🧩 Algorithm**
The deletion itself is trivial — one line: `prev.next = cur.next`. The node is gone. The list is fixed. What's hard is everything *around* the deletion: walking to the right node, handling the edge where the target is the head, and not losing the thread when you cut.

The `dummy` node is the trick. You create a sentinel that sits *before* the head — `dummy.next = head` — and you start your walk from `dummy`, not from `head`. Why? Because if the target *is* the head, you need a `prev` that points to it — and the head has no predecessor. The dummy *is* the predecessor. It exists so that every node — including the head — has someone behind it. You never face the "what if I need to delete the first one?" edge case, because the dummy made the first node no longer special.

```python
def delete_value(head, target):
    dummy = ListNode(0, head)
    prev = dummy
    cur = head

    while cur:
        if cur.val == target:
            prev.next = cur.next
            break

        prev = cur
        cur = cur.next

    return dummy.next
```

> Time $O(n)$ · Space $O(1)$

The deeper principle: **you don't delete the thing — you redirect the thing that points to it.** The node itself isn't destroyed. It's *orphaned*. The pointer that used to reach it now skips over it. The node still exists in memory, still holds its value, still has its `next` — but nobody can get to it. It's been cut from the chain, not removed from existence. The deletion is a *rerouting*, not a destruction.

And the `dummy` wisdom: **every edge case has a predecessor if you create one.** The head is special because it's the only node without a `prev`. The dummy removes that specialness. Instead of handling "what if it's the head?" as a separate case, you make the head *not special* by giving it a predecessor. The edge case doesn't go away — it *dissolves*, because the condition that created it ("no predecessor") no longer exists. You didn't handle the edge case. You *eliminated* it by changing the structure so the edge never occurs.

**🏢 Workplace**
When you fire someone — or remove a project, a process, a policy — the act of removal is simple: one decision, one announcement, one redirect. What's hard is the *context around the removal*: the walk up to it, the positioning, the conversations before the conversation. And the hardest edge: what if the thing you're removing is the *head* — the lead, the founder, the pillar?

The `dummy` wisdom: **every removal has a context if you create one.** The reason firing the head is harder than firing anyone else is that the head appears to have no predecessor — no one above them to make the removal feel structurally normal. But if you've built a `dummy` — a board, an advisor, a framework, a governance structure that sits *above* the head — then the head isn't special anymore. They have a predecessor. The removal is `prev.next = cur.next`: the board redirects the chain. The head is orphaned, not destroyed. The organization moves on — `return dummy.next` — and the new head surfaces naturally.

And the principle: **you don't destroy the person — you reroute the reporting line.** The person still exists. Their skills, their relationships, their history — all still there. But the chain no longer reaches them. The rerouting is the removal. The destruction is unnecessary — and usually counterproductive. You don't need to erase someone to remove their influence. You just need to redirect the pointer that used to lead to them.

**🌍 Life**
When you remove something from your life — a habit, a commitment, a relationship, a version of yourself — the act of removal is simple: one redirect, one "I'm done," one `prev.next = cur.next`. What's hard is the *context*: the positioning, the walk up to the decision, the conversations before the break.

And the hardest edge: what if you're removing the *head* — your core identity, your primary role, the thing that has been the start of your list for years? "I'm not a lawyer anymore." "I'm not a wife anymore." "I'm not the funny one anymore." The head has no predecessor. There's nothing *before* it to redirect from. It feels like removing the foundation.

The `dummy` wisdom: **create a predecessor for your identity.** The `dummy` is the *you* that exists before and beyond any single role — the awareness that watches the roles, the values that predate the job, the self that isn't the title. When you have a `dummy` — a sense of self that isn't tied to any one node — then no role is special. Removing the head isn't an existential crisis; it's `prev.next = cur.next`. The role is orphaned, not the self. `return dummy.next` — the next thing you are surfaces naturally. The chain continues because the dummy was holding it all along.

And the principle: **you don't destroy the old self — you reroute.** The habit still exists in memory. The old role still shaped who you are. The relationship still happened. You don't erase it. You redirect the pointer that used to lead to it. The `next` of your life now points somewhere new — and the old node sits in the past, unreachable by the current chain, but not destroyed. Not forgotten. Just *no longer where the chain goes*. The deletion is a rerouting, not a burning. And the chain is longer — and healthier — for having been redirected.

**⚠️ Anti-pattern**
*"I need to completely destroy the old thing before I can move on."*
That's trying to `del` the node instead of `prev.next = cur.next`. You're trying to erase the old self — the old career, the old relationship, the old habit — from existence. But the node is in memory. It shaped you. It's part of your structure. You can't `del` it without corrupting the chain — the memories, the skills, the growth it gave you. The `dummy` approach says: don't destroy. Redirect. The old node doesn't need to be erased; it needs to be *unreachable from the current chain*. Walk on. `prev.next = cur.next`. The old you is still in memory — still shaped you, still matters — but the chain has moved on. `return dummy.next`. The new head. The next role. The next chapter. Not the death of the old — the rerouting of the chain.
