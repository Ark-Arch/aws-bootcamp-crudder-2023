# Week 1 — App Containerization

*I just learnt about CORS

Cross-Origin Resource Sharing (An API security practice)
- this is a security feature implemented by web browsers to prevent malicious websites from making unauthorized requests to another site.

- it restricts how resources on a web page can be requested from another domain.

- By default, web applications are limited to interacting with resources from the same origin (same domain, protocol, and port).
-> So when my application serves an API that should be accessible from different domains, CORS is needed.


flask-cors is python extension for handling Cross-Origin Resource Sharing in Flask applications.

key-words with CORS
- origin requests.
-> the solution to a CORS error is on the server. i have to be able to control the server
- that is how i can include headers (or preflight the headers)