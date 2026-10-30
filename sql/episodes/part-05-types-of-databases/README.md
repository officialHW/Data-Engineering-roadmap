# Part 5: Types of databases

Relational vs non-relational databases, explained with an online shop.

[Back to the SQL series](../../README.md)

---

## The big idea

Not every database stores data in tables. Databases come in two families:

- **Relational (RDBMS):** data lives in tables with rows and columns, linked by keys.
- **Non-relational (NoSQL):** everything that doesn't use that table model. NoSQL is commonly read as "not only SQL".

Different databases are built for different jobs. A real shop might use several of them together.

---

## The four common types

| Type | Proper term | How data is stored | Example tools | Job in our shop |
|---|---|---|---|---|
| Relational | RDBMS | Tables: rows and columns, linked by keys | PostgreSQL, MySQL, SQLite | Customers and their orders |
| Document | Document store | Flexible JSON-like documents | MongoDB | Products with different details |
| Key-value | Key-value store | A key that returns a value | Redis | Loading a shopping cart instantly |
| Graph | Graph database | Nodes and the relationships between them | Neo4j | "Customers who bought this also bought" |

Other types exist too, such as wide-column (Cassandra), time-series (InfluxDB), and vector databases.

---

## See the relational type in action

Our practice database is relational. Load it from [`data/thefirst_henrystore.sql`](../../data/thefirst_henrystore.sql), then run:

```sql
SELECT Customers.name, Products.name AS product, Orders.quantity
FROM Orders
JOIN Customers ON Orders.customer_id = Customers.customer_id
JOIN Products  ON Orders.product_id  = Products.product_id
LIMIT 5;
```

Three tables, linked by `customer_id` and `product_id`. That linking is what makes it relational.

---

## What the other types look like

These are illustrations. They are not part of the practice database, and you can't run them in SQLite.

**Document:** each product is its own flexible document, so a phone and a T-shirt can hold different details.

```json
{ "name": "Phone",   "storage_gb": 128, "colour": "black" }
{ "name": "T-shirt", "size": "M",        "fabric": "cotton" }
```

**Key-value:** give it a key, get a value back.

```
cart_482  ->  3 items
```

**Graph:** customers and products are nodes, and purchases are the relationships between them. That makes questions like "who else bought this?" fast to answer.

---

## Good to know

- "Non-relational" doesn't mean the data has no relationships. It means the database doesn't use the relational table model. Graph databases are built entirely around relationships.
- The categories overlap in real life. For example, PostgreSQL is relational but can also store JSON.

---

## Next

Part 6: what we can actually do with the data inside a database.
