# Web Application Development

##### Server-side Rendering \(SSR\)

One of the most common issues with server-side rendering in Node.js applications is the overload of the event-loop. Server side rendering \(SSR\) breaks the assumption that led to that vision. It is compute intensive. User code in Node.js runs in a single thread, so for compute operations \(as opposed to I/O\), you can execute them concurrently, but not in parallel. Node.js is able to handle large amounts of asynchronous I/O in parallel but runs into limits on compute. As the compute portion of the request increases relative to I/O, concurrent requests will have an increasing impact on latency because of contention for the CPU.

In practice, requests are often composed of many different asynchronous phases, even if still mostly compute. This can result in even worse interleaving. This problem amplifies as concurrency increases.

> For example, when a single Node.js server is trying to render 10 req in a single second T but only has capacity for 2 req/sec, it will accept all 10 and queue them up. Of those 10 users, the last one will receive the response after 5 second. As no one waits 5 second for a page to load, they will hit refresh and create one more request. If in T+1 the server receives 10 more requests, all of them will be queued up, and it will finish responding to those after 9s.

In order to mitigate this issue, we can apply some intelligent rules of load balancing which keep in consideration the current load of the Node.js process and more precisely of its event loop. To gather metrics on the current usage of the event loop, we can use loopbench via the Express middleware overload-protection.

After running some benchmarks on the current application, we identified an average of 2 req/sec per Node.js process.

Base on this data we can configure overload-protection to return HTTP Status 503 to notify the load balancer that the current node it's too busy to process any other request and to retry later on. This is a basic circuit breaking technique to avoid to saturate Node.js processes adding latency to the overall user experience.

> [https://github.com/mcollina/loopbench](https://github.com/mcollina/loopbench)
>
> [https://github.com/davidmarkclements/overload-protection](https://github.com/davidmarkclements/overload-protection)

##### Assets compilation and distribution

Webpack is used to bundle the bootstrap app into dedicated applications and assets. The included webpack config file generates a dist folder containing 3 subfolders: assets, server and client.

* assets contains all the static assets used by the frontend application like css and images
* server contains the server.js file and the set of routes
* client contains the React application

The client and assets artifacts can be served in production by a dedicated NGINX machine or directly at the edge by Fastly. During local development, everything is directly served by the Node.js process to optimize the development time.

Currently, configurations \(.env files\) are also bundled via webpack-dotenv but it's not a recommended practice as it might lead to leaking sensitive information like API keys.

##### Development workflow

The main goal of the experience behind the boilerplate is to facilitate and optimize the development process. For this purpose webpack is bundling and auto-restarting the Node.js app while updating the front-end app.

> npm run dev

### IRC

Internet Relay Chat \(IRC\) is a system for chatting that involves a set of rules and conventions and client/server software. On the Web, certain sites such as Talk City or IRC networks such as the Undernet provide servers and help you download an IRC client to your PC.

The chat process works on a client/server networking model. IRC clients are computer programs that users can install on their system or web based applications running either locally in the browser or on 3rd party server. These clients communicate with chat servers to transfer messages to other clients.

IRC is also an open standard, and therefore doesn’t belong to anyone. The protocol is defined as RFC 1459. That means anyone can read the specification and write a client or server program

###### Related links

```
https://wiki.mozilla.org/IRC
https://en.wikipedia.org/wiki/Comparison_of_Internet_Relay_Chat_clients
```

### Browser Database

```
IndexDB
https://developers.google.com/web/ilt/pwa/working-with-indexeddb
```

### Sprites and Spritesheets

```
https://www.codeandweb.com/what-is-a-sprite-sheet
```



