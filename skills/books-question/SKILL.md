---
name: books-question
description: Answer a question about a client's books in Mastro with real figures, such as spending, income, balances, profit, or what a transaction was. Use whenever someone asks about a specific client's numbers.
---

# Answer a question about a client's books

1. Find the client with `list_clients`, and pass its id as `clientId` to every other tool.
2. Call `books_map` with the person's question, word for word. It's Mastro's map of the books for
   that question: the accounts, contacts, bank feeds, rules, and documents the question names, with
   their balances and activity for the periods it mentions.
3. Go further only as far as the question needs:
   - `report` for the profit and loss (also by month), cash flow, cash by month, balance sheet, and
     receivables and payables agings.
   - `balances` for every account's balance on a day.
   - `read_report` for any other report, and `read_data` for records. `mastro_guide` lists them
     all.
4. Amounts come back in integer cents: show them as dollars, such as $1,234.56. Dates are
   `YYYY-MM-DD`. Say which period each figure covers.
5. Say where each number comes from (the report and the period). If lines are still waiting for
   review in that period (`review_counts`), or the month isn't closed, say the figure can still
   change.

Numbers that identify a person or an account come back with only their last four digits, and
employees' pay never comes back at all. Don't ask the person for more.
