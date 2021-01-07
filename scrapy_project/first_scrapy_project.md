
# **START YOUR FIRST SCRAPY PROJECT**

<img src="https://github.com/lakebrains-technologies/Blogs/blob/master/scrapy_project/images/thumbnail.png?raw=true"/>

Before start with scrapy. I hope you’re already familiar with python or python package installer. They both are required to install scrapy on your machine. Scrapy requires a python 3.6+ version.

If you don’t have to install python on your machine you just need to install it first.

Install python - [https://www.python.org/downloads/](https://www.python.org/downloads/)

Download python from the above links and install it to your system.

After installing python, you just need to install the python package install in your system or you can create a virtual environment for your scrapy project

## **Python package install**

```
pip install pip
```

## **In python, we can use anaconda for a virtual environment**

Install anaconda - [https://www.anaconda.com/products/individual#windows](https://www.anaconda.com/products/individual#windows)

Download anaconda from the above links and install it in your system.

Pip installs python packages whereas Conda installs packages that may contain software written in any language.

## \# **Install scrapy on your machine using the following command on cmd or conda cmd**

```
pip install scrapy
```

<img src="https://github.com/lakebrains-technologies/Blogs/blob/master/scrapy_project/images/1.jpg?raw=true"/>

## \# **After installation you check scrapy in your system using the following command**

```
scrapy
```

<img src="https://github.com/lakebrains-technologies/Blogs/blob/master/scrapy_project/images/2.jpg?raw=true"/>

## \# **For check scrapy version on your system**

```
scrapy version
```

<img src="https://github.com/lakebrains-technologies/Blogs/blob/master/scrapy_project/images/3.jpg?raw=true"/>

## \# **Run a quick benchmark test**

```
scrapy bench
```

Scrapy Comes With A Simple Benchmarking Suite That Spawns A Local HTTP Server And Crawls It At The Maximum Possible Speed. The Goal Of This Benchmarking Is To Get An Idea Of How Scrapy Performs In Your Hardware, In Order To Have A Common Baseline For Comparisons. It Uses A Simple Spider That Does Nothing And Just Follows Links.

<img src="https://github.com/lakebrains-technologies/Blogs/blob/master/scrapy_project/images/4.jpg?raw=true"/>

## \# **For example check static website URL using scrapy**

```
scrapy fetch — nolog https://docs.scrapy.org/en/latest/topics/commands.html
                            (Your Website Url)
```

## \# **Save/Download static website in local machine using scrapy where**

```
scrapy fetch — nolog https://docs.scrapy.org/en/latest/topics/commands.html > scrapydocs.html
                            (Your Website Url >   Your Output File Name)

```

## \# **Open your website URL in a web browser for static website**

```
scrapy view https://docs.scrapy.org/en/latest/topics/commands.html
```

## \# **For scrapy shell**

```
scrapy shell https://docs.scrapy.org/en/latest/topics/commands.html
```

<img src="https://github.com/lakebrains-technologies/Blogs/blob/master/scrapy_project/images/5.jpg?raw=true"/>


## \# **Shelp() to see all commands**

```
shelp()
```

<img src="https://github.com/lakebrains-technologies/Blogs/blob/master/scrapy_project/images/6.jpg?raw=true"/>

## \# **Use xpath or css in scrapy in scrapy shell**
### **For xpath**

```
fetch(“https://docs.scrapy.org/en/latest/topics/commands.html”)
response.xpath(‘/html/head/title/text()’).get()
```

<img src="https://github.com/lakebrains-technologies/Blogs/blob/master/scrapy_project/images/7.jpg?raw=true"/>

### **For CSS**

```
fetch(“https://docs.scrapy.org/en/latest/topics/commands.html”)
response.css(‘#div’).get()
```

<img src="https://github.com/lakebrains-technologies/Blogs/blob/master/scrapy_project/images/8.jpg?raw=true"/>

When you start any project in scrapy just create a separate directory for your project


## \# **Make a new directory**

```
mkdir dir
```

<img src="https://github.com/lakebrains-technologies/Blogs/blob/master/scrapy_project/images/9.jpg?raw=true"/>

## \# **Swtich to your new directory**

```
cd dir
```

## \# **Create your first scrapy project**

```
scrapy startproject scrapyprojectname
                    (Your scrapy project name)
```

<img src="https://github.com/lakebrains-technologies/Blogs/blob/master/scrapy_project/images/10.jpg?raw=true"/>

## \# **Enter to your project folder**

```
cd scrapyprojectname
```

<img src="https://github.com/lakebrains-technologies/Blogs/blob/master/scrapy_project/images/11.jpg?raw=true"/>

## \# **Create the first spider for the project first switch to spider folder in cmd then run this command**

```
scrapy genspider example –t crawl example.com

    (Spider Name - > Use for import LinkExtractor ,CrawlSpider, Rule ->   website URL)
```

<img src="https://github.com/lakebrains-technologies/Blogs/blob/master/scrapy_project/images/12.jpg?raw=true"/>

## \# **First we need to switch spider location in command prompt then run the spider**

```
scrapy crawl example
        (Spider Name)
```

## \# **Example project for scraping product data from amazon eCommerce website**

### **Reference url** - [https://blog.datahut.co/tutorial-how-to-scrape-amazon-data-using-python-scrapy/](https://blog.datahut.co/tutorial-how-to-scrape-amazon-data-using-python-scrapy/)
### **For Official Documentation for Scrapy** - [Https://Docs.Scrapy.Org/En/Latest/Topics/Commands.Html](Https://Docs.Scrapy.Org/En/Latest/Topics/Commands.Html)

### ***Author Name*** :  [Deepesh sharma](https://medium.com/@sharma.deepesh78)