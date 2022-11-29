# Web Browser

A web browser \(commonly referred to as a browser\) is a software application for accessing information on the World Wide Web. Each individual web page, image, and video is identified by a distinct URL, enabling browsers to retrieve and display them on the user's device.

The most popular web browsers are Chrome, Firefox, Safari, Internet Explorer, and Edge.

### Function

The purpose of a web browser is to fetch information resources and display them on a user's device.

This process begins when the user inputs a URL, such as [https://en.wikipedia.org/](https://en.wikipedia.org/), into the browser. Virtually all URLs on the Web start with either http: or https: which means the browser will retrieve them with the Hypertext Transfer Protocol. In the case of https: the communication between the browser and the web server is encrypted for the purposes of security and privacy. Another URL prefix is file: which is used to display local files already stored on the user's device.

Once a web page has been retrieved, the browser's rendering engine displays it on the user's device. This includes image and video formats supported by the browser. Web pages usually contain hyperlinks to other pages and resources. Each link contains a URL, and when it is clicked, the browser navigates to the new resource. Thus the process of bringing content to the user begins again.

All major browsers allow the user to open multiple pages at the same time, either in different browser windows or in different tabs of the same window. They also support the use of extensions to add to or modify browser operation in a variety of ways.

### Mobile Browsers

A mobile browser is a web browser designed for use on a mobile device such as a mobile phone or PDA. Mobile browsers are optimized so as to display Web content most effectively for small screens on portable devices. Mobile browser software must be small and efficient to accommodate the low memory capacity and low-bandwidth of wireless handheld devices. Typically they were stripped-down web browsers, but some more modern mobile browsers can handle more recent technologies.

The most popular web browsers are Android browser, Chrome, Firefox, Safari, Internet Explorer, UC Browser and Samsung Internet.

### Browser Wars

### Layout Engine/Browser Engine/Rendering Engine

A core software component of every major web browser. The primary job of a browser engine is to transform HTML documents and other resources of a web page into an interactive visual representation on a user's device. A browser engine is not a stand-alone computer program but a critical piece of a larger program.

In addition to layout and rendering, browser engines enforce the security policy between documents and implement the Document Object Model \(DOM\) data structure exposed to page scripts. They also handle hyperlinks and web forms.

Executing JavaScript \(JS\) code is a separate matter, however, as every major web browser uses a dedicated engine for this. The JS language was originally created for use in browsers, but it is now used elsewhere too, so the implementation of JS engines is decoupled from browser engines. In a web browser, the two engines work in concert via the shared DOM data structure.

Browser engines may be used in other types of programs besides web browsers \(just as different types of cars can be manufactured with the same engine\). For example, an email client may need one to display HTML email. The Electron framework, which is powered by the two engines of the Google Chrome browser, has been used to create many applications.

##### Layout and Rendering

The layout of a web page is typically specified by Cascading Style Sheets \(CSS\). Each style sheet is a series of rules which the browser engine interprets. For example, some rules specify typography details, such as font, color, and text size. The engine combines all relevant CSS rules to calculate precise graphical coordinates for the visual representation it will paint on the screen.

Some engines may begin rendering before all of a page's resources are downloaded. This can result in visual changes as more data is received, such as images being gradually filled in or a flash of unstyled content.

##### Rendering Engines

Because the Web platform is an open standard, there are multiple browser engine implementations.

* Trident - used in Internet Explorer, Microsoft Outlook, and other Windows applications. It was developed by Microsoft, who later introduced the EdgeHTML engine for its Edge web browser.
* Gecko - Mozilla project's browser engine, used in its Firefox web browser, the Thunderbird email client, and the SeaMonkey internet suite. Goanna is a fork of Gecko used by the Pale Moon browser.
* WebKit - powers Safari and was the engine originally used in Google Chrome. WebKit began as an Apple-initiated fork of the KHTML engine, which was created by KDE for its Konqueror browser. Google later forked WebKit into the Blink engine, which is now developed independently from WebKit.
  Both WebKit and Blink are used in other browsers. Although Apple permits third-party browsers as alternatives to Safari on iOS devices, all browsers distributed through its App Store use WebKit as their engine.

##### References

```
https://en.wikipedia.org/wiki/Browser_engine
https://en.wikipedia.org/wiki/Blink_(web_engine)
https://en.wikipedia.org/wiki/WebKit
https://en.wikipedia.org/wiki/Gecko_(software)
https://en.wikipedia.org/wiki/Trident_(software)
```

#### JavaScript Engines

A program or interpreter which executes JavaScript code. A JavaScript engine may be a traditional interpreter, or it may utilize just-in-time compilation to bytecode in some manner.

##### Active Projects

* Rhino, managed by the Mozilla Foundation, open source, developed entirely in Java
* SpiderMonkey, the first JavaScript engine, which powered Netscape Navigator and today powers Firefox
* V8 - open source, developed by Google in Denmark, part of Google Chrome and Node.js
* JavaScriptCore - open source, marketed as Nitro and developed by Apple for Safari
* Chakra \(JavaScript\) for Microsoft Edge
* Nashorn, open source as part of OpenJDK, written by Oracle Java Languages and Tool Group
* JerryScript, is an ultra-lightweight JavaScript engine for the Internet of Things.

##### References

```
https://en.wikipedia.org/wiki/JavaScript_engine
https://en.wikipedia.org/wiki/List_of_ECMAScript_engines
https://en.wikipedia.org/wiki/Comparison_of_JavaScript_engines

https://en.wikipedia.org/wiki/Rhino_(JavaScript_engine)
https://en.wikipedia.org/wiki/SpiderMonkey
https://en.wikipedia.org/wiki/Chrome_V8
https://en.wikipedia.org/wiki/WebKit#JavaScriptCore
https://en.wikipedia.org/wiki/Chakra_(JavaScript_engine)
https://en.wikipedia.org/wiki/Nashorn_(JavaScript_engine)
https://en.wikipedia.org/wiki/JerryScript
```

### References

```
https://en.wikipedia.org/wiki/Web_browser
https://en.wikipedia.org/wiki/Mobile_browser
https://en.wikipedia.org/wiki/List_of_web_browsers

Explore
https://en.wikipedia.org/wiki/Web_search_engine
https://en.wikipedia.org/wiki/Browser_wars
https://en.wikipedia.org/wiki/UC_Browser
```



