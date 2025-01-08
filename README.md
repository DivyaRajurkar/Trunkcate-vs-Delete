# Trunkcate-vs-Delete


Here are the key differences between the **`DELETE`** and **`TRUNCATE`** statements in SQL:

| **Aspect**                | **`DELETE`**                                                   | **`TRUNCATE`**                                               |
|---------------------------|---------------------------------------------------------------|------------------------------------------------------------|
| **Operation Type**        | DML (Data Manipulation Language)                               | DDL (Data Definition Language)                             |
| **Functionality**         | Removes specific rows from a table based on a condition.       | Removes all rows from a table.                             |
| **Condition**             | Can include a `WHERE` clause to specify which rows to delete.  | Does not support a `WHERE` clause; deletes all rows.       |
| **Transaction Rollback**  | Supports transactions; can be rolled back using `ROLLBACK`.    | Generally cannot be rolled back (depends on the DBMS).     |
| **Performance**           | Slower, as it logs each row deletion in the transaction log.   | Faster, as it does not log individual row deletions.       |
| **Reset Identity**        | Does not reset `IDENTITY` columns by default.                  | Resets `IDENTITY` columns (auto-increment values).         |
| **Triggers**              | Triggers are fired for deleted rows.                          | Triggers are not fired because it bypasses them.           |
| **Locking**               | Acquires row-level locks on the table.                        | Acquires a schema-level lock; table structure is locked.   |
| **Use Case**              | When you want to selectively delete rows or use triggers.     | When you need to quickly remove all rows and reset the table. |

### Example:

1. **DELETE:**
   ```sql
   DELETE FROM employees WHERE department = 'HR';
   ```
   Deletes rows where the department is "HR".

2. **TRUNCATE:**
   ```sql
   TRUNCATE TABLE employees;
   ```
   Removes all rows from the `employees` table.

### Choosing Between `DELETE` and `TRUNCATE`:
- Use **`DELETE`** when:
  - You need to delete specific rows.
  - You need triggers to fire.
  - You want the ability to roll back the operation.

- Use **`TRUNCATE`** when:
  - You need to remove all rows quickly.
  - You don’t need to log individual row deletions.
  - Resetting the `IDENTITY` column is required.
