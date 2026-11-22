# Python for Data Engineering — Test Question Bank

## Sessions 01–12

> **Instructions:** This question bank contains **28 questions** organized by session. Select 20 for the final test. Each question is tagged with its difficulty level (**Easy** or **Medium**). Questions are numbered sequentially across sessions.

---

## Sessions 01–04: Python Foundations (5 Questions)

---

### Session 01 — Python Basics for Data Engineering

**1. Which of the following data types is immutable in Python?** *(Easy)*

- A) `list`
- B) `dict`
- C) `set`
- D) `tuple`

<details><summary>Answer</summary>D — Tuples are ordered, immutable collections. Once created, their elements cannot be changed.</details>

---

**2. What does the following code print?** *(Easy)*

```python
data = {"name": "Alice", "age": 30, "city": "Prague"}
print(data.get("country", "Unknown"))
```

- A) `None`
- B) `KeyError`
- C) `"Unknown"`
- D) `"country"`

<details><summary>Answer</summary>C — The `.get()` method returns the default value `"Unknown"` when the key `"country"` does not exist in the dictionary, instead of raising a `KeyError`.</details>

---

### Session 02 — Control Flow and Functions

**3. What is the output of the following code?** *(Easy)*

```python
numbers = [1, 2, 3, 4, 5, 6]
result = [x ** 2 for x in numbers if x % 2 == 0]
print(result)
```

- A) `[1, 4, 9, 16, 25, 36]`
- B) `[4, 16, 36]`
- C) `[2, 4, 6]`
- D) `[1, 9, 25]`

<details><summary>Answer</summary>B — The list comprehension filters even numbers (`x % 2 == 0`) and squares them. Even numbers are 2, 4, 6 → 4, 16, 36.</details>

---

**4. What is the purpose of `*args` and `**kwargs` in a Python function definition?** *(Medium)*

- A) `*args` accepts keyword arguments; `**kwargs` accepts positional arguments
- B) `*args` accepts a variable number of positional arguments as a tuple; `**kwargs` accepts a variable number of keyword arguments as a dictionary
- C) Both are used to restrict the number of arguments a function can receive
- D) `*args` accepts a list; `**kwargs` accepts a set

<details><summary>Answer</summary>B — `*args` collects extra positional arguments into a tuple, while `**kwargs` collects extra keyword arguments into a dictionary. They allow functions to accept flexible numbers of arguments.</details>

---

### Session 03 — File Handling and Logging

**5. Which of the following correctly reads a CSV file so that each row is returned as a dictionary with column headers as keys?** *(Easy)*

- A) `csv.reader(file)`
- B) `csv.DictReader(file)`
- C) `csv.DictWriter(file)`
- D) `json.load(file)`

<details><summary>Answer</summary>B — `csv.DictReader()` reads each row as a dictionary where the keys are taken from the header row of the CSV file.</details>

---

## Sessions 05–12: Libraries, Pandas & Data Engineering (23 Questions)

---

### Session 05 — Working with Libraries

**6. What does `defaultdict(list)` do when you access a key that does not exist?** *(Easy)*

- A) Raises a `KeyError`
- B) Returns `None`
- C) Automatically creates the key with an empty list as the default value
- D) Returns `0`

<details><summary>Answer</summary>C — A `defaultdict(list)` automatically creates a missing key with an empty list (`[]`) as its default value, so you can directly append to it without first checking if the key exists.</details>

---

**7. Which `itertools` function would you use to chain multiple lists into a single iterable without creating a new list in memory?** *(Easy)*

- A) `itertools.product()`
- B) `itertools.chain()`
- C) `itertools.cycle()`
- D) `itertools.combinations()`

<details><summary>Answer</summary>B — `itertools.chain()` takes multiple iterables and chains them together into a single iterable, yielding elements one by one without creating a combined list in memory.</details>

---

**8. What does `functools.lru_cache` do?** *(Medium)*

- A) Limits the number of times a function can be called
- B) Caches (memoizes) function results so that repeated calls with the same arguments return the cached result instead of recomputing
- C) Converts a function into a generator
- D) Sorts the results of a function call

