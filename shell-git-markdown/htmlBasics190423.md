#HTML Basics

How Web Works

- The URL (Uniform Resource Locator) is the unique address of a resource on the web contains a human readable domain name, that needs to be resolved to the technical IP (Internet Protocol) address of the web server via a DNS (Domain Name Server)
- The browser sends a GET (that's an HTTP method) request to load a HTML (Hyper Text Markup Language) document from a web server
- The web server sends a response containing the document
- Often the HTML code contains references to additional resources (CSS (Cascading Style Sheet) files, images, etc.), which the browser then also requests from the server
- The browser renders the received content to the screen and makes it interactive
- Browsers might also request additional data from servers later via subsequent GET or POST requests

HTML (Hyper Text Markup Language) is used to express text in a structured way. HTML tags indicate what kind of element is displayed on the website. For example, a headline is written like this:


1. Using semantic HTML elements
2. Nesting / grouping of HTML elements


HTML tag attributes : Some elements require some more information in order to work properly. This information is specified via attributes, for example „src“ in img

Layout:

Every HTML document starts with a doctype followed by the <html> element, which consists of two main parts:

```Html

<!DOCTYPE html>
<html>
<head>

</head>
<body>

</body>
</html>
```

Other tags:

<a> for link
<b> to make bold text
<strong> for bold text with emphasys
<body> main HTML part
<br> for break
<div> it is a division or part of an HTML document
<h1>... for titles
<i> to make an italic text
<img> for images in document
<ol> is an ordered list, <ul> for an unordered list
<li> is a list item in bulleted (ordered list)
<p> for paragraph
<span> to style part of text