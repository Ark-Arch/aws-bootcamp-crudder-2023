CORS - Cross Origin Resource Sharing

A classic CORS error:
3000-arkarch-awsbootcampcrud-7wqwt8ubprp.ws-eu115.gitpod.io/:1 Access to fetch at 'https://4567-arkarch-awsbootcampcrud-7wqwt8ubprp.ws-eu115.gitpod.io/api/activities/home' from origin 'https://3000-arkarch-awsbootcampcrud-7wqwt8ubprp.ws-eu115.gitpod.io' has been blocked by CORS policy: No 'Access-Control-Allow-Origin' header is present on the requested resource. If an opaque response serves your needs, set the request's mode to 'no-cors' to fetch the resource with CORS disabled.

WHAT THE PROBLEM MEANS:
1. That my frontend is running at:
https://3000-arkarch-awsbootcampcrud-7wqwt8ubprp.ws-eu115.gitpod.io
2. my backend is running at:
https://4567-arkarch-awsbootcampcrud-7wqwt8ubprp.ws-eu115.gitpod.io

3. The browser is blocking a cross-origin request since the backend server is not returning the appropriate CORS headers!

*because these origins are different (in that they have different ports), the browser treats the requests to the backend as a cross-origin request. 

By default, browsers enforce strict security rules and block such requests unless the backend seerver explicitly allows them by returning the 'Access-Control-Allow-Origin' header.


HOW TO FIX THE CORS ISSUE
1. enable CORS in the backend!. example flask-cors

2. ensure that the request mode is not set to no-cors. 
    setting it to no-cors will prevent me from reading the response due to it being "opaque", and it won't solve the CORS issue.

3. ensure backend allows requests from the correct origin.
    frontend origin.
    CHECK YOUR PREFLIGHT REQUESTS.
        ensure server is set up to handle preflight requests.

4. AND SOMETIMES, YOUR BACKEND PORT MIGHT JUST NOT BE PUBLICLY AVAILABLE!!!!!