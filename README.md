# selenium-interview-questions

## 1. What is a Xpath?
Xpath is an expression or syntax to locate an element on the webpage.

Xpath=//tagname[@attribute='value']

Different ways to find elements on the web page.
1. ID - To find the element by ID of the element
2. Classname - To find the element by Classname of the element
3. Name - To find the element by name of the element
4. Link text - To find the element by text of the link
5. XPath - XPath required for finding the dynamic element and traverse between various elements of the web page
6. CSS path -	CSS path also locates elements having no name, class or ID.

There are two types of XPath:

1) Absolute XPath - Starts from parent node of DOM, all the way to destination. The key characteristic of XPath is that it begins with the single forward slash(/) ,which means you can select the element from the root node.
2) Relative XPath - can start from anywhere in the DOM. It starts with double forward slash (//). It can search elements anywhere on the webpage.

## 2. How to search dynamic elements on the webpage?
We can use contains or stars-with method to find dynamic elements.

1. contains() is a method used in XPath expression.

//tagname[contains(@attribute,'value')]

//input[contains(@name,'uid')]

<div class="new-training">Selenium Online Trainings</div>

//div[contains(text(),'Selenium Online Trainings')]

2. starts-with is a function used for finding the web element whose attribute value gets changed on refresh or by other dynamic operations on the webpage.

For example -: Suppose the ID of particular element changes dynamically like:

Id=” message12″

Id=” message345″

<input id="message123">user id must not be blank</label>

Xpath=//input[starts-with(@id,'message')]
