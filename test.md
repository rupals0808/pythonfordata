---

### 🟢 Part 1: Foundations (Sessions 1–5) — 5 Questions

#### **Q1. (Session 1 — Data Types)**
What is the output of the following code?
```python
price = "$999.99"
clean_price = float(price.replace("$", ""))
print(type(clean_price))
```
- **a)** `<class 'str'>`
- **b)** `<class 'int'>`
- **c)** `<class 'float'>`
- **d)** `ValueError`

---

#### **Q2. (Session 2 — Functions & List Comprehensions)**
What does this function return?
```python
def process(records, min_qty=1):
    return [r for r in records if r['quantity'] >= min_qty]

data = [
    {'product': 'Laptop', 'quantity': 3},
    {'product': 'Mouse', 'quantity': 0},
    {'product': 'Keyboard', 'quantity': 5}
]
result = process(data, min_qty=2)
print(len(result))
```
- **a)** `1`
- **b)** `2`
- **c)** `3`
- **d)** `0`

---

#### **Q3. (Session 3 — File Handling)**
Which file mode should you use to add new log entries to an existing file without overwriting previous entries?
- **a)** `"r"` (read)
- **b)** `"w"` (write)
- **c)** `"a"` (append)
- **d)** `"x"` (exclusive create)

---

#### **Q4. (Session 4 — Exception Handling)**
What gets printed when this code runs?
```python
try:
    value = int("not_a_number")
except ValueError:
    print("BAD")
except TypeError:
    print("WRONG")
else:
    print("OK")
finally:
    print("DONE")
```
- **a)** `BAD`
- **b)** `WRONG` then `DONE`
- **c)** `BAD` then `DONE`
- **d)** `OK` then `DONE`

---

#### **Q5. (Session 5 — Libraries & Virtual Environments)**
What is the standard command sequence to create a virtual environment and install packages from a requirements file?
- **a)** `pip install venv` then `pip install requirements.txt`
- **b)** `python -m venv .venv` then `pip install -r requirements.txt`
- **c)** `python create venv` then `pip install --file requirements.txt`
- **d)** `pip venv .venv` then `pip freeze > requirements.txt`

---

### 🟡 Part 2: Data Handling & DE Concepts (Sessions 6–12) — 15 Questions

#### **Q6. (Session 6 — Pandas Fundamentals)**
Which method displays row count, column names, non-null counts, data types, and memory usage all in a single call?
- **a)** `df.describe()`
- **b)** `df.head()`
- **c)** `df.info()`
- **d)** `df.shape`

---

#### **Q7. (Session 6 — Pandas Fundamentals)**
What is the primary difference between `df.loc[0:3]` and `df.iloc[0:3]`?
- **a)** They are identical — both return index rows 0, 1, and 2
- **b)** `loc` is label-based (endpoint is inclusive); `iloc` is integer position-based (endpoint is exclusive)
- **c)** `loc` selects columns; `iloc` selects rows
- **d)** `loc` is only for string indices; `iloc` is only for numeric indices

---

#### **Q8. (Session 7 — Data Cleaning)**
You have dirty region values like `["  NORTH ", "south", " East"]`. Which chain of methods standardizes them to `["north", "south", "east"]`?
- **a)** `df['region'].lower().trim()`
- **b)** `df['region'].str.strip().str.lower()`
- **c)** `df['region'].apply(strip).apply(lower)`
- **d)** `df['region'].clean().standardize()`

---

#### **Q9. (Session 7 — Data Cleaning)**
What does `pd.to_numeric(df['price'], errors='coerce')` do when it encounters an invalid string like `"N/A"`?
- **a)** Raises a `ValueError`
- **b)** Retains the string `"N/A"` as-is
- **c)** Replaces the value with `NaN`
- **d)** Converts the value to `0`

---

#### **Q10. (Session 8 — Aggregations)**
What does the following named aggregation produce?
```python
df.groupby('region').agg(
    total_revenue=('amount', 'sum'),
    order_count=('order_id', 'count')
)
```
- **a)** A DataFrame with one row per unique region, having clean `total_revenue` and `order_count` columns
- **b)** A Series with the sum of `amount` per region
- **c)** A Python syntax error because `agg()` does not accept keyword arguments
- **d)** An unaltered DataFrame with two calculated columns appended at the end

