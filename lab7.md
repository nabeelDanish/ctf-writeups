# Lab: Basic SSRF against the local server

## Steps:

1. Navigate to the product details page and turn the interceptor on
2. Click on check stock button, you will see that the intercepted request has api url being sent
3. Replace the url with `http://localhost/admin` and see that it returns the admin panel
4. Click on delete carlos button and observe the request being made. It will go to 
```
http://localhost/admin/delete?username=carlos
```
5. This request will fail, since it is not server side request forgery. Redo Step 2, this time, replace the URL with
```
http://localhost/admin/delete?username=carlos
```
6. The response will say could not fetch stock information
7. Redo step 2 and 3 and you will see that carlos is now deleted