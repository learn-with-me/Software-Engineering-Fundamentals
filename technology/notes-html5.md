# HTML5

> Facade: An extremely thin layer of abstraction around the native api. It is not a polyfill. Nor does it add functionality on top of existing apis. Main goal is to have thin layer of insulation across the production code.

If you use native api in your code and a breaking change is introduced, you'll have a bunch of places to go and change into, however facade is like a pressure release value. Framework is just a more complex version of facade. They add all kinds of extra stuff into it like polyfills, etc.

##### Persistent Storage API

The API stores some information in the browser.

* Cookies
  ```
  Get and set cookies related to the current document
  ```
* SessionStorage
* ```
  Maintains separate storage area or each given origin that's available for the duration of the page session.
  ```
* LocalStorage
  ```
  Stores data as key-value pair locally on user's browser. Unlike cookie, local storage is persistent. Data will
  always be available even after the browser is closed.
  ```
* 
WebRTC API

WebSockets API

##### Reference

```
http://html5index.org/
https://developer.mozilla.org/en-US/docs/Web
https://developer.mozilla.org/en-US/docs/Web/Guide/HTML/HTML5
https://www.sitepoint.com/10-html5-apis-worth-looking/
https://www.htmlgoodies.com/html5/javascript/a-5-minute-overview-of-all-new-javascript-apis-in-html5.html
```



