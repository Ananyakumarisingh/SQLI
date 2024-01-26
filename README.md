# SQLI
SQLI also know as sql injections 

## What's that?
SQL injection is an aatack that occurs when untrusted data is used to construct an sql query the data is inserted or injectedinto the sql query string.
It allows an attacker to execute arbitrary requests to an sql database.
It is not the only code injection form but the most common one.
It is the top security threat to web applications.
It's easy for attackers to detect and exploit.

Know more about sqli with some [examples](sql-injections.md).

## Solutions to SQL Injection
- Limit the application's database privileges
- Limit permission to create, drop, or truncate tables
- Don't grant access privileges to database users
- Never let the application connect as the root user
- Sanitize the input

## SQL Sanitization
Render every single qoute in the data harmless by putting a backslach in front of it.

## Use SQL prepared statements
- Data must match a specified datat type
- Data can't interfere [more..](preparedstatement.md)
- Use allow-lists to validate data before using it in a query.
