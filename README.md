# selenium-interview-questions

## 1. What are the various WebDriver methods in selenium?
```java
1. driver.get(url)
2. driver.switchTo()
3. driver.getTitle()
4. driver.getWindowHandles()
5. driver.getWindowHandle()
6. driver.close()
7. driver.quit()
8. driver.findElement()
9. driver.findElement(By.xpath("//input[@name='uid']"))
```

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
2. quit is used to close all opened browser windows.

## 4. How to initialize driver to run on different browsers ?
Here we are creating an object of child class and assigning to parent reference variable. This is upcasting. We do this so we can run test on multiple browsers.
```java
1. WebDriver driver = new ChromeDriver();
2. WebDriver driver = new FirefoxDriver();
```

## 5. What is a Xpath?
Xpath is an expression or syntax to locate an element on the webpage.

Xpath=//tagname[@attribute='value']

Different ways to find elements on the web page. There are 8 types of locators and all the locators take string as an argument.
```java
1. id(String)
2. name(String)
3. className(String)
4. tagName(String)
5. linkText(String)
6. partialLinkTest(String)
7. xpath(String)
```
There are two types of XPath:

1) Absolute XPath - Starts from parent node of DOM, all the way to destination. The key characteristic of XPath is that it begins with the single forward slash(/) ,which means you can select the element from the root node.
2) Relative XPath - can start from anywhere in the DOM. It starts with double forward slash (//). It can search elements anywhere on the webpage.

## 6. How to search dynamic elements on the webpage?
We can use contains or stars-with method to find dynamic elements.

### 1. contains() is a method used in XPath expression.
```java
//tagname[contains(@attribute,'value')]
//input[contains(@name,'uid')]
<div class="new-training">Selenium Online Trainings</div>
//div[contains(text(),'Selenium Online Trainings')]
```

### 2. starts-with is a function used for finding the web element whose attribute value gets changed on refresh or by other dynamic operations on the webpage.

For example -: Suppose the ID of particular element changes dynamically like:
```java
Id=” message12″
Id=” message345″

<input id="message123">user id must not be blank</label>
Xpath=//input[starts-with(@id,'message')]
```
## 7. Difference between findElement and findElements in Selenium?
![img.png](img.png)

## 8. How to find count of links on the webpage?
```java
driver.get("https://www.google.com")
List<WebElement> ls = driver.findElements(By.tagName("a"));
System.out.println(ls.size());
    for(WebElement element : ls){
    System.out.println(element.getAttribute("href"));
   }
```

## 9. How to check logo available or not ?
```java
driver.get("https://www.google.com");
WebElement element = driver.findElement(By.xpath("//*[@name='logo']"));
boolean logoPresent = element.isDisplayed();
assert.assertTrue(logoPresent);
```
1. assertTrue(boolean condition): This Assertion verifies the Boolean value returned by the condition. If the Boolean value is true, then the assertion passes the test case.
2. assertEquals(String ExpectedTitle, String ActualTitle);
3. assertNotNull(String titleValue);

## 10. How to get element attribute value in selenium ?
```java
driver.get("https://www.google.com");
WebElement element = driver.findElement(By.id("uid"));
String str = element.getAttribute("value");
System.out.println(str);
```

## 11. How to check page title in selenium ?
```java
driver.get("https://www.google.com");
String str = driver.getTitle();
assertEquals(str,"Facebook");
```

In our automation framework we have a method getPageTitle() in BasePage abstract class which is common for all the page classes. This promotes reusability.
```java
public String getPageTitle(){
System.out.println("Returning Title");
return driver.getTitle();
}
```
## 12. How to handle alerts in selenium?
There are 3 types of javascript popup
1. Alert - contains only ok button
2. Confirmation - contains ok and cancel button
3. Prompt - also contains text
We cannot move the popup.We cannot inspect the popup.

```java
driver.get("https://www.google.com");
Alert alert = driver.switchTo.alert();
alert.accept();
driver.switchTo.defaultContent();
```
Prompt alert
```java
driver.get("https://www.google.com");
Alert alert = driver.switchTo.alert();
alert.sendKeys("Yes");
alert.accept();
driver.switchTo.defaultContent();
```

## 13. What are xpath axis?
Xpath axis are used to find complex elements.

```java
  <div class="group">
    <label>Password</>
    <span>
     <input class="is_required" type="password" id="passwd" name="passwd" value="">
    </span>
  </div>
```
### 1. Parent -> Selects the parent of the current node
//input[@id='passwd']//parent::span

### 2. Ancestor -> The ancestor axis selects all ancestors element (grandparent, parent, etc.) of the current node as shown in the below screen.
//input[@id='passwd']//ancestor::div

### 3. Following-sibling -> Selects the following siblings of the context node. Siblings are at the same level of the current node.
//label[text()='Password']//following-sibling::span

### 4. Following -> Selects all the elements following the current node.
//label[text()='Password']//following::input

## 14. Difference between get and navigate method in WebDriver?

1. driver.navigate.to("https://www.google.com");
2. driver.navigate().refresh();
3. driver.navigate().back();
4. driver.navigate().forward();

`get method` -> a) The get() method takes a string URL as a parameter and returns nothing.
This method opens the specified URL in the current browser window. URL must be in the form of https://www.google.com. If the HTTPS is not included then it will throw a message “Cannot navigate to invalid URL”.

