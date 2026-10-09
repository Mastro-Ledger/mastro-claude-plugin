---
name: review-queue
description: Work a client's bank and card review queue in Mastro. Use when someone asks to categorize, clean up, or go through a client's bank or card transactions, or to get the review queue ready to approve.
---

# Work the review queue

Mastro holds each client's new bank and card lines for review until someone at the firm approves
where they go. You suggest; the person approves on Mastro's screen.

1. Find the client with `list_clients`, and pass its id as `clientId` to every other tool.
2. Call `review_counts` to see how many lines are waiting and how many a rule already suggests a
   category for.
3. Call `bank_lines_for_review` to list them: each line's id, date, amount in cents (money in is
   positive), the bank's description, the merchant, and the rule that suggests a category, if one
   does.
4. Call `chart_of_accounts` for the accounts to categorize into. Use the client's own accounts,
   never ones you make up.
5. For each line with no suggestion, call `suggest_categorization` with the account and the amount
   in cents without its sign, and a one-sentence reason. Split a line across accounts only when it
   clearly covers more than one thing, and make the splits add up to the line's amount.
6. When you can't tell what a line is, don't guess. Draft a question to the client about that line
   with `draft_client_question`: plain words, one question, what you need and why.
7. When the firm keeps categorizing the same merchant the same way, offer a rule with
   `suggest_rule`, so next month's lines arrive with a suggestion.
8. Finish with `show_review_queue`, so the person sees every line with its suggestion and approves
   or rejects each one. Nothing posts until they do, and approving is always their click, never
   yours.

Then say briefly what you did: how many lines you suggested categories for, which accounts you
used most, and which lines you asked the client about.
