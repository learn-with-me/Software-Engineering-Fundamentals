# Data Mining

Data mining is the automated gathering of data from the internet. Also commonly known as screen scraping, web scraping, web harvesting, etc.

## Table of contents

- Crawling vs Scraping
- Ways it is done?
- [Legalities]
- [Ethics]
- Tasks
  - Finding
  - Parsing
  - Crawling

## Classifying the project

- `crawling` or `scraping`
- `broad` or `targeted`
- `one-time` or `long running`
  - One-time projects result in producing files in formats like csv, json, etc
  - Long running projects involve monitoring, re-scanning for new data, update data, etc
- Data needed for collection or more in-depth analysis

## Using Python

Python has a default recursion limit (the number of times a program can recursively call itself) of 1,000. Because Wikipedia’s network of links is extremely large, the program will eventually hit that recursion limit and stop, unless you put in a recursion counter or something to prevent that from happening.

With server-side redirects, you usually don’t have to worry. If you’re using the `urllib` library with Python 3.x, it handles redirects automatically! If you’re using the Requests library, make sure to set the `allow_redirects` flag to True:

```python
r = requests.get('http://github.com', allow_redirects=True)
```

## Helpful links

### Affiliates

- Amazon [promotions API](https://webservices.amazon.com/paapi5/documentation/offers.html#promotions)
- Walmart [affiliate program](https://www.walmart.io/)
- Target [partners](https://partners.target.com/)
- eBay [partner network](https://partnernetwork.ebay.com/)
- Etsy [affiliates program](https://www.etsy.com/uk/affiliates)
- Nike [affiliate program](https://www.nike.com/se/en/help/a/nike-affiliate-programme)
- Advanced Auto Parts [affiliate program](https://shop.advanceautoparts.com/o/affiliates)
- [AliExpress](https://portals.aliexpress.com/affiportals/web/portals.htm)

### 3rd party tools & APIs

- [Google Search Central](https://developers.google.com/search/docs/appearance/structured-data) - to learn more about how search engines find and tag the data that they display in special search result features and enhancements.
- [WebScraping API](https://www.webscrapingapi.com/pricing)

### Examples sites to scrape

- https://records.nhl.com/
- https://www.nfl.com/stats/player-stats/
- [Wikipedia API](https://www.mediawiki.org/wiki/API:Main_page)
  - [Six Degrees of Kevin Bacon](https://en.wikipedia.org/wiki/Six_Degrees_of_Kevin_Bacon)
  - [The Oracle of Bacon](https://oracleofbacon.org/)
