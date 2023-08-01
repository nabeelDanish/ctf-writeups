# Lab: Basic SSRF against another back-end system

## Steps:

1. Navigate to the product details page and turn the interceptor on
2. Click on check stock button, you will see that the intercepted request has api url being sent
3. Open burpsuite, make the request for fetching stock information, and intercept it
4. You will see that there is a URL parameter callede apiUrl
5. We already know that the /admin port is internal, but we don't know the exact IP address
6. Change the URL to `http://192.168.1.1:8080/admin` if this returns a response 200, than this is the IP address
7. We need to iterate over these IP addresses to find the correct one. Use the Intruder tool and set the payload as
```
http://192.168.0.§1§:8080/admin
```
where `§1§` is a payload that we will iterate on

8. Change the payload type to number, and specify the range from `1` to `255`
9. Run the attack, look for a request that has a response status of `200`
10. Found the correct URL at `http://192.168.0.107:8080/admin`
11. Use the URL to get a response on the webpage, and you will see the HTML for admin panel
12. Click on the `delete carlos` button to get the URL for delete request
13. The correct URL will be
```
http://192.168.0.107:8080/admin/delete?username=carlos
```
14. Use this URL and redo step 11 to delete carlos