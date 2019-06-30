Questions\
**1. What is the difference between HTTP and HTTPS?**\
  ANSWER: HTTP stands for Hypertext Transfer Protocol and in HTTPS the 'S' in the end stands for 'Secure'. So, transfering data using HTTPS is more secure.

**2. What is the difference between HTTP GET and POST?**\
  ANSWER: GET request fetches some data from the server, while post request sends some data to the server (for example, data from the form that user filled it)

**3. What is the difference between the HTTP 2xx status codes and 4xx status codes?**\
  ANSWER: Response header with 2xx status code means that there are no mistakes. Response with 4xx status code means that there was some error (for example, 404 'Not Found')

**4. What is ajax (conceptually, what does it do)? Discribe a situation where it is useful.**\
  ANSWER: AJAX stands for Asynchronous Javascript. Ajax requests are usually requests to the server-side or to some external API. Those requests are executed in the end of the event loop. The best way to work with Ajax requests is utilizing Promises. Ajax requests take quite a long time to execute (compared to requests to, for example, cache or hard drive), so it is a good practice to display a loading ring when waiting for the response by utilizing promises.

**5. What is responsive design?**\
  ANSWER: Responsive design means that the app works on any screen size.

**6. What is the difference between these 3 CSS rules?**\
  Set the background color on a 'div' element\
  div{background: #fff}\
  Set the background color on an element with an id="div"\
  #div{background: #fff}\
  Set the background color on an element with a class="div"\
  .div{background: #fff}

**7. What is the difference between these 2 uses of the <script> tag?**\
  Load Javascript from external file:\
  ```<script src="http://example.com/whatever.js></script>```

  Write Javascript inside HTML file:\
  ```<script>var whatever = true</script>```

  **8. What is the difference between these two javascript snippets?**\
    In this case function executes and returns value 2, that is assigned to variable x:
    ```var x=function(){return 1+1;}();```

    This is a function expression:
    ```var y=function(){return 1+1;}```

    **PRACTICAL:**\

    **1. Write HTML/CSS to draw the following scene:**\


  ```
    <!DOCTYPE html>
    <html lang="en">
    <head>
      <meta charset="UTF-8">
      <meta name="viewport" content="width=<device-width>, initial-scale=1.0">
      <meta http-equiv="X-UA-Compatible" content="ie=edge">
      <title>Document</title>
      <style>
        #red, #blue {
          width: 200px;
          height: 200px;
        }

        #red {
          background-color: red;

          display: flex;
          justify-content: center;
          align-items: center;
        }

        #blue {
          background-color: blue;
        }

        #green {
          width: 100px;
          height: 100px;
          background-color: green;
        }
      </style>
    </head>
    <body>
      <div id="red">
        <div id="green"></div>
      </div>
      <div id="blue"></div>

    </body>
    </html>
```

**2. You have started analytics company with the domain“hashtag­-analytics.com.You provide this tracking pixel for your customers to place on their websites.By summing the number of times the pixel was loaded,you calculate the number of visitors to each site.\
As it stands,this pixel has a problem because it will be cached by the browser.
**a.Why is caching a problem for the analytics company?**\
  ANSWER: Because if the pixel is cached, the analytics company will no longer know how many times it was loaded (because the browser loads cache first)

**b.How could you prevent browser caching?(use any technique(s)you want)**\
  ANSWER: (source: https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/http-caching)
  Caching policy is defined via the Cache-Control HTTP header. If you set it to 'no-store', that prevents the resource from being cached. This is the best option.
  Another option is to change the filename of the image (for example, embed a version number of the file) and force the user to download a new image.

**c.What will happen if the customer’s website is served over HTTPS?**\
  ANSWER: (https://www.admonsters.com/pixel-delivery-best-practices/)\
  The tracking pixel will most likely not be sent.\
  **How could you modify the tracking pixel to fix that?**\
  ANSWER: <img src=”https://hashtag­analytics.com/12345/pixel.gif” width=”1” height=”1”/>\
  Or some logic to construct 'src' attribute can be implemented based on value of location.protocol

**d.List some information the tracking company could collect (ex:IPaddress)**
  ANSWER: (source: https://en.ryte.com/wiki/Tracking_Pixel)\
  - Operating system used (gives information on the use of mobile devices)\
  - Type of website or email used, for example on mobile or desktop\
  - Type of client used, for example a browser or mail program.\
  - Client’s screen resolution\
  - Time the email was read or website was visited\
  - Activities on the website during a session (when using multiple tracking pixels)\
**e.List some additional information(if any)that could be collected if a <script> tag is used instead of an <img> tag.**
  the screen resolution, plugins used, support of certain technologies by the browser, etc.


3. Harder!\
  The following image tag appears somewhere on some webpage.The rest of the page is valid HTML, but otherwise unknown.\
  ```<img id=”myimage” src=”​http://hashtag­analytics.com/myimage.jpg​” width=”300”height=”250”/>```
  Write CODE in plain javascript to do the following (jQuery is fine too,if you prefer):Every 2 seconds:­Check whether the image is viewable\
  **­If yes, write “visible” to the console (that is,window.console)­ If no,do nothing.

  ANSWER:
  ```
  <script>
    // function to check if the image is out of viewport (returns 'true' when the image is out of viewport)
    function isImageOutOfViewport (el) {
      var rect = el.getBoundingClientRect();
      // rect.bottom < 0 means the image is above the viewport
      // rect.right < 0 means the image is to the left outside of viewport
      // rect.left > window.innerWidth means an element is to the right outside of viewport
      // rect.top > window.innerHeight means an element is below the viewport
      return rect.bottom < 0 || rect.right < 0 || rect.left > window.innerWidth || rect.top > window.innerHeight;
    }
    // every 2 seconds check if the image is inside the viewport and log "visible" to the console if the image is visible
    setInterval(() => !isImageOutOfViewport(myimage) && console.log("visible"), 2000);

  </script>
  ```

