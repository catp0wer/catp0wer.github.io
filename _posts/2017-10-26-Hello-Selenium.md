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
[Download Selenium for Java](http://www.seleniumhq.org/download/)

![_config.yml]({{ site.baseurl }}/images/Selenium-weather1.PNG){:height="216px" width="432px"}



Put it in a location you want Selenium to be and remember the location. The path will be necessary when creating our project in the IDE.


##### Geckodriver
[Downloaded GeckoDriver](https://github.com/mozilla/geckodriver/releases)

 I put it in `C:\Windows` , because this path is in environment variables by default.
Adding the path is necessary for Selenium to execute GeckoDriver, otherwise you will see the following error when you run the test:
`‘X’ is not recognized as an internal or external command, operable program or batch file.`

You can add your path by right-clicking on `My Computer` and selecting `Properties`. 
Go to `Advanced` -> `Environmental Variables` -> `Path` -> `Edit` -> Add the path where you put your `Geckodriver.exe`.


![_config.yml]({{ site.baseurl }}/images/Selenium-weather17.JPG)

![_config.yml]({{ site.baseurl }}/images/Seleniu-weather18.JPG)

![_config.yml]({{ site.baseurl }}/images/Selenium-weather19.JPG)



##### IntelliJ IDEA IDE
[Download the community edition of IntelliJ IDEA IDE](https://www.jetbrains.com/idea/download/#section=windows), which is free.

##### Firefox
[Download Firefox](https://www.mozilla.org/en-US/firefox/new/)


It is recommended to have the last versions of all these components above for better compatibility. However, this tutorial was tested with:

 * Firefox 56.0.1
 * Geckodriver - v0.19.0-win64
 * Selenium -3.6.0




### The application 
The application opens Firefox, navigates to [https://www.google.com](https://www.google.com) and searches for ‘weather in Chisinau’.

There are a few steps we need to do to create our program: 
1.	Create a project in the IDE
2.	Write the code 
	* Create a WebDriver instance.
	* Navigate to a Web page [https://www.google.com](https://www.google.com).
	* Find the HTML element (search field, search button) on the Web page.
	* Perform an action on the found element (fill the field, click on button).
3.	Run the program

##### Create a project in IDE 
Click on `File tab` -> `New` -> `Project`

![_config.yml]({{ site.baseurl }}/images/Selenium-weather2.PNG)

Don’t select anything in Additional Libraries and Frameworks.

![_config.yml]({{ site.baseurl }}/images/Selenium-weather3.PNG)

![_config.yml]({{ site.baseurl }}/images/Selenium-weather4.PNG)

Enter the name of the project and project location.

![_config.yml]({{ site.baseurl }}/images/Selenium-weather5.PNG)

This is how an empty main class looks like – the entry point of every program:

![_config.yml]({{ site.baseurl }}/images/Selenium-weather6.JPG)

Now we need to add `Selenium libs` to be able to use it, go to `File` -> `Project Structure` -> `Modules` -> `Dependencies tab` -> Click on `Plus green` button -> Select `1 JARS or directories` -> Go to location where Selenium is downloaded and add all `.jar` files.

![_config.yml]({{ site.baseurl }}/images/Selenium-weather7.PNG)

##### Write the code

###### Create a WebDriver instance.

Firstly we need to create and instantiate a Firefox Driver object:

{% highlight java %}
WebDriver driver = new FirefoxDriver();
{% endhighlight %}

You will notice that `WebDriver` and `FirefoxDriver` will be in *red*. 


![_config.yml]({{ site.baseurl }}/images/Selenium-weather8.JPG)

We need to import some classes. For this just right-click on `WebDriver` and press `Alt+Enter` and the class will be automatically imported.
Do the same for `FirefoxDriver`.

![_config.yml]({{ site.baseurl }}/images/Selenium-weather9.JPG)

![_config.yml]({{ site.baseurl }}/images/Selenium-weather10.JPG)

###### Navigate to a Web site
To navigate to a web site we use the `GET` method in which we specify the URL we need:

{% highlight java %}
driver.get("http://www.google.com");
{% endhighlight %}

###### Inspect Element

To find an element on the page in order to fill it in or to click on it, you need to inspect it, in other words to find the `HTML` code for it.
To do so right-click and select `Inspect element`.


![_config.yml]({{ site.baseurl }}/images/Selenium-weather11.PNG)

Click on the first icon and click on the search field.
You can see that the `HTML` code which represents this field is highlighted.

![_config.yml]({{ site.baseurl }}/images/Selenium-weather12.JPG)

In the code which is highlighted we can extract the `name` or the `id` which identifies this field:

![_config.yml]({{ site.baseurl }}/images/Selenium-weather13.JPG)

I choose to use the `name`, because it is shorter.
To find the element we use the `findElement` method specifying by which `attribute` it should search.
In our case it searches by `name` which should be equal to `q`. Also we use the `sendKeys` method which types in our editable field the value “weather in Chisinau”. 
{% highlight java %}
driver.findElement(By.name("q")).sendKeys("weather in Chisinau");
{% endhighlight %}

To press the `Enter` key we also need to inspect the `Google Search` button (the same procedure as above).

![_config.yml]({{ site.baseurl }}/images/Selenium-weather14.PNG)


To click it we use the ```click``` method :

{% highlight java %}
driver.findElement(By.name("btnK")).click();
{% endhighlight %}



In the end we can close the browser by using the ```close``` method:
{% highlight java %}
driver.close();
{% endhighlight %}

##### Run the program
To run the program right-click on `Main class` and select `Run ‘Main’`.
Or you can go to the `Run` tab in the IDE and select `Run ‘Main’`.


![_config.yml]({{ site.baseurl }}/images/Selenium-weather15.PNG)

![_config.yml]({{ site.baseurl }}/images/Selenium-weather16.PNG)

##### Summary
This program is the simplest one which can serve as a base for more complicated scenarios. 
The starting point is initialization of Driver (`FirefoxDriver`, `ChromeDriver`, `InternetExplorerDriver`) and it depends on the browser you want to test on. After that you inspect the elements on the web page which you will interact with and locate them (by `name`, `id`, `XPath`, `CSS selector`) sending the command of interaction (fill, click, double click etc.). 

The complete code of the program: 
{% highlight java %}
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
{% endhighlight %}
