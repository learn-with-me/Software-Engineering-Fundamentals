# Preface

With this book, I've made an attempt to explain the world of `asynchronous communication` over internet, in my own words (along with some borrowed words).

> Note: The contents of this book do not have to be ready cover-to-cover. Instead feel free to jump around sections that appeal most to you.

## Forms of communication

- Synchrounous
- Asynchrounous
- Messaging

## How computers "talk"?

Computer "A" sends a message to computer "B". Until "B" responds back to "A", "A" has no way of knowing whether "B" received the message or not. Something along the lines of `delivery confirmation` (acknowledging) or even `an answer` (responding) to a question asked.

`Synchrounous communication (sync)` happens when "A" decides to `wait` for "B" to respond, and not do anything until it recieves a response.

`Asynchrounous communication (async)` happens when "A" continues performing other tasks, while "B" sends the response back. To do this "A" would send the message, somehow remember it is yet to get the response back, continune performing other tasks, and when receives the response from "B", goes back to reading it. Similar to how [time-sharing](https://en.wikipedia.org/wiki/Time-sharing) systems work, formally known as multi-tasking.

`Message-based communication (event)` happens when "A" is only interested in sending a message to "B", and not care about what "B" does with it.

## Protocols

How does "B" know that it has to even respond back to "A"?
How does "B" know how to read the message that "A" sent? - all binary

## Sync vs Async

So long we've relied on exchange mechanisms for communication, and we still do. It is very effective, and the right use case for `a variety of needs`. There is nothing wrong in it. And it is going nowhere.

What has changed, is our needs. Our needs have evolved into doing everything faster and doing a lot more at the same time. This is where at times it becomes impractical to committing on real-time communication, a.k.a. synchrounous communication.



