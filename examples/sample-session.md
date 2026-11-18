# An illustrative learning session

This is an invented teaching example, not an execution transcript or a result from a real repository. The files below are the entire example; line numbers in the source pointers refer to these snippets. A real session uses your repository's actual files and revision.

## The small project

A shop calculates a delivery charge from an order's subtotal, which is the sum of item prices before shipping. These two fictional files implement it.

`shipping.py`:

```python
FREE_FROM = 50
STANDARD_FEE = 5

def fee(subtotal):
    return 0 if subtotal >= FREE_FROM else STANDARD_FEE
```

`checkout.py`:

```python
from shipping import fee

def quote(prices):
    subtotal = sum(prices)
    shipping = fee(subtotal)
    return subtotal + shipping
```

## Start with the purpose

**Learner:** I built this with AI. Teach me why there are two files and how they connect.

**Agent:** The code adds the item prices, asks for the shipping charge, then combines them into a final quote. Think of a cashier totaling a basket and consulting a delivery price card. Here, the "price card" is a function: a named piece of code that accepts an input and returns an answer. (`checkout.py:L3-L6`, illustrative snapshot)

`checkout.py` coordinates the calculation. `shipping.py` contains the shipping rule. Separating those responsibilities could make the rule easier to change; that is my interpretation, because this example has no decision record explaining the author's reason. (`checkout.py:L1-L6`; `shipping.py:L1-L5`, illustrative snapshot)

## A reading route

| Read | Notice | Question it answers |
| --- | --- | --- |
| `checkout.py`, `quote`, lines 3–4 | The input list becomes one subtotal. | Where does the calculation start? |
| `shipping.py`, `fee`, lines 1–5 | The comparison chooses either 0 or 5. | What determines the delivery charge? |
| `checkout.py`, lines 5–6 | The returned fee is added to the subtotal. | How does the shipping decision affect the quote? |

## Follow a value across the files

**Agent:** Let's use the illustrative input `[20, 25]`. Reading the code, we can calculate the expected path by hand:

1. `quote` receives two item prices. `sum(prices)` produces a subtotal of 45. (`checkout.py:L3-L4`)
2. `fee(45)` checks whether 45 is at least 50. It is not, so the function returns 5. (`shipping.py:L1-L5`)
3. `quote` adds 45 and 5, so the predicted quote is 50. (`checkout.py:L5-L6`)

This is a static walkthrough; I have not run the example. The snippets also contain no explicit input validation. What a larger app does with invalid prices is outside this example. (`checkout.py:L3-L6`; `shipping.py:L4-L5`)

## Check the connection

**Agent:** Suppose the items instead total exactly 50. What shipping charge does this code choose, and why?

*In an interactive session, the agent pauses here for your answer. The exchange below illustrates one possible continuation.*

**Learner:** Shipping is 5 because you have to go over 50.

**Agent:** Look at `>=` in `shipping.py`, line 5. It means "greater than or equal to." Exactly 50 meets that condition. Try the final quote again with that in mind.

**Learner:** Shipping is 0, so the final quote is 50. If we changed `>=` to `>`, an order at exactly 50 would cost 55 instead.

**Agent:** That correctly explains the boundary and predicts the effect of that change. It demonstrates this particular rule in this example. We have not assessed your understanding of input handling or the rest of a real project.

## Save only if requested

**Learner:** Save my progress outside the project, in my learning-notes folder.

The agent uses the requested location once it is known. A record for this illustrative exchange would contain:

| Concept | State | Evidence | Next step |
| --- | --- | --- | --- |
| Shipping threshold and comparison | Demonstrated | Learner correctly explained the equality case and predicted the effect of `>`. | Recheck if the threshold or comparison changes. |
| Separation of responsibilities | Explained | Agent explained it; learner has not explained it back. | Ask why `quote` calls `fee`. |
| Input handling | Not assessed | No question answered on this topic. | Inspect validation in the actual project. |

Without a save request, the session stays in chat. In a real project, each saved finding includes the inspected revision and actual source pointers.
