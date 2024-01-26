```sql
SET @sql = "SELET * FROM articles WHERE title = ?"; -- ? indicates a placeholder for dynamic data
PREPARE stmt FROM @sql; -- converting it into a prepared statement
EXECUTE stmt USING @query; -- adds a value as input and executes the statement
```
