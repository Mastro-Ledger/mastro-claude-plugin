---
name: month-end-close
description: Close a client's month in Mastro. Use when someone asks to close a month, get a client ready for month-end, or find out what's keeping a month from closing.
---

# Close a month

A month closes in Mastro once nothing blocks it: every line reviewed, every bank and card account
reconciled, and the rest of the firm's checks passing. You find what blocks it and clear what you
can; the firm's owners and admins close it.

1. Find the client with `list_clients`, and pass its id as `clientId` to every other tool.
2. Settle which month. If the person didn't say, `show_month_end` with no month picks the first
   month not yet closed. Months are named by their last day, such as `2026-09-30`.
3. Call `month_end_checklist` with that day. It lists each check, whether it blocks the close or
   only warns, whether it passes, and why not.
4. Work each check that blocks, in this order:
   - **Lines waiting for review:** work them the way the review-queue skill does, then
     `show_review_queue` for the person to approve.
   - **An account not reconciled:** `show_reconciliation` with that account shows what's still
     outstanding. A reconciliation at a difference of zero can be finished on that screen.
   - **Questions waiting on the client:** `questions` lists the open ones, so the person knows what
     to chase.
5. Mention the warnings too. They don't stop the close, but the person should know about them.
6. When nothing blocks, show the close with `show_month_end`. The firm's owners and admins close the
   month there with a click.

Where the app can't draw Mastro's screens, such as a terminal, the same tools come back as text.
The person can close the month in Mastro, or have you close it with `do_action` (the `close_month`
action, which `mastro_guide` describes) where their firm lets its AI do that.
