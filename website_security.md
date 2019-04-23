## Add Security for your Website
- There are many ways that you can use to protect your websites from. Here I am listing few of them

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