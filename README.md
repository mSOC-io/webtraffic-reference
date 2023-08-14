# webtraffic-reference
This page is dedicated to assisting the community with interpreting web logs

# disclaimer

This page is for informational and educational purposes **only**. Interpretation of data is highly specific to individual organzations and their specific applications. Blocking traffic or declaring an incident should occur only after a proper investigation and vetting of data is performed. 

# data presentation

The data here is presented with a "log entry" in bold (e.g. **GET /robots.txt**) followed by commentary underneath. Again, this is for informational purposes only. 
_________________

# Reference

**\x16\x03\x01**

The string "\x16\x03\x01" is a representation of binary data in hexadecimal format and is commonly associated with the Transport Layer Security (TLS) protocol. It is often seen in logs related to web servers and security incidents.
The string "\x16\x03\x01" is just the start of a TLS 1.0 handshake, i.e. content type (0x16 = handshake) followed by TLS version.
The presence of this string in web server logs may indicate an attempt to exploit a vulnerability in the TLS protocol or to perform a man-in-the-middle attack.
_________________
**GET /robots.txt HTTP/1.1**

A robots.txt file is a text file that is used to instruct web robots (also known as web crawlers or spiders) which pages or sections of a website they are allowed to access and crawl. This is likely not an indicator of attack by itself. 
_________________
**GET /favicon.ico HTTP/1.1**

A favicon.ico is a small icon associated with a particular website or web page that is displayed in the browser's address bar, bookmarks, and tabs. 
It is also known as a shortcut icon, website icon, tab icon, URL icon, or bookmark icon2. A get request for favicon.ico is likely not an indicator of attack by itself. 
_________________
**GET /sendgrid.env HTTP/1.1**

The presence of this request in the log files likely indicates and attempt to GET Sendgrid API Credentials. A request of this nature should generally be considered suspicious unless it is part of some authorized activity. 
https://stackoverflow.com/questions/71330025/how-do-i-implement-sendgrid-env-file
_________________
**GET /actuator/gateway/routes HTTP/1.1**

This request is associated with Spring.io Actuator API and is consistent with a request to GET routes. The documentation for the Actualor API shows this URL described as "To retrieve the routes defined in the gateway, make a GET request to /actuator/gateway/routes." An organization may consider this recon activity or otherwise suspicious. Our review of this in most circumstances is that this is suspicious. 
_________________
**GET /.env**

This is consistent with an attempt to get environmental variables from a server. Likely suspicious and abnormal. 
_________________
**GET /_ignition/execute-solution HTTP/1.1**

This is a HTTP request that is related to the Ignition package in Laravel, a popular PHP web application framework. This is possibly an attacker attempting to exploit Ignition. 
https://stackoverflow.com/questions/58249085/how-to-solve-facade-ignition-http-middleware-ignitionenabled
_________________
**GET /.well-known/security.txt HTTP/1.1**

The "security.txt" file is typically placed in the ".well-known" directory of a website, which is a base directory for "well known" locations defined in RFC 5785.  A well-known URI is a URI [RFC3986] whose path component begins with
the characters "/.well-known/", and whose scheme is "HTTP", "HTTPS", or another scheme that has explicitly been specified to use well-known URIs. The "security.txt" file is designed to be machine- and human-readable, and it can be used by security researchers to easily report security vulnerabilities to website owners. In summary, "GET /.well-known/security.txt" is a HTTP request for a file named "security.txt" that is used to define security policies for a website. The file is typically placed in the ".well-known" directory of a website and contains information about a company's security policy, including a vulnerability disclosure policy, a security point of contact, and additional data.
https://datatracker.ietf.org/doc/html/rfc5785#section-3
