# Part 5: Types of databases

Relational vs non-relational databases, what each one is for, what goes inside, and where you will meet them.

[Back to the SQL series](../../README.md)

---

## The big idea

Not every database stores data in tables. Databases come in two families:

- **Relational (RDBMS):** data lives in tables with rows and columns, and the tables are linked by keys. RDBMS stands for Relational Database Management System. This is the family SQL was built for.
- **Non-relational (NoSQL):** everything that does not use that table model. NoSQL is commonly read as "not only SQL".

Different databases are built for different jobs. A real shop usually uses several of them together.

---

## Relational databases

**What they contain:** neat, structured data. Every row has the same columns, and every column has a set type, such as a number, text or date. Tables are linked using IDs, called **keys**. A key is a value that points to a row in another table, like `customer_id` in our Orders table.

**What they are used for:** data where accuracy matters and the shape is predictable. Orders, payments, bank balances, customer records, inventory.

**Why people choose them:**
- The structure catches mistakes, for example an order for a customer that does not exist.
- Updates are safe. If a payment fails halfway, the database can undo it instead of leaving a mess.
- SQL makes it easy to ask questions across many tables at once.

**Popular tools**

| Tool | Good to know |
|---|---|
| PostgreSQL | Free and very popular with data teams. Also handles JSON. |
| MySQL | Free. Runs a huge number of websites. |
| SQLite | A tiny database in a single file. It is what we use in this series. |
| Microsoft SQL Server | Common inside large companies. |
| Oracle Database | Common in banks and big enterprises. |

**How a relational database is built**

| Word | Plain meaning | In our shop |
|---|---|---|
| Table | One topic of data, like a spreadsheet tab | `Customers`, `Products`, `Orders` |
| Row | One record in a table | One customer, or one order |
| Column | One piece of information about each record | `name`, `city`, `price` |
| Primary key | A column that uniquely identifies each row | `customer_id` in `Customers` |
| Foreign key | A column that points to a row in another table | `customer_id` in `Orders` |
| Schema | The plan for what tables and columns exist | The design of the shop database |

We use SQL to work with exactly this kind of database, so the rest of the series builds on these words.

**Data warehouses are relational too.** A data warehouse is a database built for analysis instead of day-to-day running of an app. You query it with SQL. Examples: Snowflake, Google BigQuery, Amazon Redshift. As a data engineer you will spend a lot of time here.

---

## Non-relational (NoSQL) databases

This is the other family, and we will only look at it briefly. It holds data that does not fit neatly into rows and columns, or that changes shape often, and each type stores data in its own way. People choose these when they need flexible data, very fast lookups, huge traffic, or data that is mostly about connections.

| Type | How data is stored | Example tools | Job in our shop |
|---|---|---|---|
| Document | Flexible JSON-like documents | MongoDB, Firestore | Products with different details |
| Key-value | A key that returns a value | Redis, DynamoDB | Loading a shopping cart instantly |
| Graph | Nodes and the relationships between them | Neo4j, Amazon Neptune | "Customers who bought this also bought" |
| Wide-column | Rows whose columns can differ, built for huge scale | Cassandra, HBase | Billions of page views and clicks |
| Time-series | Measurements stamped with the time | InfluxDB | Website traffic every second |
| Vector | Numbers that capture meaning, for AI search | Pinecone | "Show me similar products" |

You do not need to learn these now. Just know they exist and what job each is good at.

---

## What formats can data come in?

Data comes in three broad shapes. The shape often decides which database fits.

| Shape | What it looks like | Examples | Usually stored in |
|---|---|---|---|
| Structured | Rows and columns, same layout every time | Orders, customers, prices, bank transactions | Relational databases, data warehouses |
| Semi-structured | Has labels, but the layout can vary | JSON, XML, API responses, app logs | Document databases, or JSON columns in relational ones |
| Unstructured | No set layout | Images, video, audio, PDFs, emails, free text | Object storage and file storage |

**JSON** is a way of writing data as labelled pairs. Here is a product written as JSON:

```json
{ "name": "Phone", "storage_gb": 128, "colour": "black" }
```

**What about images?** Databases are not the usual home for images and videos. They are large files, and databases are built for records. The common approach is:

1. The file (the product photo) goes into **object storage**, a service made for storing files. Examples: Amazon S3, Google Cloud Storage, Azure Blob Storage.
2. The database stores only a text link to that file, for example a `photo_url` column in the Products table.

So the database holds the information about the image, and storage holds the image itself.

---

## Where are they used in real life?

| Where | Database type | Why |
|---|---|---|
| Online shop: orders, payments, stock | Relational | Every payment must add up, and records must link correctly |
| Online shop: product catalogue | Document | A phone and a T-shirt have different details |
| Shopping cart and login sessions | Key-value | Needs to load in a fraction of a second |
| Social network: who follows whom | Graph | The connections are the data |
| Streaming app: viewing history at huge scale | Wide-column | Billions of rows written constantly |
| Company reports and dashboards | Data warehouse (relational) | Built to answer big analysis questions with SQL |
| Product photos, videos, PDFs | Object storage | Files are too large and awkward for a database |

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

## A quick look at one non-relational type

This is an illustration only. It is not part of the practice database, and you can't run it in SQLite. In a document database, each product is its own flexible document, so a phone and a T-shirt can hold different details:

```json
{ "name": "Phone",   "storage_gb": 128, "colour": "black" }
{ "name": "T-shirt", "size": "M",        "fabric": "cotton" }
```

---

## Good to know

- "Non-relational" doesn't mean the data has no relationships. It means the database doesn't use the relational table model. Graph databases are built entirely around relationships.
- The categories overlap in real life. For example, PostgreSQL is relational but can also store JSON.
- It is not relational versus non-relational, with one winner. Real companies use both, and picking the right one for the job is part of a data engineer's work.
- The SQL you learn in this series works on relational databases and data warehouses. That is where most data engineering work with SQL happens.

---

## Next

Part 6: what we can actually do with the data inside a database.