---

#### **Q11. (Session 8 — Joins / Merges)**
You have an `orders` DataFrame with a `customer` column and a `customers` DataFrame with a `name` column. Which merge keeps **all** orders even if a customer record is missing?
- **a)** `pd.merge(orders, customers, left_on='customer', right_on='name', how='inner')`
- **b)** `pd.merge(orders, customers, left_on='customer', right_on='name', how='left')`
- **c)** `pd.merge(orders, customers, left_on='customer', right_on='name', how='right')`
- **d)** `pd.merge(orders, customers, on='customer', how='left')`

---

#### **Q12. (Session 8 — Concatenation)**
What does `pd.concat([df1, df2], ignore_index=True)` do?
- **a)** Performs a relational SQL-style inner join on matching columns
- **b)** Vertically stacks rows from `df1` and `df2` and resets the index to `0, 1, 2...`
- **c)** Appends only rows from `df2` that do not exist in `df1`
- **d)** Joins columns horizontally side-by-side

---

#### **Q13. (Session 9 — Dates & Time)**
Which code converts a string date column to datetime and extracts the month number?
- **a)** `df['date'].to_datetime().month`
- **b)** `pd.to_datetime(df['date']).dt.month`
- **c)** `df['date'].strftime('%m')`
- **d)** `datetime.strptime(df['date'], '%Y-%m-%d').month`

---

#### **Q14. (Session 9 — Dates & Time)**
Which `.dt` accessor method returns the day of the week as a full string name (e.g., `"Monday"`)?
- **a)** `df['date'].dt.weekday`
- **b)** `df['date'].dt.day`
- **c)** `df['date'].dt.day_name()`
- **d)** `df['date'].dt.dayofweek`

---

#### **Q15. (Session 10 — ETL Architecture)**
What is the key architectural difference between **ETL** and **ELT**?
- **a)** ETL is faster than ELT
- **b)** In ETL, data is transformed before loading into the destination; in ELT, raw data is loaded first and transformed inside the target warehouse/lakehouse
- **c)** ETL works only on flat files; ELT works only on relational databases
- **d)** ELT is deprecated legacy architecture replaced by modern ETL

---

#### **Q16. (Session 10 — ETL Architecture)**
In pipeline design, why decompose the pipeline into distinct `extract()`, `transform()`, and `load()` functions?
- **a)** Python syntax mandates function separation for I/O operations
- **b)** Each stage can be tested, debugged, monitored, and modified independently
- **c)** Decomposing into functions automatically makes code run multithreaded
- **d)** It is only necessary when interacting with cloud object storage

---

#### **Q17. (Session 11 — APIs)**
After calling `response = requests.get(url)`, which pattern correctly checks for HTTP error codes (like 4xx, 5xx) and parses the response payload as a Python dictionary?
- **a)** `response.check()` followed by `response.text()`
- **b)** `response.raise_for_status()` followed by `response.json()`
- **c)** `response.ok()` followed by `json.loads(response)`
- **d)** `response.validate()` followed by `response.data()`

---

#### **Q18. (Session 11 — APIs)**
An API endpoint responds with HTTP status code `404`. What does this indicate?
- **a)** Request succeeded
- **b)** Server-side unhandled exception
- **c)** Target resource was not found
- **d)** Missing or invalid authentication credentials

---

#### **Q19. (Session 12 — Database Integration)**
Which is the secure, parameterized way to execute an `INSERT` statement in `sqlite3` to prevent SQL injection?
- **a)** `cursor.execute(f"INSERT INTO orders VALUES ('{name}', {qty})")`
- **b)** `cursor.execute("INSERT INTO orders VALUES (?, ?)", (name, qty))`
- **c)** `cursor.execute("INSERT INTO orders VALUES (" + name + ", " + str(qty) + ")")`
- **d)** `cursor.insert('orders', name, qty)`

---

#### **Q20. (Session 12 — Database Integration)**
What does `df.to_sql('orders', conn, if_exists='replace', index=False)` do?
- **a)** Appends DataFrame rows to the existing `orders` table
- **b)** Drops the existing `orders` table (if present), creates a new one, and writes all rows without adding the DataFrame index column
- **c)** Raises an `OperationalError` if the table exists
- **d)** Performs an `UPDATE` on matching primary keys

