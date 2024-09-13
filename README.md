# selenium-interview-questions

## 1. What are the various WebDriver methods in selenium?
1. driver.get(url)
2. driver.switchTo()
3. driver.getTitle()
4. driver.getWindowHandles()
5. driver.getWindowHandle()
6. driver.close()
7. driver.quit()
8. driver.findElement()
9. driver.findElement(By.xpath("//input[@name='uid']"))

## 2. What are WebElement methods?
Anything present on the webpage is called as webelement.Like checkbox, textbox, buttons etc

Before performing any action on the elements.We have to perform the following steps
1. Inspect the element.
2. Locate the element.
3. Find the element.
4. perform action on the element.

### Methods of WebElement interface-


## 3. Difference between close() and quit() method ?
1. close is used to close current browser window
2. quit is used to close all browser windows.

## 4. How to initialize driver to run on different browsers ?
Here we are creating an object of child class and assigning to parent reference variable. This is upcasting.
1. WebDriver driver = New ChromeDriver();
2. WebDriver driver = new FirefoxDriver();

## 5. What is a Xpath?
Xpath is an expression or syntax to locate an element on the webpage.

Xpath=//tagname[@attribute='value']

Different ways to find elements on the web page. There are 8 types of locators and all the locators take string as an argument.
1. Id(String)
2. name(String)
3. className(String)
4. tagName(String)
5. linkText(String)
6. partialLinkTest(String)
7. xpath(String)

There are two types of XPath:

1) Absolute XPath - Starts from parent node of DOM, all the way to destination. The key characteristic of XPath is that it begins with the single forward slash(/) ,which means you can select the element from the root node.
2) Relative XPath - can start from anywhere in the DOM. It starts with double forward slash (//). It can search elements anywhere on the webpage.

## 6. How to search dynamic elements on the webpage?
We can use contains or stars-with method to find dynamic elements.

### 1. contains() is a method used in XPath expression.

//tagname[contains(@attribute,'value')]

//input[contains(@name,'uid')]

<div class="new-training">Selenium Online Trainings</div>

//div[contains(text(),'Selenium Online Trainings')]

### 2. starts-with is a function used for finding the web element whose attribute value gets changed on refresh or by other dynamic operations on the webpage.

For example -: Suppose the ID of particular element changes dynamically like:

Id=” message12″

Id=” message345″

<input id="message123">user id must not be blank</label>

Xpath=//input[starts-with(@id,'message')]

## 7. Difference between findElement and findElements in Selenium?
![img.png](img.png)

## 8. How to find count of links on the webpage?
driver.get("https://www.google.com)

List<WebElement> ls = driver.findElements(By.tagName("a"));

System.out.println(ls.size());

    for(WebElement element : ls){
    System.out.println(element.getAttribute("href"));
   }

## 9. 
