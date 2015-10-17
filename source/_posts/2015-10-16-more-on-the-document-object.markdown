---
layout: post
title: "more on the Document object"
date: 2015-10-16 19:47:24 -0500
comments: true
categories: 
---
My last post touched on the difference between core JavaScript and Web API's, or client-side JavaScript. Because of the importance of this difference, I felt one more blog post was in order on the topic. Again, I highly encourage you to read the article at <a target='_blank' href='http://foorious.com/ikn/javascript/r2j/what-is-javascript/'>foorious.com</a> which does a great job of explaining the difference between core JavaScript and Web API's. The main Web API that core JavaScript deals with is the Document object, or DOM, standing for Document Object Model. 
  
The following are all quotes from <a target='_blank' href='https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model/Introduction'>MDN, “Introduction to the DOM”</a>, including the script examples:
“The DOM provides a representation of the document as a structured group of nodes and objects that have properties and methods. Essentially, it connects web pages to scripts or programming languages.....The DOM is a fully object-oriented representation of the web page, and it can be modified with a scripting language....All of the properties, methods, and events available for manipulating and creating web pages are organized into objects....The DOM is not a programming language, but without it, (languages) wouldn't have any model or notion of the web pages, XML pages and elements with which (they are) usually concerned...”
<p style='margin:0'>“Implementations of the DOM can be built for any language....The DOM was designed to be independent of any particular programming language...
Python DOM example to return a list all &lt;p> elements in the document:
<pre style='margin:0 0 0 10%;padding:0 0 0 5%; color:purple; background: #B2B2B2; font-weight: bold;'>
import xml.dom.minidom as m
doc = m.parse('C:\\Projects\\Py\\chap1.xml');
doc.nodeName # DOM property of document object;
p_list = doc.getElementsByTagName('para');
</pre>JavaScript DOM example to return a list of all &lt;p> elements in the document:
<pre style='margin:0 0 0 10%;padding:0 0 0 5%; color:purple; background: #B2B2B2; font-weight: bold;'>
var paragraphs = document.getElementsByTagName('P');
// paragraphs[0] is the first &lt;p> element
// paragraphs[1] is the second &lt;p> element, etc.
alert(paragraphs[0].nodeName)
</pre></p>
"...documents may be accessed by various browsers with different DOMs....Different browsers have different implementations of the DOM, and these implementations exhibit varying degrees of conformance... but every web browser uses some document object model to make web pages accessible to script....In the beginning, JavaScript and the DOM were tightly intertwined, but eventually they evolved into separate entities....”

MDN further expounds on the fact that there are different DOM's in <a target='_blank' href='https://developer.mozilla.org/en-US/docs/Web/JavaScript/JavaScript_technologies_overview'>JavaScript Technologies Overview”</a>:
“As every web developer has experienced, the DOM is a mess. Browser support uniformity varies a lot from feature to feature, mainly because many important DOM features have very unclear, specifications (if any), and different web browsers add incompatible features for overlapping use cases (like the Internet Explorer event model)....One common, though perhaps not the most reliable, approach to cross-browser compatibility is to use JavaScript libraries, which abstract DOM features and keep their APIs working the same in different browsers. Some of the most widely used frameworks are jQuery, prototype, and YUI.....”

Understanding that it is a language independent convention, and that it is a totally different DOM in each browser are the two main take-aways. When I looked up other <a target='_blank' href='https://developer.mozilla.org/en-US/docs/Web/API'>Web API's on Mozilla</a>, I was pleased to read “interfaces (that is, types of objects)” on the very first line! According to Mozilla, we can officially call Web API's types of objects. If you look at that list of Web API's on the link – wow! The browser is a very powerful piece of software! In front-end web development, it is better to think of the purpose of your code as communicating with the types of objects in the browser, which will be different from browser to browser.