---

### 🔑 Answer Key & Quick Reference

| Question | Correct Answer | Topic |
| :---: | :---: | :--- |
| **Q1** | **c** | String cleaning & `float()` type conversion |
| **Q2** | **b** | List comprehension filtering (`quantity >= 2` matches Laptop & Keyboard) |
| **Q3** | **c** | Append mode `"a"` keeps previous file contents |
| **Q4** | **c** | `ValueError` catches conversion error; `finally` always runs |
| **Q5** | **b** | `python -m venv .venv` and `pip install -r requirements.txt` |
| **Q6** | **c** | `df.info()` gives schema, non-null count, and memory |
| **Q7** | **b** | `loc` is label/inclusive; `iloc` is integer position/exclusive |
| **Q8** | **b** | Vectorized string accessors `.str.strip().str.lower()` |
| **Q9** | **c** | `errors='coerce'` converts unparseable values to `NaN` |
| **Q10** | **a** | Named aggregations in pandas `groupby().agg()` |
| **Q11** | **b** | Left join preserves all records from the left DataFrame (`orders`) |
| **Q12** | **b** | Vertical row stacking with index reset |
| **Q13** | **b** | `pd.to_datetime()` paired with `.dt.month` |
| **Q14** | **c** | `.dt.day_name()` returns full weekday names (e.g. Monday) |
| **Q15** | **b** | ETL transforms before load; ELT transforms inside storage/warehouse |
| **Q16** | **b** | Modularity allows isolated testing, logging, and reusability |
| **Q17** | **b** | `response.raise_for_status()` + `response.json()` |
| **Q18** | **c** | 404 indicates Not Found |
| **Q19** | **b** | Parameterized query `?` placeholders prevent SQL injection |
| **Q20** | **b** | `if_exists='replace'` recreates table; `index=False` omits index column |

The interactive notebook [Final_Quiz_Sessions_1_to_12.ipynb](file:///c:/Users/rupal/.gemini/antigravity/scratch/pythonfordata/Final_Quiz_Sessions_1_to_12.ipynb) includes answer cells for learners to enter their answers (`answer_1 = "c"`, etc.) and an interactive scoring script at the end that calculates their percentage score with feedback!



Here are **10 additional multiple-choice questions specifically covering Session 12 (Database Integration)**. 

They test key topics taught in Session 12: connection lifecycles, cursors, commit vs rollback, `executemany()`, query fetching (`fetchone`, `fetchall`), reading/writing with Pandas (`read_sql`), and schema inspection.

---

### **Q1. Connection & Cursor Roles**
In the standard Python `sqlite3` pattern, what is the specific role of the `cursor` object?
```python
conn = sqlite3.connect("data/pipeline.db")
cursor = conn.cursor()
```
- **a)** It establishes the network connection to the database file  
- **b)** It executes SQL statements and acts as a pointer to fetch result rows  
- **c)** It automatically commits every transaction without calling `conn.commit()`  
- **d)** It closes the database connection when done  

---

### **Q2. Committing Transactions**
You run an `INSERT` statement via Python, but when you inspect the database later, the new rows are not there. What line of code was most likely missing?
```python
cursor.execute("INSERT INTO orders VALUES (101, 'Laptop', 999.99)")
# ???
conn.close()
```
- **a)** `cursor.fetchall()`  
- **b)** `conn.commit()`  
- **c)** `cursor.reset()`  
- **d)** `conn.save()`  

---

### **Q3. Bulk Inserts with `executemany`**
You have a list of 1,000 tuples to insert into a table. What is the most efficient and standard method to use instead of a `for` loop of individual `execute()` calls?
- **a)** `cursor.execute_batch(sql, data)`  
- **b)** `cursor.insert_many(sql, data)`  
- **c)** `cursor.executemany(sql, data)`  
- **d)** `cursor.execute_all(sql, data)`  

---

### **Q4. Fetching Query Results**
What is the return type of `cursor.fetchall()` after executing a `SELECT` statement?
- **a)** A Pandas DataFrame  
- **b)** A dictionary where keys are column names  
- **c)** A list of tuples, where each tuple represents one row  
- **d)** A single comma-separated string  

---