<details><summary>Answer</summary>B — `lru_cache` is a decorator that caches function results (memoization). When the function is called again with the same arguments, the cached result is returned instantly without re-executing the function.</details>

---

### Session 06 — Pandas Fundamentals

**9. What is the difference between `.loc[]` and `.iloc[]` in Pandas?** *(Easy)*

- A) `.loc[]` uses integer positions; `.iloc[]` uses labels
- B) `.loc[]` uses labels (names); `.iloc[]` uses integer positions
- C) Both use integer positions
- D) Both use labels

<details><summary>Answer</summary>B — `.loc[]` is label-based selection (uses row/column names), while `.iloc[]` is integer position-based selection (uses numeric indices starting from 0).</details>

---

**10. Given the following DataFrame, what does `df[df['age'] > 25]` return?** *(Easy)*

```python
df = pd.DataFrame({
    'name': ['Alice', 'Bob', 'Charlie'],
    'age': [22, 30, 27]
})
```

- A) All rows
- B) Only the rows where `age` is greater than 25 (Bob and Charlie)
- C) Only the `age` column
- D) A single value

<details><summary>Answer</summary>B — Boolean filtering `df[df['age'] > 25]` returns a DataFrame containing only the rows where the condition is `True`: Bob (30) and Charlie (27).</details>

---

**11. Which Pandas method would you use to find the 3 highest values in a column called `"salary"`?** *(Easy)*

- A) `df.sort_values('salary').head(3)`
- B) `df['salary'].max(3)`
- C) `df.nlargest(3, 'salary')`
- D) `df['salary'].top(3)`

<details><summary>Answer</summary>C — `.nlargest(n, column)` returns the top `n` rows with the largest values in the specified column. Option A would return the 3 *lowest* values since `sort_values` defaults to ascending order.</details>

---

### Session 07 — Data Cleaning with Pandas

**12. What does `df.isnull().sum()` return?** *(Easy)*

- A) The total number of rows in the DataFrame
- B) The count of missing (`NaN`) values in each column
- C) `True` or `False` for each cell
- D) The percentage of missing values

<details><summary>Answer</summary>B — `df.isnull()` returns a DataFrame of booleans (`True` for `NaN`), and `.sum()` counts the `True` values in each column, giving the number of missing values per column.</details>

---

**13. Which method would you use to replace all missing values in a column with the column's median?** *(Easy)*

- A) `df['col'].dropna()`
- B) `df['col'].fillna(df['col'].median())`
- C) `df['col'].replace(None, 'median')`
- D) `df['col'].isnull().median()`

<details><summary>Answer</summary>B — `.fillna(value)` replaces `NaN` values with the specified value. Passing `df['col'].median()` fills missing values with the column's median.</details>

---

**14. In the IQR method for outlier detection, a data point is considered an outlier if it falls:** *(Medium)*

- A) More than 1 standard deviation from the mean
- B) Below Q1 − 1.5 × IQR or above Q3 + 1.5 × IQR
- C) Outside the range of the minimum and maximum values
- D) Below the median

<details><summary>Answer</summary>B — The IQR (Interquartile Range) method defines outliers as values below Q1 − 1.5 × IQR or above Q3 + 1.5 × IQR, where IQR = Q3 − Q1.</details>

---

**15. What does `pd.to_numeric(series, errors='coerce')` do when it encounters a non-numeric value?** *(Easy)*

- A) Raises a `ValueError`
- B) Skips the value entirely
- C) Converts the non-numeric value to `NaN`
- D) Converts it to `0`

<details><summary>Answer</summary>C — With `errors='coerce'`, `pd.to_numeric()` converts values that cannot be parsed as numbers into `NaN` instead of raising an error.</details>

---

**16. What is the main advantage of using the `category` dtype in Pandas?** *(Easy)*

- A) It makes columns immutable
- B) It speeds up sorting but increases memory usage
- C) It reduces memory usage for columns with a limited number of unique values
- D) It automatically removes duplicate values

<details><summary>Answer</summary>C — The `category` dtype stores data more efficiently by mapping values to integer codes internally. This is especially beneficial when a column has few unique values relative to its length.</details>

