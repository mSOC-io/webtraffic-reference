# webtraffic-reference
This page is dedicated to assisting the community with interpreting web logs

#disclaimer

This page is for informational and educational purposes **only**. 

**\x16\x03\x01**

The string "\x16\x03\x01" is a representation of binary data in hexadecimal format and is commonly associated with the Transport Layer Security (TLS) protocol. It is often seen in logs related to web servers and security incidents.
The string "\x16\x03\x01" is just the start of a TLS 1.0 handshake, i.e. content type (0x16 = handshake) followed by TLS version.
The presence of this string in web server logs may indicate an attempt to exploit a vulnerability in the TLS protocol or to perform a man-in-the-middle attack.

**GET /robots.txt HTTP/1.1**

A robots.txt file is a text file that is used to instruct web robots (also known as web crawlers or spiders) which pages or sections of a website they are allowed to access and crawl. This is likely not an indicator of attack by itself. 

**GET /favicon.ico HTTP/1.1**

A favicon.ico is a small icon associated with a particular website or web page that is displayed in the browser's address bar, bookmarks, and tabs. 
It is also known as a shortcut icon, website icon, tab icon, URL icon, or bookmark icon2. A get request for favicon.ico is likely not an indicator of attack by itself. 