### **Q5. Fetching a Single Row / Scalar**
What does `cursor.fetchone()` return if no rows match the query?
```python
cursor.execute("SELECT * FROM orders WHERE order_id = 99999")
result = cursor.fetchone()
```
- **a)** `None`  
- **b)** An empty tuple `()`  
- **c)** Raises an `IndexError`  
- **d)** Raises a `NoSuchRowError`  

---

### **Q6. Reading SQL into Pandas with Parameters**
Which is the correct syntax to query a database directly into a Pandas DataFrame using parameter placeholders?
- **a)** `pd.read_sql("SELECT * FROM orders WHERE region = ?", conn, params=['north'])`  
- **b)** `pd.read_sql("SELECT * FROM orders WHERE region = 'north'", cursor)`  
- **c)** `pd.read_sql_query("SELECT * FROM orders", conn, where={'region': 'north'})`  
- **d)** `pd.from_db("orders", conn, filter="region == 'north'")`  

---

### **Q7. The `if_exists` parameter in `to_sql()`**
You want to insert new daily records into an existing table named `daily_sales` without wiping out historical records. What should `if_exists` be set to?
```python
df.to_sql('daily_sales', conn, if_exists=???, index=False)
```
- **a)** `if_exists='extend'`  
- **b)** `if_exists='update'`  
- **c)** `if_exists='append'`  
- **d)** `if_exists='insert'`  

---

### **Q8. Database Table Inspection**
In SQLite, how do you query the system catalog to list all user tables in the database?
- **a)** `SELECT * FROM sys.tables`  
- **b)** `SHOW TABLES`  
- **c)** `SELECT name FROM sqlite_master WHERE type='table'`  
- **d)** `SELECT table_name FROM information_schema.tables`  

---

### **Q9. Transaction Rollback on Failure**
In a production pipeline, how should database operations be wrapped to ensure partial writes are discarded if an error occurs mid-pipeline?
```python
try:
    cursor.execute("INSERT INTO orders ...")
    cursor.execute("UPDATE inventory ...")
    conn.commit()
except Exception as e:
    # ???
    raise e
```
- **a)** `conn.rollback()`  
- **b)** `conn.revert()`  
- **c)** `cursor.undo()`  
- **d)** `conn.close(force=True)`  

---

### **Q10. Closing Connections with Context Managers**
What is the advantage of using SQLite connection with Python's `with` statement?
```python
with sqlite3.connect("data/pipeline.db") as conn:
    cursor = conn.cursor()
    cursor.execute("INSERT INTO orders VALUES (?, ?, ?)", order_data)
```
- **a)** It automatically runs `cursor.fetchall()`  
- **b)** It automatically manages transactions: commits on success and rolls back if an exception is raised  
- **c)** It prevents other programs from reading the SQLite database file permanently  
- **d)** It automatically converts SQL results into Pandas DataFrames  

---

### 🔑 Answer Key & Explanations

| Question | Correct Answer | Explanation |
| :---: | :---: | :--- |
| **Q1** | **b** | The connection maintains the link to the DB; the `cursor` handles SQL statement execution, traversal, and row fetching. |
| **Q2** | **b** | DML operations (`INSERT`, `UPDATE`, `DELETE`) start a transaction; you must call `conn.commit()` to persist changes to disk. |
| **Q3** | **c** | `executemany(sql, seq_of_params)` prepares the statement once and executes it across all tuples efficiently. |
| **Q4** | **c** | By default, standard SQLite cursors return rows as a list of tuples `[(col1, col2), (col1, col2), ...]`. |
| **Q5** | **a** | When no rows are returned or when all rows have been exhausted, `cursor.fetchone()` returns `None`. |
| **Q6** | **a** | `pd.read_sql(sql, conn, params=...)` supports parameterized queries, protecting against injection and type errors. |
| **Q7** | **c** | `if_exists='append'` inserts new rows into the existing table. (`'replace'` drops/recreates; `'fail'` raises a `ValueError`). |
| **Q8** | **c** | SQLite keeps metadata in the `sqlite_master` (or `sqlite_schema`) table where `type='table'`. |
| **Q9** | **a** | Calling `conn.rollback()` restores the database state to the start of the current transaction, preventing partial/corrupt loads. |
| **Q10** | **b** | In Python's `sqlite3`, `with conn:` provides transaction management (commit on normal exit, rollback on exception). |