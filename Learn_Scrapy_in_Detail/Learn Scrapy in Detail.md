
# Learn Scrapy In Detail

---
> ## What is Scrapy? <br>

Definition:- <br>
Scrapy is an open-source framework written in python. Scrapy is made for web Scrapping only but it can also be used in extracting data using APIs.
Scrapy is a complete package when it comes to downloading the webpages, processing, and storing the data into databases.
Scrapy is an application framework for crawling websites or web pages and extracting structured data which can be used for a wide range of useful applications like data mining, information processing, or historical archival. Scrapy can be used for API,s and Generic Crawler.

> ## Two main Concepts in Scrapy. <br>

1. Crawling
2. Scraping

- Crawling:- Is the act of programmatically retrieving and downloading a web page’s data, extracting its hyperlink, and following them.
- Scraping:- Is the act of programmatically retrieving and downloading a web page’s data, extracting very specific information from it.

<img src="https://github.com/lakebrains-technologies/Blogs/blob/master/Learn_Scrapy_in_Detail/Images/1.png?raw=true"/>

> ## Some Python Libraries for Scraping
 - BeautifulSoup <br>
- Requests
- URLlib
- Html.parser
- LXML
- Selectolax <br>

<img src="https://github.com/lakebrains-technologies/Blogs/blob/master/Learn_Scrapy_in_Detail/Images/2.png?raw=true"/>

> ## Scrapy is not a library it’s a Framework

- There is a huge difference between framework and library let’s see the difference:

<img src="https://github.com/lakebrains-technologies/Blogs/blob/master/Learn_Scrapy_in_Detail/Images/3.png?raw=true"/>

> ## Scrapy has two pillars on which it works: -
 1. Asynchronous
 2. Control
---
>1. ## Asynchronous:- 
-  This is the most important and defining feature of scrapy.
- Without Asynchronous it’s not possible to run multiple Spiders jobs at the same time.
- Scrapy is written with twisted which is a high-level network event-driven framework for python.
- Asynchronous works to connect multiple URL and crawl to different pages
---
>2. ## Control:-
- The Data flow process needs complete control and it’s possible by its modular design.
- This is the engine of scrapy which handle the crawler request from the Spiders
- And then past to the downloaded module and execute.
- Then we get the result as items.
- There are the multiple control data flows working at the same time to execute the module in a loop and get data multiple times from multiple URLs.

> ## Advantages of Scrapy
- Fault-tolerant
- Parallel execution
- Reliable
- Control
- speed

> ## Scrapy Architecture

In the below image we can see the architecture of scrapy.

<img src="https://github.com/lakebrains-technologies/Blogs/blob/master/Learn_Scrapy_in_Detail/Images/4.png?raw=true"/>
 
1. Spiders:- These are custom classes written by developers to parse responses and extract items from sites.
2. Engine:- This is responsible for the data flow between all components of the system. And interfere when sudden action is happening.
3. Scheduler:-This receives the requests from the engine and incuse them to feeding them later when the engine requires them.
4. Downloader:- This is responsible for fetching the webpages and feeding them to the engine which return feeds them to the Spiders.
5. Items:- This is responsible for processing the items once they have been extracted by the Spiders. Items represent the data that is retrieved from the websites. It also does some typical tasks like cleaning, validating, and data persistence such as storing the item in the database.

There is another example of scrapy architecture and the workflow of architecture.
<img src="https://github.com/lakebrains-technologies/Blogs/blob/master/Learn_Scrapy_in_Detail/Images/5.png?raw=true"/>

> ## Spiders

Spiders are classes where custom behaviors are defined as crawling and parsing pages.

> ## How Scrapy implemented Spiders

- What can be crawled means which URL or which webpage you wanted to crawl and get data from that page.
- We have to find out our way to crawl the website or webpage.
- And the last one is how we parsed like we want to parse in which format JSON, XML, HTML, etc.

> ## Types of Scrapy Spiders

## 1. Scrapy.spider:-
> This is the simplest spider and the one on which other spiders must inherit. This spider doesn’t provide any special functionality. It just provides the default request method implementation which sends requests to start URL attribute and call the parse method for each of the result.
- Name:- Defines the name of the spider
- Allowed_domains:- List of the domain that the spider allowed to crawl.
- Start_URLs:- List of URL where the spider begins to crawl from
- Start_requests:- A method that must return an iterable object with the first requests to crawl for the spider.
>Parse:- default method used by Scrapy to process downloaded response when their requests don’t specify a callback

> ## Example:

### It imports Scrapy Libraries
>import scrapy

### It creates the default class named by your project
>class CoolSpider(scrapy,spider):

### Your project Name
>name = ‘website.com’

### Domain from you extract data
>allowed_domains = [‘Website.com’]

### URL from you start scraping
>start_urls= [
‘http://www.website.com/page.html’,
‘http://www.website.com/page2.html’,
]

