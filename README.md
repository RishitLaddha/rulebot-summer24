
# Rule-Based E-commerce Chatbot

A simple rule-based chatbot that answers common e-commerce queries such as pricing, availability, order status, returns, payment methods, and support contacts.  
Originally created as a small summer project in my first year and later cleaned up for GitHub.

---

## Overview

The notebook implements a lightweight chatbot using straightforward keyword rules. It does not use machine learning.  
It is ideal for understanding how rule matching works and for quick prototypes where predictable responses are needed.

What it can handle:
- Greetings
- Pricing questions (e.g., “price of Apple laptop”)
- Availability questions (e.g., “do you have Samsung phones”)
- Order status prompts (asks for order ID)
- Return and refund policy
- Accepted payment methods
- Customer support contact

---

## Data Model

A single in-memory dictionary named `products` stores sample categories, items, brands, and prices:

- `electronics`: laptop, phone, tablet, headphones  
- `clothing`: tops, pants, jeans, shoes, jackets  
- `home_appliances`: refrigerator, washing_machine, microwave, vacuum_cleaner  
- `books`: fiction, non-fiction, comics, textbooks

Each item maps to a set of brands with example prices. This is mock data for demonstration.

---

## How It Works

Core functions:
- `chatbot_response(user_input)`: Routes a message based on simple keyword checks (price, availability, returns, etc.).
- `handle_pricing_queries(user_input)`: Looks up item and brand in `products` and returns a price if found.
- `handle_availability_queries(user_input)`: Lists available brands for a matched item.
- `run_chatbot()`: Command-line loop that reads user input and prints responses.
- `run_tests()`: Small assertion suite that validates key responses.

Routing logic is intentionally minimal: lowercase the input and check for the presence of keywords like “price”, “available”, “return”, “payment”, “support”, and so on. This keeps behavior transparent and easy to modify.

---

## Quick Start

Requirements:
- Python 3.10+ (tested on 3.11)
- Jupyter (if running the `.ipynb`)

Options to run:

1) In Jupyter Notebook  
- Open the `.ipynb` file.  
- Run all cells.  
- At the prompt, type messages such as:
```

Hello
What is the price of an Apple laptop?
Do you have Samsung phones available?
Where is my order?
What is your return policy?

```
- Type `exit`, `quit`, or `bye` to end.

2) From a script (optional)  
- Export the core cells to a `.py` file.  
- Ensure `run_chatbot()` is called in `if __name__ == "__main__":`.

---

## Example Interactions

```

You: Hello
Chatbot: Hello! How can I assist you today?

You: What is the price of an Apple laptop?
Chatbot: The price of Apple Laptop is \$1200.

You: Do you have Samsung phones available?
Chatbot: We have Phone from Samsung, Apple, Redmi, Oneplus, Google. Please specify a brand for more details.

````

---

## Tests

The notebook includes `run_tests()` with basic assertions:

```python
run_tests()
# Output:
# All tests passed!
````

Use this to verify that the routing and formatting are working as expected.

---

## Limitations

* Purely rule-based: no NLP or learning.
* Keyword-sensitive: user phrasing must include expected item/brand names.
* Static catalog: prices and brands are hard-coded.

These limitations are intentional for a compact demo. For a production system, consider an intent classifier, entity extraction, and a real catalog or API.

---

## Possible Improvements

* Add simple NLP (synonyms, spelling tolerance).
* Extract entities with regex or a lightweight parser.
* Load products from JSON/CSV instead of hard-coding.
* Add unit tests for more edge cases.
* Wrap in a small web UI (Flask/FastAPI) for a browser chat interface.

---

## License

Open source for learning and reuse. Feel free to fork and adapt.