---

### Session 08 — Data Aggregation and Joins

**17. The GroupBy pattern in Pandas follows which three-step approach?** *(Easy)*

- A) Filter → Sort → Aggregate
- B) Split → Apply → Combine
- C) Extract → Transform → Load
- D) Read → Process → Write

<details><summary>Answer</summary>B — The GroupBy pattern follows **Split-Apply-Combine**: split the data into groups, apply a function to each group, and combine the results back together.</details>

---

**18. What type of join keeps all rows from the left DataFrame and only matching rows from the right DataFrame?** *(Easy)*

- A) `inner`
- B) `outer`
- C) `left`
- D) `right`

<details><summary>Answer</summary>C — A `left` join keeps all rows from the left DataFrame. Where there is no match in the right DataFrame, the result will contain `NaN` for the right DataFrame's columns.</details>

---

**19. What does the `indicator=True` parameter do in `pd.merge()`?** *(Medium)*

- A) It adds an index column to the result
- B) It adds a `_merge` column showing whether each row came from the left, right, or both DataFrames
- C) It prints a summary of the merge operation
- D) It validates that the merge keys are unique

<details><summary>Answer</summary>B — When `indicator=True`, Pandas adds a `_merge` column to the result with values `"left_only"`, `"right_only"`, or `"both"`, showing the source of each row.</details>

---

**20. What is the difference between `.agg()` and `.transform()` in a GroupBy operation?** *(Medium)*

- A) `.agg()` returns a result with the same shape as the original; `.transform()` returns a reduced result
- B) `.agg()` returns a reduced/aggregated result (one row per group); `.transform()` returns a Series with the same index as the original DataFrame
- C) They are identical
- D) `.transform()` can only be used with numeric data

<details><summary>Answer</summary>B — `.agg()` reduces each group to a single value (e.g., sum, mean), resulting in one row per group. `.transform()` applies a function to each group but broadcasts the result back to match the original DataFrame's index, so the output has the same number of rows as the input.</details>

---

### Session 09 — Working with Dates and Time

**21. What is the difference between `strftime()` and `strptime()`?** *(Easy)*

- A) `strftime()` parses a string into a datetime; `strptime()` formats a datetime into a string
- B) `strftime()` formats a datetime object into a string; `strptime()` parses a string into a datetime object
- C) Both convert strings to datetime objects
- D) Both format datetime objects into strings

<details><summary>Answer</summary>B — `strftime` = **string format time** (datetime → string). `strptime` = **string parse time** (string → datetime).</details>

---

**22. What is the recommended best practice for storing timestamps in a data pipeline that handles data from multiple time zones?** *(Easy)*

- A) Store in the local time zone of the data source
- B) Store in UTC and convert to local time only for display
- C) Store without any time zone information
- D) Store in the server's local time zone

<details><summary>Answer</summary>B — Storing timestamps in UTC is the standard best practice for global data pipelines. Converting to local time zones should only happen at the display/presentation layer.</details>

---

**23. Which Pandas method is used for time-based grouping (e.g., aggregating daily data to monthly)?** *(Easy)*

- A) `.groupby()`
- B) `.resample()`
- C) `.rolling()`
- D) `.pivot_table()`

<details><summary>Answer</summary>B — `.resample()` is a time-based groupby method. For example, `.resample('M').sum()` groups data by month and sums the values. It requires a DatetimeIndex or a datetime column specified via `on=`.</details>

---

### Session 10 — ETL Pipeline Design

**24. What does "idempotency" mean in the context of ETL pipeline design?** *(Medium)*

- A) The pipeline runs only once and cannot be restarted
- B) Running the pipeline multiple times produces the same result as running it once
- C) The pipeline automatically retries on failure
- D) Each step in the pipeline runs in parallel

<details><summary>Answer</summary>B — An idempotent pipeline produces the same result regardless of how many times it is run. This is a key design principle that ensures reliability — if a pipeline fails and is re-run, it won't create duplicates or inconsistencies.</details>

---