### Function to parse data and response parameter which holds the data of your webpage.
>Def parse(self, response):<br>
for h1 in response.xpath(‘//h1’).getall():

### Yield freeze your page till data will extract
>Yield {“title”:h1}

### Xpath helps to extract the exact data you want from the webpage
>for href in response.xpath(‘//a/@href’).getall(): <br>
yield scrapy.request(response.urljoin(href),self.parse)

## 2. Generic Spider:- 
   >Purpose of this Spider is to provide convenient functionality for few common scrapy use cases such as following all links on-site based on specific rules or calling for site maps or parsing an XML or CSV data fields.

> ## Scrapy has four different types of generic spiders

>- CrawlSpider:- Follows all links on a site based on certain rules.
>- XMLFeedSpider :- parses XML feeds by iterating through nodes.
>- CSVFeedSpider:- parses CSV feeds by iterating through rows
>- SiteMapSpider:- crawl a site by discovering the URLs using sitemaps

> ## Crawl Spider

>1. Rules:- list of one or more rule object
>2. Rule:- Defines behavior for crawling a site
>3. Parse_start_URL:- This method is called for the start_URLs responses.
>4. Link_extractor:- Define how links will be extracted from each crawled page.

> ## Example:-

### Importing scrapy library
> Import scrapy

### Import scrapy spider library to crawl on multiple pages and assign rules
>From scrapy.spiders import Crawlspider, Rule

### This library extract all the links found on the website or webpage
>From scrapy.linkextractors import LinkExtractor

### Class of project
>Class CoolSpider (CrawlSpider):

### Project name
>Name = ‘website.com’

### Website from we extract data
>allowed_domains = [‘Website.com’]

### URL from we start searching and extracting data
>start_urls= [
‘http://www.website.com/page.html’,
‘http://www.website.com/page2.html’,
]

### Rules which give instructions to the crawler that what we want and how
>Rules = (
Rule(LinkExtractor(allow=(‘product\.php’, ),callback=’parse_item’),
)

### Parser class to parse the HTML page
>def parse_item(self, response):
Item = scapy.Item()
Item[‘name’] = response.xpath(‘//td[@id=”prod_name”]/text()’).get()
Item[‘link_text’] = response.meta[‘link_text’]
Return item

>### XMLFeedSpider

XMLFeedSpider [source] XMLFeedSpider is designed for parsing XML feeds by iterating through them by a certain node name. The iterator can be chosen from internodes , XML, and HTML

> ## Example:

### Importing Libraries for XMLFeedSpider
>from scrapy.spiders import XMLFeedSpider

### Class to call the library
>class ExampleSpider(XMLFeedSpider):

### Name of the project
>name = ‘example

### Taking URL of website in variable
>namespaces = [
(‘x’, ‘http://www.w3.org/TR/html4/'),
]
itertag = ‘x:td’
iterator = ‘xml’

### Function to get data by using XPath
>def parse_node(self, response, node):
self.logger.debug(node.xpath(‘text()’).extract_first())

> ## CSVFeedSpider

### 1. Delimiter:-
>Represents the separator char for each field in the CSV. Defaults to,
### 2. Quotechar:-
>Represents the enclosure char for each field in the CSV. Defaults to,
> ## Headers:-Column names within the CSV

## Example:

### Import Scrapy
>import scarpy

### CSVSpider receive each file as CSV and store data
>From scrapy.spiders import CSVFeedSpider

### Represents the stock of a particular product at a particular location
>from project.items import ProductItem

### Class of project
>Class CoolSpider(CSVSpider):

### Project name
>Name = ‘website.com’

### Website from we extract data
>allowed_domains = [‘Website.com’]

### URL from we start searching and extracting data
>start_urls= [ ‘http://www.website.com/products.csv’]

### Delimiter is the comma character, which acts as a field
>delimiter = ‘:’

### It refers to the single-character string that will be used to quote values if special characters (like delimiter) appears inside the field.
>quotechar = “ ’ “

### Headers contain protocol-specific information which appears when a connection request sent
>headers = [‘products’ , ‘price’]

### Parser function for parsing the HTML data
>def parse_row(self, response, row)
item= ProductItem()
item[‘product’] = row[‘product’]
item[‘price’] = row[‘price’]
return item

> ## SiteMapSpider

1. Sitemap_URL:- List of URLs Pointing to the Sitemap
2. Sitemap_rule:- [(‘/product/’,’prase_product’)]
3. Sitemap_follow:- list of sitemap regular expressions that should be followed.
4. Sitemap_alternate_links:- Alternate links for the specific URL
Sitemap_filter:- Filters to select sitemap entries based on attributes.

> ## Example:

### Import Scrapy
>import scrapy

### SitemapSpider allows you to crawl a site by discovering the URLs using Sitemaps.
>From scrapy.spiders import SitemapSpider

### Class of project
>class Coolspider(SitemapSpider):

### Sitemap URL from we engaged the sitemaps
>Sitemap_urls = [‘http://www.website.com/sitemap.xml’]

### Assigning the rules which follow by the crawler
>Sitemap_rules=[
(‘/product/’,’parse_product’),
(‘/prodcategory/’, ‘parse_prod_category’),
]

### Parser function
>def parse_product(self, response):

### Scrape each product category

>def parse_prod_category(self, response)