The `getTitle()` method takes nothing as a parameter and returns the page title of the currently loaded web page. If the web page has no title, it will return a null String.

The `getText()` method accepts nothing as a parameter and returns a string value.
This method is used to retrieve the inner text of the specified element.

`getCssValue() : String`
The `getCssValue()` method accepts nothing as a parameter and returns a String value.
This method is used to fetch the value of the CSS property of the given web element when it is invoked.

`getAttribute(String Name) : String`
a) The getAttribute() method takes the String as a parameter and returns a String value.
b) It is used to fetch or get the value of the attribute of the WebElement.

`close() : void`
a) The close method takes nothing as a parameter and returns nothing.
b) This method is used to close only the browser window that web driver is currently controlling.

`quit() : void`
a) The quit() method accepts nothing as a parameter and returns nothing.
b) This method is used to close all windows opened by WebDriver.

### difference between get and navigate method of selenium WebDriver?
driver.get() used to launch a particular website url, whereas driver.navigate().to() is also used to launch the particular website by passing the URL but we can use forward and backward button to navigate between the pages during test case writing.

Both are exactly same, both are synonyms of each other. In fact navigate.to() method is calling get() method internally.

Get Method takes only string as parameter, whereas navigate can take string as well URL instance as parameters.

## 15. Why do we need to typecast driver object?

```java
WebDriver driver = new ChromeDriver();
JavascriptExecutor jsExecutor = (JavascriptExecutor) driver;
TakesScreenshot ts = (TakesScreenshot) driver;
```

Why are we doing typecasting WebDriver instance to JavascriptExecutor or TakesScreenshot.

![img_1.png](img_1.png)

##### driver pointing to ChromeDriver class object does not has methods from JavascriptExecutor or TakesScreenshot, because  we are instantiating class using WebDriver interface.

![img_2.png](img_2.png)


## 16. How to get size of browser window in selenium?
Selenium provides a class named Dimension which can be used to get the current size of the browser window and set the new size of the browser window. Size means the height and width of the browser.

```java
Dimension currentDimension = driver.manage().window().getSize();
int height = currentDimension.getHeight();
int width = currentDimension.getWidth();
System.out.println("Current height: "+ height);
System.out.println("Current width: "+width);
```

## 17. How to unselect a checkbox?
```java
<input type="checkbox" id="vehicle1" name="vehicle1" value="Bike">
```
WebElement element=driver.findElement(By.id("#vehicle1"))

element.click();

## 18. How to handle no element found exception without using try catch or throws?
Ans - Use explicit wait time.

Here are different ways to handle NoSuchElementException in Selenium:
NoSuchElementException is thrown by the findElement() method in Selenium WebDriver when the desired web element cannot be located using the specified locator, such as ID, name, CSS Selector, or XPath.

1. `Dynamic values` -> Some web elements are very dynamic in nature. In such cases the specified locator cannot be accessed by Selenium WebDriver as its properties keep on changing causing NoSuchElementException.
   For example, while automating, the locator value was “//a[@class=’abc_123’]”, however while executing the test the class value got changed to “abc_456”.

We can handle this using contains or starts-with method.

2. `element not yet loaded` -> Some elements take time to load as there can be synchronization issues between app and selenium script and therefore we may get no such element exception.

We can handle this using dynamic wait time like explicit wait time.
```java
WebDriverWait wait =new WebDriverWait(driver, Duration.ofSeconds(10)
WebElement login=wait.until(ExpectedConditions.elementToBeClickable(By.xpath("//button[text()='login']")));
login.click();
```

3. `Incorrect locators`- fix the locator.

4. `Use try catch block` -> Surround the code block which you feel may throw a NoSuchElementException with a try-catch block.

5. Switch to Frame -> Some web elements are inside frame/ iframe and it is only discovered when you encounter an exception. Always check if the element is inside any frame and in such case switch to the frame/ iframe and then perform the action on the desired web element.

## 19. Different exceptions in selenium?
1. `No Such Element Exception` ->
2. `NoAlertPresentException Exception` -> Raised when an expected alert is not present. Happens when trying to interact with an alert that doesn’t exist..
    Handle alerts inside a try catch block.

 ```java
  try {
  Alert alert = driver.switchToAlert();
  }
  catch(){
  System.out.print("No alert present")
  }
 ```
   A good way to resolve this is to:

   Handle Alerts: Always check for and handle alerts before proceeding with any other interactions.
   Use Try-Catch: Encapsulate actions in a try-catch block and handle alerts if they appear.

3. `ElementNotInteractableException` ->
   Element Not Interactable Exception is raised when an element is found but is not interactable (e.g., it’s hidden or disabled).
   
   Resolution ->
   The primary resolution method for an ElementNotInteractableException is to ensure that the element is both visible and enabled before interacting with it.

4. `No Such window Exception` ->

## 20. If both implicit and explicit wait is defined, which one will execute first?
If you have both waits applied then both waits will be applicable in common scenarios.