**25. In an ETL pipeline, which approach correctly describes the difference between ETL and ELT?** *(Easy)*

- A) ETL and ELT are the same thing
- B) In ETL, data is transformed before loading to the destination; in ELT, raw data is loaded first and then transformed in the destination
- C) In ETL, data is loaded first; in ELT, data is transformed first
- D) ELT is an older approach; ETL is the modern cloud-native approach

<details><summary>Answer</summary>B — ETL (Extract-Transform-Load) transforms data before loading it. ELT (Extract-Load-Transform) loads raw data first and performs transformations in the destination system (common with modern cloud data warehouses).</details>

---

### Session 11 — Working with APIs

**26. Which HTTP status code indicates that you have exceeded the API's rate limit?** *(Easy)*

- A) 401
- B) 404
- C) 429
- D) 500

<details><summary>Answer</summary>C — HTTP status code 429 means "Too Many Requests" and indicates that the client has sent too many requests in a given time period (rate limit exceeded).</details>

---

**27. Why should you never hardcode API keys directly in your Python source code?** *(Easy)*

- A) It makes the code run slower
- B) Python does not support string constants
- C) It is a security risk — keys may be exposed if the code is shared or committed to version control; use environment variables instead
- D) API keys cannot be stored as strings

<details><summary>Answer</summary>C — Hardcoding API keys is a security vulnerability. If the code is shared, pushed to a repository, or leaked, the keys are exposed. The best practice is to store them in environment variables and access them with `os.environ.get('API_KEY')`.</details>

---

### Session 12 — Database Integration

**28. What is the primary reason for using parameterized queries (with `?` placeholders) instead of string formatting when constructing SQL queries?** *(Easy)*

- A) Parameterized queries run faster
- B) String formatting is not supported in Python
- C) Parameterized queries prevent **SQL injection** attacks by ensuring user input is treated as data, not executable SQL code
- D) Parameterized queries automatically create database indexes

<details><summary>Answer</summary>C — SQL injection is a security vulnerability where malicious SQL code is inserted through user input. Parameterized queries ensure that input values are always treated as data, never as part of the SQL command, preventing this attack.</details>

---

**29. What does the `if_exists` parameter control in `df.to_sql()`?** *(Easy)*

- A) Whether the connection is kept open
- B) Whether the index is included
- C) What happens if the target table already exists in the database — options are `'fail'`, `'replace'`, or `'append'`
- D) Whether to create a new database file

<details><summary>Answer</summary>C — The `if_exists` parameter determines the behavior when the table already exists: `'fail'` raises an error, `'replace'` drops and recreates the table, and `'append'` adds new rows to the existing table.</details>

---

**30. What does CRUD stand for in the context of database operations?** *(Easy)*

- A) Copy, Rename, Update, Delete
- B) Create, Read, Update, Delete
- C) Connect, Read, Upload, Disconnect
- D) Compile, Run, Undo, Debug

<details><summary>Answer</summary>B — CRUD stands for **Create** (`INSERT`), **Read** (`SELECT`), **Update** (`UPDATE`), and **Delete** (`DELETE`) — the four fundamental operations for managing data in a database.</details>

---

## Summary

| Session Range | Questions | Count |
|:---|:---|:---:|
| Sessions 01–04 (Python Foundations) | Q1 – Q5 | 5 |
| Session 05 (Libraries) | Q6 – Q8 | 3 |
| Session 06 (Pandas Fundamentals) | Q9 – Q11 | 3 |
| Session 07 (Data Cleaning) | Q12 – Q16 | 5 |
| Session 08 (Aggregation & Joins) | Q17 – Q20 | 4 |
| Session 09 (Dates & Time) | Q21 – Q23 | 3 |
| Session 10 (ETL Pipeline Design) | Q24 – Q25 | 2 |
| Session 11 (APIs) | Q26 – Q27 | 2 |
| Session 12 (Database Integration) | Q28 – Q30 | 3 |
| **Total** | | **30** |

### Difficulty Breakdown

| Difficulty | Count |
|:---|:---:|
| Easy | 24 |
| Medium | 6 |
| **Total** | **30** |

