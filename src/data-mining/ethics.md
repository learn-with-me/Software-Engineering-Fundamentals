# Ethics

## Trespass to Chattels

Trespass to chattels is fundamentally different from what we think of as “trespassing laws” in that it applies not to real estate or land but to movable property, or chattels in legal parlance. It applies when your property is interfered with in some way that does not allow you to access or use it.

Checking out a website via your browser is fine; launching a full-scale Distributed Denial of Service (DDOS) attack against it obviously is not.

Three criteria need to be met for a web scraper to violate trespass to chattels:

1. **Lack of consent:** Because web servers are open to everyone, they are generally “giving consent” to web scrapers as well. However, many websites’ Terms of Service agreements specifically prohibit the use of scrapers. In addition, any cease and desist notices delivered to you may revoke this consent.
2. **Actual harm:** Servers are costly. In addition to server costs, if your scrapers take a website down, or limit its ability to serve other users, this can add to the “harm” you cause.
3. **Intentionality:** If you’re writing the code, you know what it does! Arguing a lack of intention would likely not go well when defending your web scraper.

## Computer Fraud and Abuse Act

Computer Fraud and Abuse Act (CFAA) applies to only a stereotypical version of a malicious hacker unleashing viruses, the act has strong implications for web scrapers as well.

In short: stay away from protected computers, do not access computers (including web servers) that you are not given access to, and especially, stay away from government or financial computers.

## Robots Exclusion Protocol (robots.txt)

If you go to just about any large website and look for its `robots.txt` file, you will find it in the `root web folder`. robots.txt can be parsed and used by automated programs extremely easily. It is merely a sign that says `Please don’t go to these parts of the site`.

There is no official governing body for the syntax of robots.txt. Example below:

```
# Welcome to my robots.txt file!
User-agent: *
Disallow: *

# Google Search Engine Robot
User-agent: Googlebot
Allow: *
Allow: /search?q=%23
Disallow: /private
```

## Considerations

* Don't be a jerk
* Do not scrape any user's personal information, even if it is publicly available
* Respect rules in robots.txt, defined by the domain owner
* It’s best to leave the bot running slowly and during the night, than hammering the site hard in a short time.
* If you're crawling multiple websites, it is ok to do that in parallel. The load needs to be reasonable for each individual remote server.

## Interesting links

* [The Google web cache](http://webcache.googleusercontent.com/search?q=cache:http://pythonscraping.com) | Every site that Google's bot crawl, they make a copy of the site and host it on the internet. If a website you are searching for, or scraping, is unavailable, you might want to check there to see if a usable copy exists!
