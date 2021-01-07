# **Selenium Tool Startup guide for Beginner:**

<img src="https://github.com/lakebrains-technologies/Blogs/blob/master/selenium_tool/images/1.png?raw=true"/>

Selenium is the most powerful automation tool for testing web applications using a web browser. It’s an open-source tool. They have many inbuilt packages and APIs that make our task easier.

## **Pre-Requirement:**

Before starting with selenium we need to configure python 3+ in our system.

If you don’t have to install python on your machine you just need to install it first.

Install python - [https://www.python.org/downloads/](https://www.python.org/downloads/)

Download python from the above links and install it to your system.

## **Install selenium:**

After python successfully setup, then we can install selenium in our system.

```
pip install selenium
```

Selenium is a web scrappy tool. They can help to extract content from dynamic websites or web applications and we can store that content in any database or excel format for further analytics purposes.

### **Use of selenium web scraping tool:**

- web content scraping
- data mining
- Research/analytics
- Web Data Integration

### **Selenium Driver:**

Selenium needs a browser driver to provide a platform to launch and perform tasks in a web browser.

So we need to install a Webdriver in our web browser.

### \#  **Install Chromedriver in Windows**

Get to the latest release of Chromedriver by going to the official websites.
[http://chromedriver.chromium.org/downloads](http://chromedriver.chromium.org/downloads)
After downloading the latest version you just need to unzip it.

After unzip move the chormedrive to c://programfile or move to your python folder. Just confirm that your path is setup with your environment variable.

### \# **Install ChromeDriver in Ubantu**

open terminal and run this command one by one

```
wget https://chromedriver.storage.googleapis.com/2.41/chromedriver_linux64.zip
unzip chromedriver_linux64.zip

# Chormedriver path setup in ubuntu open terminal and run this commands
sudo mv chromedriver /usr/bin/chromedriver
sudo chown root:root /usr/bin/chromedriver
sudo chmod +x /usr/bin/chromedriver
```

after successfully setup selenium or chormedriver in our system. We practices so exercise for more understanding.

### \# **Exercise 1 :**

Open lakebrains.com url using selenium chrome web driver

```
from selenium import driver
 driver = webdriver.Chrome()
 driver.get(“https://www.lakebrains.com")
```

### **Locating Elements:**

when we want to extract data/content from website so we need to local or unique identifier of our conentet so following this locator element to we can get our content from website.

```
• find_element_by_id
• find_element_by_name
• find_element_by_xpath
• find_element_by_link_text
• find_element_by_partial_link_text
• find_element_by_tag_name
• find_element_by_class_name
• find_element_by_css_selector
```

when we have same element multiple times over webpage or we want to find all elements then we can use this following element locator they will return a list

```
• find_elements_by_name
• find_elements_by_xpath
• find_elements_by_link_text
• find_elements_by_partial_link_text
• find_elements_by_tag_name
• find_elements_by_class_name
• find_elements_by_css_selector
```

### \# **Exercise 2 :**
Open Google.com url and search keyword using selenium chrome web driver

```
 from selenium import driver
 import time
 driver = webdriver.Chrome()
 driver.get(‘http://www.google.com/')
 time.sleep(5)

 # Target Search Input element name=’q’
 search_box = driver.find_element_by_name(‘q’)

 # Pass Keyword here
 search_box.send_keys(‘lakebrains’) 
 search_box.submit()
 time.sleep(5) 
 driver.quit()
```

### \# **Navigate Google.com through HTML DOM Elements and get search text element**

```
<input id=”id-search-field” name=”q” type=”search” role=”textbox” class=”search-field” placeholder=”Search” value=”” tabindex=”1">
```

following way to we can also access the above text element

```
CSS ID: .find_element_by_id(“id-search-field”)

DOM Path: .find_element_by_xpath(“//input[@id=’id-search-field’]”)

CSS class: .find_element_by_class_name(“search-field”)

CSS Name: find_element_by_name(‘q’)
```

In selenium, many times we are facing a timeout situation so have to use WebDriverWait and we have to handle is an error we can add try/except in our code.

```
try:
 wait = WebDriverWait(browser, 10)
 element = wait.until(EC.element_to_be_clickable((By.XPATH, “put the xpath here”)))
 except:
 print(“xpath is not found”)
```

### \# **Exercise 3 :**

we used multiple api in our project those api could be pre-build api or we can create our custom api as well.

This following api to we can get email from current webpage

```
# Get Email address from Current Page using xpath
# Funtion :
# getEmailAddress(page_data,find)
#
# Input args :
# page_data : Current webpage completed page source
# find : flag (if it is true then return email address)
#
# Output :
# Return email address or return false if email not found
def getEmailAddress(page_data,find):t
 try:
 email = re.findall(“([a-zA-Z0–9_.+-]+@[a-zA-Z0–9-]+\.[a-zA-Z0–9-.]+)”, page_data)
 if not email:
 email = “ “
 find = False
 return email ,find
 else:
 find = True
 return email ,find
 except:
 email = “ “
 find = False
 return email ,find
```

### Useful Links:

Selenium with Python: [https://selenium-python.readthedocs.io](https://selenium-python.readthedocs.io)


### ***Author Name*** :  [Deepesh sharma](https://medium.com/@sharma.deepesh78)
