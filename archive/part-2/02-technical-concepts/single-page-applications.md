# Single Page Applications

### Approach

Interacts with the user by dynamically rewriting the current page rather than loading entire new pages from a server. This approach avoids interruption of the user experience between successive pages, making the application behave more like a desktop application. SPAs are more application-like because they reject the more typical web paradigm of moving between distinct pages with different URLs. The page does not reload at any point in the process, nor does control transfer to another page, although the location hash or the HTML5 History API can be used to provide the perception and navigability of separate logical pages in the application.

### Frameworks

* Angular.js
* Ember.js
* ExtJS
* Knockout.js
* Meteor.js
* Vue.js
* React
* Fulcro

### Challenges

Because the SPA is an evolution away from the stateless page-redraw model that browsers were originally designed for, some new challenges have emerged. Each of these problems has an effective solution with:

* Client-side JavaScript libraries addressing various issues.
* Server-side web frameworks that specialize in the SPA model.
* The evolution of browsers and the HTML5 specification designed for the SPA model.

##### Search Engine Optimization

Because of the lack of JavaScript execution on crawlers of some popular Web search engines, SEO \(Search engine optimization\) has historically presented a problem for public facing websites wishing to adopt the SPA model. 

Because SEO compatibility is not trivial in SPAs, it is worth noting that SPAs are commonly not used in a context where search engine indexing is either a requirement, or desirable.

...... Add more here

##### Client/Server code partitioning

One way to increase the amount of code that can be shared between servers and clients is to use a logic-less template language like Mustache or Handlebars. Such templates can be rendered from different host languages, such as Ruby on the server and JavaScript in the client. However, merely sharing templates typically requires duplication of business logic used to choose the correct templates and populate them with data. Rendering from templates may have negative performance effects when only updating a small portion of the page—such as the value of a text input within a large template. Replacing an entire template might also disturb a user's selection or cursor position, where updating only the changed value might not. To avoid these problems, applications can use UI data bindings or granular DOM manipulation to only update the appropriate parts of the page instead of re-rendering entire templates.

##### Browser history

With an SPA being, by definition, "a single page", the model breaks the browser's design for page history navigation using the Forward/Back buttons. This presents a usability impediment when a user presses the back button, expecting the previous screen state within the SPA, but instead, the application's single page unloads and the previous page in the browser's history is presented.

The traditional solution for SPAs has been to change the browser URL's hash fragment identifier in accord with the current screen state. This can be achieved with JavaScript, and causes URL history events to be built up within the browser. As long as the SPA is capable of resurrecting the same screen state from information contained within the URL hash, the expected back button behavior is retained.

To further address this issue, the HTML5 specification has introduced pushState and replaceState providing programmatic access to the actual URL and browser history.

##### Analytics

Analytics tools such as Google Analytics rely heavily upon entire new pages loading in the browser, initiated by a new page load. SPAs do not work this way.

After the first page load, all subsequent page and content changes are handled internally by the application, which should simply call a function to update the analytics package. Failing to call said function, the browser never triggers a new page load, nothing gets added to the browser history, and the analytics package has no idea who is doing what on the site.

It is possible to add page load events to an SPA using the HTML5 history API; this will help integrate analytics. The difficulty comes in managing this and ensuring that everything is being tracked accurately – this involves checking for missing reports and double entries. Some frameworks provide open source analytics integrations addressing most of the major analytics providers.

##### Speed of initial Load

Single Page Applications have a slower first page load than server-based applications. This is because the first load has to bring down the framework and the application code before rendering the required view as HTML in the browser. A server-based application just has to push out the required HTML to the browser, reducing the latency and download time.

There are some ways of speeding up the initial load of an SPA, such as a heavy approach to caching and lazy-loading modules when needed. But it's not possible to get away from the fact that it needs to download the framework, at least some of the application code, and will most likely hit an API for data before displaying something in the browser. This is a "pay me now, or pay me later" trade-off scenario. The question of performance and wait-times remains a decision that the developer must make.

### References

```
https://en.wikipedia.org/wiki/Single-page_application
```

### 



