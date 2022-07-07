# Web Scraping

` Web Scraping` is a technique employed to extract large amounts of data from websites where by the data is extracted and saved to a local file in your computer or to a database in table (spreadsheet) format.


We are going to use BueatifulSoup for `Web Scraping`.

## Index
1. **[Installing Library](#installing-the-beautifulsoup-liberary-for-pythonbrbr)**
1. **[Importing BeautifulSoup](#importing-the-beautifulsoup-in-python-ide)**
1. **[Fetching the HTML Script from Web](#fetching-the-html-script-from-web-page)**
1. **[Using BeautifulSoup](#using-the-htmldoc-in-beautifulsoup)**
1. **[Prettify Function ](#prettify-function)**
1. **[Fetching Tag ](#fetching-tags)**
1. **[Fetching all occurance of Tag ](#fetching-all-occurance-of-a-tag)**
1. **[Fetching  Attribute and Values  from Tag ](#fetching-attributes-and-their-values-from-tag)**
1. **[Fetching Text from Tags ](#fetching-text-from-tags)**


## Installing the BeautifulSoup Liberary for python.

Open `command prompt` and write : 
```
pip install beautifulsoup4
```
## Importing the BeautifulSoup in python IDE
```python
from bs4 import BeautifulSoup
```

## Fetching the HTML Script from Web Page
As it is web scraping you have to get the `html script` of Web Pages. You can get them by using request library :
```python
import requests
url = "https://www.flipkart.com/"
response = requests.get(url)
html_doc = response.text
```

`html_doc`  in above code will have html script of that web page in String format.

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

## Using the html_doc in BeautifulSoup
```python
from bs4 import BeautifulSoup
soup = BeautifulSoup(html_doc, 'html.parser')
```

Here `BeautifulSoup(html_doc, 'html.parser')` takes two parameter :
1. `html_doc`  : html script in string format
1. `parser` : As beautiful soup scrap Xml file also, you have to specify what type of parser you want to use.

`soup ` is an object or variable through which we are going to extract data from the html_docs. 


## Prettify Function
```python
docs = soup.prettify()
print(docs)
```
This function show your html script present in `html_docs` in well indented and readable form.<br>
`Output` : 

```python
 <html>
 <head>
  <title>
   The Dormouse's story
  </title>
 </head>
 <body>
  <p class="title">
   <b>
    The Dormouse's story
   </b>
  </p>
  <p class="story">
   Once upon a time there were three little sisters; and their names were
   <a class="sister" href="http://example.com/elsie" id="link1">
    Elsie
   </a>
   ,
   <a class="sister" href="http://example.com/lacie" id="link2">
    Lacie
   </a>
   and
   <a class="sister" href="http://example.com/tillie" id="link3">
    Tillie
   </a>
   ; and they lived at the bottom of a well.
  </p>
  <p class="story">
   The End
  </p>
 </body>
</html>
```

##  Fetching Tags
**Case 1** :

You can fetch the Tags using `soup.tag_name `. It return the first occurance of that perticular tag.
### Title
```python
soup.title
```
`Output`:
```python
<title>The Dormouse's story</title>
```
### Paragraph
```python
soup.p
```
`Output` :
```python
<p class="title"><b>The Dormouse's story</b></p>
```
### Anchor
```python
soup.a
```
`Output` : 
```python
<a class="sister" href="http://example.com/elsie" id="link1">Elsie</a>
```

**Case 2** :

You can also fetch the tags using its **id**.
```python
soup.find(id="link3")
```
`Output` :
```python
<a class="sister" href="http://example.com/tillie" id="link3">Tillie</a>
```

## Fetching all Occurance of a Tag
It is done using find_all function : `soup.find_all("tag_name")`. It return all the Occurance of that perticular tag.
### Anchor Tag
```python
soup.find_all('a')
```
`Output` :
```python
[<a class="sister" href="http://example.com/elsie" id="link1">Elsie</a>,
 <a class="sister" href="http://example.com/lacie" id="link2">Lacie</a>,
 <a class="sister" href="http://example.com/tillie" id="link3">Tillie</a>]
```
### Paragraph Tag
```python
soup.find_all('p')
```
`Output` :
```python
[<p class="title"><b>The Dormouse's story</b></p>, <p class="story">Once upon a time there were three little sisters; and their names were
<a class="sister" href="http://example.com/elsie" id="link1">Elsie</a>,
<a class="sister" href="http://example.com/lacie" id="link2">Lacie</a> and
<a class="sister" href="http://example.com/tillie" id="link3">Tillie</a>;
and they lived at the bottom of a well.</p>, <p class="story">The End</p>]
```



## Fetching Attributes and their Values from Tag


**Case 1** :

We do this using `soup.tag_name.attrs` which return us dictionary of attribute names and their values.

```python
soup.a.attrs
```
`Output` :
```python
{'href': 'http://example.com/elsie', 'class': ['sister'], 'id': 'link1'}
```
**Case 2** :

`soup.tag_name['attribute']` returns the value of attribute for the tag you have specified in place of `tag_name`.

**Sample 1**
```python
soup.p['class']
```

`Output` :
```
title
```
**Sample 2**
```python
soup.a['id']
```
`Output` :
```python
link1
```
**Sample 3**
```python
soup.a['href']
```
`Output` :
```python
http://example.com/elsie
```

## Fetching Text from Tags

**Case 1** :

Using the `get_text` function you can get all the text from `html_doc`.
```python
soup.get_text()
```
`Output` :
```python 
The Dormouse's story

The Dormouse's story
Once upon a time there were three little sisters; and their names were
Elsie,
Lacie and
Tillie;
and they lived at the bottom of a well.
The End
```

**Case 2** :

`soup.tag_name.string` this return the text of first occuring tag that you specify in place of `tag_name`.

```python
soup.p.string
```
`Output` :
```python
The Dormouse's story
```