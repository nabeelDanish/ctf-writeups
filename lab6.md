# Lab: User ID controlled by request parameter with data leakage in redirect

## Steps:

1. Login with the credentials
2. See that the id is supplied in the query parameters
3. Go to Home Page and turn the interceptor on
4. Click on 'My Account', this will create a request for getting user data
5. Change the id in the query paramter from `wiener` to `carlos`
6. Forward the request, and check its response in the HTTP Response (A new request will be generated almost instantly since the last one failed and redirected the request to `/login`)
7. In the body of the HTML you will find the `carlos` API key