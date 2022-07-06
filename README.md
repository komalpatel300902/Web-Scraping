# Web Scraping

` Web Scraping` is a technique employed to extract large amounts of data from websites where by the data is extracted and saved to a local file in your computer or to a database in table (spreadsheet) format.


We are going to use BueatifulSoup for `Web Scraping`.

Downloading the BeautifulSoup Liberary for python.<br><br>
Open `command prompt` and write : 
```
pip install beautifulsoup4
```
Importing the BeautifulSoup in python IDE
```python
from bs4 import BeautifulSoup
```

Let's start by taking a html script as string for simplicity.<br>
`Note` : We use triple quote for multi-lined String.
```python
html_doc = """<html><head><title>The Dormouse's story</title></head>
<body>
<p class="title"><b>The Dormouse's story</b></p>

<p class="story">Once upon a time there were three little sisters; and their names were
<a href="http://example.com/elsie" class="sister" id="link1">Elsie</a>,
<a href="http://example.com/lacie" class="sister" id="link2">Lacie</a> and
<a href="http://example.com/tillie" class="sister" id="link3">Tillie</a>;
and they lived at the bottom of a well.</p>

<p class="story">The End</p>
"""
```

As it is web scraping you have to get the `html script` of Web Pages. You can get them by using request library :
```python
import requests
url = "https://www.flipkart.com/"
response = requests.get(url)
html_doc = response.text
```

`html_doc`  in above code will have html script of that web page in String format.

## Using the `html_doc` in BeautifulSoup
```python
from bs4 import BeautifulSoup
soup = BeautifulSoup(html_doc, 'html.parser')
```

Here `BeautifulSoup(html_doc, 'html.parser')` takes two parameter :
1. `html_doc`  : html script in string format
1. `parser` : As beautiful soup script Xml file also you have to specify what type of parser you want to use.

`soup `in above example is a object or variable through which we are going to extract data from the html_docs. 