1. Implicit wait -> driver.manage().timeouts().implicitlyWait(30, TimeUnit.SECONDS);
   It should throw NoSuchElementException after 30 seconds i.e. implicit wait timeout.

2. Explicit Wait -> WebDriverWait wait = new WebDriverWait(driver, Duration.ofSeconds(10));
   You will see WebDriver will poll at an interval of 500 MS for 10 seconds and will throw timeout exceptions as there is no such element.
  custom polling interval ->
  wait.pollingEvery(Duration.ofSeconds(2));

Now WebDriver will poll to check condition on an interval of 2 seconds and terminate after 10 seconds.

#### Let’s mix implicit and explicit wait and observe the behavior.
First driver will wait for implicit wait, if not found, it will apply explicit wait and keep polling for default interval.


## 21. Difference between Selenium 3 and Selenium 4?
 
#### Architecture
Selenium 4 uses the W3C protocol to standardize communication with browsers, while Selenium 3 uses the JSON wire protocol over HTTP

#### WebDriver Manager
WebDriver Manager in Selenium 4 automatically downloads the appropriate driver binaries based on the specified browsers, handles the configuration, and ensures compatibility.

#### Options class 
In Selenium 4, the DesiredCapabilities class has been deprecated, and the Options class has been introduced as a replacement for configuring and customizing the desired capabilities of browsers or browser drivers.

#### Relative Locators 
Selenium 4 introduces the concept of relative locators, which provide additional flexibility in locating web elements based on their relationship with other elements

#### New Exceptions
1. New Exceptions in Selenium 4.0
   ElementClickInterceptedException
   Element Click Intercepted Exception is raised when an element you try to click is not clickable because another element is blocking it

2.  ElementNotInteractableException
    Element Not Interactable Exception is raised when an element is found but is not interactable (e.g., it’s hidden or disabled).

 #### Deprecated exceptions ->
   ElementNotVisibleException
   Status: Deprecated in Selenium 3 and eliminated in Selenium 4.


## 22. How to handle shadow dom elements?

## 23. How to handle SSL certificates?
Create a ChromeOptions object, set the setAcceptInsecureCerts capability to true, and then create a ChromeDriver instance. The browser will then trust invalid certificates.

 ```java
//Create instance of ChromeOptions Class
ChromeOptions handlingSSL = new ChromeOptions();

//Using the accept insecure cert method with true as parameter to accept the untrusted certificate
handlingSSL.setAcceptInsecureCerts(true);
				
//Creating instance of Chrome driver by passing reference of ChromeOptions object
WebDriver driver = new ChromeDriver(handlingSSL);
```


## 24. How does fluent wait work?

Fluent wait can help you set polling intervals.Fluent wait in Selenium 4 is a more flexible and customizable way of implementing waits in your test automation scripts.
It's a more flexible type of explicit wait that allows users to define polling intervals, exceptions to ignore, and maximum timeout duration.
```java
//Declare and initialise a fluent wait
FluentWait wait = new FluentWait(driver);
//Specify the timout of the wait
wait.withTimeout(5000, TimeUnit.MILLISECONDS);
//Specify polling time
wait.pollingEvery(250, TimeUnit.MILLISECONDS);
//Instructs Fluent Wait to ignore NoSuchElementException during the polling period.
wait.ignoring(NoSuchElementException.class)

//This is how we specify the condition to wait on.
//This is what we will explore more in this chapter
wait.until(ExpectedConditions.alertIsPresent());
```

## 25. What are cookies? And how do you manage those using Selenium WebDriver? 
A cookie is a small piece of data that is sent from a website and stored in your computer. Cookies are mostly used to recognise the user and load the stored information.
It stores information using a key-value pair. It is a small piece of data sent from Web Application and stored in Web Browser, while the user is browsing that website.

driver.manage().addCookie(new Cookie("key", "value"));

Set<Cookie> cookies = driver.manage().getCookies();
System.out.println(cookies);

## 26. How to switch contexts? What are different contexts available using Selenium WebDriver?

## 27. How can you scroll a page up to a certain element?
JavaScriptExecutor is an interface that is used to execute JavaScript through selenium webdriver. The JavaScript Executor is a powerful feature of Selenium WebDriver that allows you to execute JavaScript code directly in the browser.

JavaScriptexecutor provides two methods:

1. ExecuteScript
2. ExecutrAsyncScript

 ```java
<JavaScriptexecutor js = (JavascriptExecutor) driver;
js.executeScript("window.scrollTo(0, document.body.scrollHeight)");
 ```

The scrollIntoView() method is a JavaScript method that can be used to scroll an HTML element into the viewport. When called on an element, it will scroll the element’s parent container so that the element becomes visible in the viewport.

```java
JavascriptExecutor js = (JavascriptExecutor) driver;
js.executeScript(“arguments[0].scrollIntoView();”, webElement);
```


## 28. How to handle permission popups in selenium?
These are browser popups, generated by browser.
 ```java
ChromeOptions options = new ChromeOptions();
options.addArguments("disable-notification");
WebDriver driver = new ChromeDriver(options);
```

## 30. How to handle calendar in selenium?










