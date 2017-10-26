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


