---
layout: post
title: The simplest Selenium application from scratch
---


Here I want to share my first Selenium application which launches a browser, opens a web-page and looks up the weather in a particular location by typing some text in the search box and clicking "Search". 

The following components are required: 

 - Selenium
 - Geckodriver
 - IntelliJ IDEA IDE 
 - Firefox 

This tutorial assumes you use Firefox, but it can be easily adapted to other browsers.
                                                                                                                                                                                      

##### Selenium
Download Selenium for Java from here: http://www.seleniumhq.org/download/

Screenshot

Put it in a location you want Selenium to be and remember the location. The path will be necessary when creating our project in IDE.


##### Geckodriver
Downloaded GeckoDriver from here:	 https://github.com/mozilla/geckodriver/releases

 I put it in `C:\Windows` , because this path is in environment variables by default.
Adding the path is necessary for Selenium to execute GeckoDriver, otherwise you will see the following error when you run the test:
`‘X’ is not recognized as an internal or external command, operable program or batch file.`

You can add your path by clicking on `My Computer` and selecting `Properties`. 
Go to `Advanced` -> `Environmental Variables` -> `Path` -> Paste the path where you put your Geckodriver exe.



On Windows systems you can change the system path by right-clicking `My Computer` and choosing `Properties`. In the dialogue that appears, navigate `Advanced` -> `Environmental Variables `-> `Path`

##### IntelliJ IDEA IDE
Download the community edition of IntelliJ IDEA IDE, which is free, from here and install it:
https://www.jetbrains.com/idea/download/#section=windows

##### Firefox
Download Firefox from here: https://www.mozilla.org/en-US/firefox/new/


It is recommended to have the last versions of all these components above for better compatibility.








### The application 
The application opens the Firefox, navigates to https://www.google.com and searches for ‘weather in Chisinau’.

There are a few steps we need to do to create our program: 
1.	[Create a project in IDE](#create-ide-project)
2.	Write the code 
i. Create a WebDriver instance.
ii.	Navigate to a Web page (https://www.google.com).
iii.	Find the HTML element (search field, search button) on the Web page.
iv.	Perform an action on the found element (fill the field, click on button).
3.	Run the program

##### Create a project in IDE (#create-ide-project)
Click on `File tab` -> `New` -> `Project`

Screenshot

Don’t select anything in Additional Libraries and Frameworks.

Screenshot
Screenshot
Enter the name of the project and project location.
Screenshot

This is how an empty main class looks like – the entry point of every program.

Screenshot

Now we need to add `Selenium libs` to be able to use it -> Go to `File` -> `Project Structure` -> `Modules` -> `Dependencies tab` -> Click on `Plus green` button -> Select `1 JARS or directories` -> Go to location where the Selenium is downloaded and add all `.jar` files.

Screenshot

##### Write the code

###### Create a WebDriver instance.

Firstly we need to create and instantiate a Firefox Driver object:

```java
WebDriver driver = new FirefoxDriver();
```

You will notice that `WebDriver` and `FirefoxDriver` will be in *red*. 



Screenshot

We need to import some classes. For this just right-click on `WebDriver` and press `Alt+Enter` and the class will be automatically imported.
Do the same for `FirefoxDriver`.

Screenshot

###### Navigate to a Web site
To navigate to a web site we use the get method in which we specify the URL we need:

```java
driver.get("http://www.google.com");
```

###### Inspect Element

To find an element on the page in order to fill it in or to click on it, you need to inspect it, in other words to find the `HTML` code for it.
To do so right-click and select `Inspect element`.


Screenshot

Click on the first icon and click on the search field.
You can see that the `HTML` code which represents this field is highlighted.

Screenshot

In the code which is highlighted we can extract the `name` or the `id` which identifies this field:

Screenshot

I choose to use the `name`, because it is shorter.
To find the element we use the `findElement` method specifying by which `attribute` it should search.
In our case it searches `by name` which should be equal to ‘q’. Also we use the `sendKeys` method which types in our editable field the value “weather in Chisinau”. 
```java
driver.findElement(By.name("q")).sendKeys("weather in Chisinau");
```

To press the `Enter` key we also need to inspect button `Google Search` (the same procedure as above).

Screenshot


To click on it we use the ```click``` method :

```java
driver.findElement(By.name("btnK")).click();
```



In the end we can close the browser by using the ```close``` method:
```java
driver.close();
```

##### Run the program
To run the program right-click on `Main class` and select `Run ‘Main’`.
Or you can go to Run tab in the IDE and select `Run ‘Main’`.


Screenshot

##### Summary
This program is the simplest one which can serve as a base for more complicated scenarios. 
The starting point is initialization of Driver (`FirefoxDriver`, `ChromeDriver`, `InternetExplorerDriver`) and it depends on the browser you want to test on. After that you inspect the elements on the web page which you will interact with and locate them (`by` `name`, `id`, `XPath`, `CSS selector`) sending the command of interaction (fill, click, double click etc.). 

The complete code of the program: 
```java
package com.company;

import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.firefox.FirefoxDriver;


public class Main {

    public static void main(String[] args) {
       WebDriver driver = new FirefoxDriver();
        driver.get("http://www.google.com");
        driver.findElement(By.name("q")).sendKeys("weather in Chisinau");
        driver.findElement(By.name("btnK")).click();
        driver.close();
    }
}
```
