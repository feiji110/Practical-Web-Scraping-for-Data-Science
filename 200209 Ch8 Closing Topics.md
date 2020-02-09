# An overview of other helpful tools and libraries 
# 8.1 Other tools
## 8.1.1 Alternative Python Libraries
+ Python3 and the requests,Beautiful Soup,and Selenium libraries

Python ecosystem also provides a wealth of other libraries to **handle HTTP messaing** 

+ built-in *urllib* module
+ [httplib2]( https://github.com/httplib2/httplib2) 
+ [urllib3](http://urllib3.readthedocs.io/)
+ [grequests]( https://pypi.python.org/pypi/grequests)
+ [aiohttp](http://aiohttp.readthedocs.io/)

+ Beautiful Soup library itself depends on an HTML parser to perform most of the bulk (n.大部分) parsing work, It is hence also possible to use these **lower-level parsers** directly should you wish to do so.
+ “lxml” and “html5lib” being popular alternatives .(the additional overhead added by Beautiful Soup causes some slowdown.though first dealing with other issues before scraping speed becomes a real concern)eg:setting up a parallel scraping mechanism.

## 8.1.2 [Scrapy](https://scrapy.org/) 
> Scrapy is a comprehensive Python library for crawling websites  and extracting structured
data from websites,which is also popular.
+ deal with both HTTP and HTML side of things,and provide a command-line(命令行) tool to quickly set up,debug,and deploy wep crawlers.
+ especially in cases where you have to write a **robust crawler**. as it provides many **sane defaults** for restarting scripts, crawling in parallel, data collection, and so on. 

####  [Scrapy Cloud](https://scrapinghub.com/scrapy-cloud)
+  a cloud platform for running web crawlers. 
+  This is helpful in cases where you want to quickly run your scraper on a bunch of servers without hosting these yourself. * But at a cost*.
+  An alternative would be to set up your scrapers on Amazon AWS or Google’s Cloud Platform.

+  A notable drawback of Scrapy is that is does not emulate(竞争，模仿) a full browser stack. Dealing with JavaScript will hence be troublesome using this library. 
+ There does exist a plug-in(插件) that **couples** “Splash” (a JavaScript rendering(表演，渲染) service) **with** Scrapy, though this approach is a little cumbersome(n.笨重，麻烦，troublesome) to set up and maintain.

## 8.1.3 Caching
+ it is a good idea to implement(实施) some **client-side** caching(缓存) solution while building  web scrapers, which will keep fetched web  pages in its “memory.”
 This **avoids** continuously hammering(锤击) web servers with requests over and over again, which is especially helpful during **development of your scripts**(脚本开发) (where you’ll oftentimes restart a script to see if a bug has been fixed, you get the results you expect, and so on).
 #### [CacheControl](http://cachecontrol.readthedocs.io/en/latest/)
 ````py 
 import requests 
 from cachecontrol import CacheControl

 session = requests.Session()
 cached_session = CacheControl(session)
# now can use cached_session like a normal session. 
# All GET requests will be cached.
````
