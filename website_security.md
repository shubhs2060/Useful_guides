## Add Security for your Website
- There are many ways that you can use to protect your websites from attackers. Here I am listing few of them here

- **noSniff MimeType**

* MIME types are a way of determining what kind of file you’re looking at. PNG images have the type image/png; JSON files are application/json; JavaScript files are typically text/javascript. When your browser loads a file, it reads the server’s Content-Type header to determine what the thing is.
  

* Suppose at the time of uploading a file you want your user to upload jpeg files for image . But some user added js in a file and change its extension to jpeg and uploaded to your system . And when you go to check that image the js in that file gets executed which could contain malicious JavaScript! Perhaps the nastiest attack is called Rosetta Flash, which allows someone to load a malicious Flash plugin instead of data! 

* Solution to this

    The X-Content-Type-Options header tells browsers not to sniff MIME types. When this header is set to nosniff, browsers won’t sniff the MIME type—they will trust what the server says and block the resource if it’s wrong.
  
* Use it like this

  ```
  # prevent mime based attacks
    Header set X-Content-Type-Options "nosniff"
  ```

- **Clickjacking**

* Clickjacking is a malicious technique of tricking a user into clicking on something different from what the user perceives, thus potentially revealing confidential information or allowing others to take control of their computer while clicking on seemingly innocuous objects, including web pages

* Thus if a attacker add your website in an iframe and add it on his websites then you could be getting unwanted clicks on your application and can result in overloading.

* To protect your application from this you can use X-Frame-Options in your headers
The X-Frame-Options header tells browsers to prevent your webpage from being put in an iframe. When browsers load iframes, they’ll check the value of the X-Frame-Options header and abort loading if it’s not allowed.

- The header has three options:

* X-Frame-Options: DENY will prevent anyone from putting this page in an iframe.

* X-Frame-Options: SAMEORIGIN will prevent anyone from putting this page in an iframe unless it’s on the same origin. That generally means that you can put your own pages in iframes, but nobody else can.

* X-Frame-Options: ALLOW-FROM http://test.com will allow http://test.com to put your page in an iframe, but nobody else. (Currently, you can only allow one domain.)

* Use it like this

  ```
  # prevent from loading in iframes
    Header set X-Frame-Options "DENY"
  ```
