# **Readings: Web Scraping**

## **How to Web Scrape with Python in 4 Minutes**

Web scraping is a technique for mechanically accessing and extracting vast volumes of data from a website, saving a lot of time and effort. 

<br>

**Python Code**

We start by importing the following libraries:
```
import requests
import urllib.request
import time
from bs4 import BeautifulSoup
```

Next, set the url to the website and access the site with our requests library:
```
url = 'http://web.mta.info/developers/turnstile.html'
response = requests.get(url)
```
Next; parse the html with BeautifulSoup, nested BeautifulSoup data structure.
```
soup = BeautifulSoup(response.text, “html.parser”)
```

We use the method .findAll to locate all of our < a > tags.
```
soup.findAll('a')
```
This code gives us every line of code that has an < a > tag.

Next, let’s extract the actual link that we want. 
```
one_a_tag = soup.findAll(‘a’)[38]
link = one_a_tag[‘href’]
```

We can use our urllib.request library to download this file path to our computer. We provide request.urlretrieve with two parameters: file url and the filename. 

For example files, we named them “turnstile_180922.txt”, “turnstile_180901”.
```
download_url = 'http://web.mta.info/developers/'+ link
urllib.request.urlretrieve(download_url,'./'+link[link.find('/turnstile_')+1:])
```

Now pause our code for a second so that we are not spamming the website with requests. This helps us avoid getting flagged as a spammer.
```
time.sleep(1)
```


<br>

<br>

## **How to Scrape Websites Without Getting Blocked**

Web scraping is an activity that must be carried out responsibly in order to avoid causing harm to the websites being scraped. Poor scraping methods might affect the site's speed. While most websites do not have anti-scraping techniques, certain websites employ procedures that can result in web scraping being restricted because they oppose free data access.

If a crawler makes several requests per second and downloads huge files, an underpowered server will struggle to keep up with multiple crawlers' demands. Some site managers dislike spiders and try to limit their access because web crawlers, scrapers, or spiders don't actually drive human website visitors and appear to impact the site's performance.

<br>

This is done by following a set of rules:

1. ***Respect Robots.txt***

    Web spiders should ideally follow the robot.txt file for a website while scraping. It has specific rules for good behavior.

    It's found usually on the root directory of a website – http://example.com/robots.txt.

    If it contains lines like the ones shown below, it means the site doesn’t doesn't want to be scraped.
    ```
    User-agent: *
    Disallow:/ 
    ```

2. ***Make the crawling slower, do not slam the server, treat websites nicely***

    Make your spider appear real by imitating human behavior. Add some delays after crawling a limited number of pages, and use the fewest amount of concurrent requests possible. Put a 10-20 second pause between clicks and don't put too much strain on the website by treating it nicely.

3. ***Do not follow the same crawling pattern***

4. ***Make requests through Proxies and rotate them as needed***

5. ***Rotate User Agents and corresponding HTTP Request Headers between requests***
