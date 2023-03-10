#### Exercise1.1

## 1.When a user enters an URL in the browser, how does the browser fetch the desired result ? Explain this with the below in mind and Demonstrate this by drawing a diagram for the same.
####  a).What is the main functionality of the browser?
####  b).High Level Components of a browser.
####  c).Rendering engine and its use.
####  d).Parsers (HTML, CSS, etc.)
####  e).Script Processors.
####  f).Tree constructing.
####  g).Order of script processing
####  h).Layout and Painting

# When a user enters an URL in the browser, how does the browser fetch the desired result ?

Ans.
#### Before we answer this question we will need to know more about the browser itself, such what a browser consists of, what is its basic but main functionality, etc. We will answer it one by one.
###  What is Browser?
!
![browser](https://user-images.githubusercontent.com/29350720/224015760-0281e63a-b1f8-4099-a58d-fcbbcece8aae.jpg)


  A browser is a software program that is used to explore, retrieve, and display the information available on the World Wide Web. 
This information may be in the form of pictures, web pages, videos, and other files that all are connected via hyperlinks and categorized with the help of URLs (Uniform Resource Identifiers).
Browsers' user interface have a lot in common with each other. Among the common user interface elements are:

-   Address bar for inserting the URI
-   Back and forward buttons
-   Bookmarking options
-   A refresh and stop buttons for refreshing and stopping the loading of current documents
Home button that gets you to your home page.

### How Website works?

Let’s start normal way of using the internet. You visit a website like www.linkedin.com
The moment you enter this address in your browser and you hit ENTER, a lot of different things happen:
-  The URL gets resolved(using DNS)
-  A Request is sent to the server of the website
-  The response of the server is parsed
-  The page is rendered and displayed

### Steps for user enters an URL in the browser and fetch the desired result ,
![url steps](https://user-images.githubusercontent.com/29350720/224009090-cb104022-023b-4569-b267-7ccd8117e01d.jpg)


For now, let's imagine that the "web is a road". On "one end of the road is the client", which is like your "house". On the "other end of the road is the server", which is a "shop" you want to buy something from.

1. **Your internet connection**: 
Allows you to send and receive data on the web. It's basically like the street between your house and the shop.
2. **TCP/IP**: 
Transmission Control Protocol and Internet Protocol are communication protocols that define how data should travel across the internet. This is like the transport mechanisms that let you place an order, go to the shop, and buy your goods. In our example, this is like a car or a bike (or however else you might get around).
3. **DNS**:
Domain Name System is like an address book for websites. When you type a web address in your browser, the browser looks at the DNS to find the website's IP address before it can retrieve the website. The browser needs to find out which server the website lives on, so it can send HTTP messages to the right place (see below). This is like looking up the address of the shop so you can access it.
4. **HTTP**: 
Hypertext Transfer Protocol is an application protocol that defines a language for clients and servers to speak to each other. This is like the language you use to order your goods.
    - Component files: 
        A website is made up of many different files, which are like the different parts of the goods you buy from the shop. These files come in two main types:
    - Code files: 
        Websites are built primarily from HTML, CSS, and JavaScript, though you'll meet other technologies a bit later.
        Assets: This is a collective name for all the other stuff that makes up a website, such as images, music, video, Word documents, and PDFs.

- When you type a web address into your browser (for our analogy that's like walking to the shop):

1. The browser goes to the DNS server, and finds the real address of the server that the website lives on (you find the address of the shop).
2. The browser sends an HTTP request message to the server, asking it to send a copy of the website to the client (you go to the shop and order your goods). This message, and all other data sent between the client and the server, is sent across your internet connection using TCP/IP.
3. If the server approves the client's request, the server sends the client a "200 OK" message, which means "Of course you can look at that website! Here it is", and then starts sending the website's files to the browser as a series of small chunks called data packets (the shop gives you your goods, and you bring them back to your house).
4. The browser assembles the small chunks into a complete web page and displays it to you (the goods arrive at your door — new shiny stuff, awesome!).

## DNS Resolution:

The DNS Resolution process starts when the user types a URL address on the browser and hits Enter. At this point, the browser asks the operating system for a specific page, in this case google.com.

![image](https://user-images.githubusercontent.com/113002603/193535285-39ef00c9-3536-4a64-8bfc-55034f9a268e.png)

- **Step 1: OS Recursive Query to DNS Resolver**

  Since the operating system doesn’t know where “www.google.com” is, it queries a DNS resolver. The query the OS sends to the DNS Resolver has a special flag that tells it is a “recursive query.” This means that the resolver must complete the recursion and the response must be either an IP address or an error.
   At this point, the resolver goes through a process called recursion to convert the domain name into an IP address.

- **Step 2: DNS Resolver Iterative Query to the Root Server**

  The resolver starts by querying one of the root DNS servers for the IP of “www.google.com.” This query does not have the recursive flag and therefore is an “iterative query,” meaning its response must be an address, the location of an authoritative name server, or an error.
  There are 13 root server clusters named A-M with servers in over 380 locations. They are managed by 12 different organizations that report to the Internet Assigned Numbers Authority (IANA), such as Verisign.

- **Step 3: Root Server Response**

  These root servers hold the locations of all of the top level domains (TLDs) such as .com, .de, .io, and newer generic TLDs such as .camera.
The root doesn’t have the IP info for “www.google.com,” but it knows that .com might know, so it returns the location of the .com servers.

- **Step 4:  DNS Resolver Iterative Query to the TLD Server**

  Next the resolver queries one of the .com name servers for the location of google.com. Like the Root Servers, each of the TLDs have 4-13 clustered name servers existing in many locations. There are two types of TLDs: country codes (ccTLDs) run by government organizations, and generic (gTLDs). Every gTLD has a different commercial entity responsible for running these servers. In this case, we will be using the gTLD servers controlled by Verisign, who run the .com, .net, .edu, and .gov among gTLDs.

- **Step 5: TLD Server Response**

  Each TLD server holds a list of all of the authoritative name servers for each domain in the TLD. For example, each of the 13 .com gTLD servers has a list with all of the name servers for every single .com domain. The .com gTLD server does not have the IP addresses for google.com, but it knows the location of google.com’s name servers. The .com gTLD server responds with a list of all of google.com’s NS records. In this case Google has four name servers, “ns1.google.com” to “ns4.google.com.”

- **Step 6: DNS Resolver Iterative Query to the Google.com NS**

  Finally, the DNS resolver queries one of Google’s name server for the IP of “www.google.com.”

- **Step 7: Google.com NS Response**

  This time the queried Name Server knows the IPs and responds with an A or AAAA address record (depending on the query type) for IPv4 and IPv6, respectively.

- **Step 8: DNS Resolver Response to OS**

  At this point the resolver has finished the recursion process and is able to respond to the end user’s operating system with an IP address.



# a) What is the main functionality of the browser?
The main functionality of a browser is to represent the resources we choose by requesting it from server. This resource can be html, video, pdf, image or anything which the server sends. The browser will just process this response and represent it to us with


To achieve this, browser has some high level components 

#  b).High Level Components of a browser.
## Components of a Web Browser:-


![highlevel 1](https://user-images.githubusercontent.com/29350720/224016096-915c9b9b-b0dc-447c-9da7-c9276b118adf.jpg)

1. #### The User Interface :
The user interface is the space where User interacts with the browser. It includes the address bar, back and next buttons, home button, refresh and stop, bookmark option, etc. Every other part, except the window where requested web page is displayed, comes under it.

2. #### The Browser Engine: 
The browser engine works as a bridge between the User interface and the rendering engine. According to the inputs from various user interfaces, it queries and manipulates the rendering engine.

3. #### The Rendering Engine: 
The rendering engine, as the name suggests is responsible for rendering the requested web page on the browser screen. The rendering engine interprets the HTML, XML documents and images that are formatted using CSS and generates the layout that is displayed in the User Interface. However, using plugins or extensions, it can display other types data also. Different browsers user different rendering engines:
- Internet Explorer: Trident
- Firefox & other Mozilla browsers: Gecko
- Chrome & Opera 15+: Blink
- Chrome (iPhone) & Safari: Webkit
For example if the requested content is HTML, the rendering engine parses HTML and CSS, and displays the parsed content on the screen.

4. #### Networking: 
Component of the browser which retrieves the URLs using the common internet protocols of HTTP or FTP. The networking component handles all aspects of Internet communication and security. The network component may implement a cache of retrieved documents in order to reduce network traffic.

5. #### UI Backend: 
UI backend is used for drawing basic widgets like combo boxes and windows. This backend exposes a generic interface that is not platform specific. It underneath uses operating system user interface methods.

6. #### JavaScript Interpreter: 
It is the component of the browser which interprets and executes the javascript code embedded in a website. The interpreted results are sent to the rendering engine for display. If the script is external then first the resource is fetched from the network. Parser keeps on hold until the script is executed.

7. #### Data Storage: 
This is a persistence layer. Browsers support storage mechanisms such as localStorage, IndexedDB, WebSQL and FileSystem. It is a small database created on the local drive of the computer where the browser is installed. It manages user data such as cache, cookies, bookmarks and preferences.

# c).Rendering engine and its use.

# Rendering engine: 

The networking layer will start sending the contents of the requested documents to the rendering engine in chunks of 8KBs.

![image](https://user-images.githubusercontent.com/113002603/193411687-8c427e9e-f140-49b6-931f-2a0d6adf57e4.png)

We describe five steps in the critical rendering path.
Those are :- 

1.Parsing:
Once the browser receives the first chunk of data, it can begin parsing the information received. Parsing is the step the browser takes to turn the data it receives over the network into the DOM and CSSOM, which is used by the renderer to paint a page to the screen.

- Building the DOM tree:
![building dom](https://user-images.githubusercontent.com/29350720/224015884-6d8731da-2e98-449e-a2f8-dd44913c097d.png)

  The first step is processing the HTML markup and building the DOM tree. HTML parsing involves tokenization and tree construction.
The DOM is the internal representation of the markup for the browser. The DOM is also exposed, and can be manipulated through various APIs in JavaScript.

![image](https://user-images.githubusercontent.com/113002603/193412275-11315a81-8eda-4866-8f79-55be09cc6f07.png)

  When the parser finds non-blocking resources, such as an image, the browser will request those resources and continue parsing. Parsing can continue when a CSS file is encountered, but <script> tags—particularly those without an async or defer attribute—block rendering, and pause the parsing of HTML.

**Preload scanner**:
While the browser builds the DOM tree, this process occupies the main thread. As this happens, the preload scanner will parse through the content available and request high priority resources like CSS, JavaScript, and web fonts. Thanks to the preload scanner, we don't have to wait until the parser finds a reference to an external resource to request it.

2. **Building the CSSOM**:

  The second step in the critical rendering path is processing CSS and building the CSSOM tree. The CSS object model is similar to the DOM. 
The browser converts the CSS rules into a map of styles it can understand and work with. 
The browser goes through each rule set in the CSS, creating a tree of nodes with parent, child, and sibling relationships based on the CSS selectors.

## Render:
![rendering tree](https://user-images.githubusercontent.com/29350720/224016320-9923f8f3-cecf-4538-b60a-00fc6d1be1f3.jpg)

  Rendering steps include style, layout, paint and, in some cases, compositing. 
![rendering tree2](https://user-images.githubusercontent.com/29350720/224016647-624f9b8c-36a3-4182-a2f1-7bc4ba8f6a4e.jpg)

The CSSOM and DOM trees created in the parsing step are combined into a render tree which is then used to compute the layout of every visible element, which is then painted to the screen.

3. **Style**:

  The third step in the critical rendering path is combining the DOM and CSSOM into a **render tree**. The computed style tree, or render tree, construction starts with the root of the DOM tree, traversing each visible node.
Tags that aren't going to be displayed, like the <head> and its children and any nodes with display: none, such as the script { display: none; }

4. **Layout**:

  The fourth step in the critical rendering path is running layout on the render tree to compute the geometry of each node.

  After the construction of the render tree, it goes through a *layout process* of the render tree. When the renderer is created and added to the tree, it does not have a position and size. The process of calculating these values is called layout or reflow. 
  *Layout* is the process by which the width, height, and location of all the nodes in the render tree are determined, plus the determination of the size and position of each object on the page.
  *Reflow* is any subsequent size and position determination of any part of the page or the entire document.

  The position of the root renderer is 0,0 and its dimensions are the viewport–the visible part of the browser window.
All renderers have a “layout” or “reflow” method, each renderer invokes the layout method of its children that need layout.

5. Paint:
  The last step in the critical rendering path is painting the individual nodes to the screen, the first occurrence of which is called the first meaningful paint. 
In the painting or rasterization phase, the browser converts each box calculated in the layout phase to actual pixels on the screen. 
Painting involves drawing every visual part of an element to the screen, including text, colors, borders, shadows, and replaced elements like buttons and images. 
The browser needs to do this super quickly.

**Compositing**:

  When sections of the document are drawn in different layers, overlapping each other, compositing is necessary to ensure they are drawn to the screen in the right order and the content is rendered correctly.

# (d). Parsers
When a browser receives the HTML and CSS code for a webpage, it uses parsers to analyze the code and construct a tree-like structure known as the Document Object Model (DOM) tree. The DOM tree represents the content of the webpage in a hierarchical manner and allows the browser to determine how the content should be displayed on the page.

The process of parsing the HTML and CSS code involves breaking down the code into smaller pieces and analyzing each piece to determine its meaning and how it relates to other pieces of the code. The HTML parser uses the syntax of the HTML language to identify the different elements on the page, such as headings, paragraphs, and links. It then organizes these elements into a hierarchical structure that represents the content and structure of the page.

The CSS parser analyzes the styles defined in the CSS code and applies them to the elements in the DOM tree. This allows the browser to determine the appearance of each element on the page, such as its color, font, and size.

Parsing is important because it allows the browser to understand the content and structure of the webpage and determine how it should be displayed to the user. Without parsing, the browser would not be able to accurately render the content and styles of the page and the user would not be able to view the page as intended by the web developer.

# (e). Script Processors
Script processors are components of a web browser that are responsible for executing JavaScript code on a webpage. JavaScript is a programming language that is commonly used on the web to add interactivity and dynamic behavior to webpages. It allows web developers to create functions that manipulate the content and appearance of a page, and interact with the user.

When the rendering engine encounters JavaScript code while constructing the DOM tree, it passes the code to the script processors to be executed. The script processors analyze the code and execute it in the order in which it appears on the page. This can include functions that manipulate the styles and content of the page, or interact with the user through events such as clicking a button or hovering over an element.

Script processors are important because they allow web developers to add dynamic and interactive behavior to their pages. Without script processors, webpages would be static and unable to respond to user input or change their content and appearance.

# (f). Tree construction: algorithm
![tree constructor](https://user-images.githubusercontent.com/29350720/224016952-30377ac6-d4b4-45d7-8b53-76ee2c3b1cb4.jpg)

Tree construction is a process that is used by a web browser to represent the content and structure of a webpage in a hierarchical manner. This is done using a tree-like structure known as the Document Object Model (DOM) tree.

![tree constructorn example for html](https://user-images.githubusercontent.com/29350720/224017935-d638379d-116f-4f18-bbdb-b0351003b80b.jpg)

The process of tree construction begins when the browser receives the HTML code for a webpage. The browser uses a parser to analyze the HTML code and identify the different elements on the page, such as headings, paragraphs, and links. It then organizes these elements into a hierarchical structure, with each element becoming a node in the tree. The root node of the tree represents the entire webpage, and each child node represents a specific element on the page.

Tree construction is important because it allows the browser to understand the content and structure of the webpage in a way that it can use to determine how the page should be displayed to the user. The DOM tree provides a representation of the page that the rendering engine can use to render the content and apply styles, and that JavaScript code can use to manipulate the page. Without tree construction, the browser would not be able to accurately render the content of the page.

# (g). Order of processing scripts
When a browser processes the HTML, CSS, and JavaScript code on a webpage, it follows a specific order to ensure that the page is rendered correctly. The order of script processing is as follows:

The HTML code is parsed and the DOM tree is constructed based on the HTML elements on the page.
The CSS code is parsed and used to apply styles to the elements in the DOM tree.
The JavaScript code is executed, which may manipulate the styles and content of the page.
This order is important because it ensures that the styles are applied to the correct elements on the page and that any JavaScript code can manipulate the correct styles and content. If the order were reversed, the JavaScript code would not have access to the correct styles and the page may not be rendered correctly.

# (h). Layout and Painting
After the browser has parsed the HTML, CSS, and JavaScript code on a webpage and constructed the DOM tree, it uses a process called layout to determine the position and size of each element on the page. This process involves calculating the position of each element based on its relationship to other elements in the DOM tree, and the styles applied to it.

Once the layout has been determined, the browser uses a process called painting to draw the elements onto the screen and display the final version of the webpage to the user. This involves drawing each element onto a canvas, which is then displayed to the user.

The processes of layout and painting are important because they allow the browser to accurately render the content and styles of the webpage and display it to the user in a user-friendly manner. Without these processes, the content of the page would not be positioned correctly and the user would not be able to see the intended layout of the page.

## References:
               - 1. https://taligarsiel.com/Projects/howbrowserswork1.htm#The_browser_main_functionality
               - 2. https://www.youtube.com/watch?v=vB_Z3JjkVwU&t=134s
               - 3. https://medium.com/@maneesa/what-happens-when-you-type-an-url-in-the-browser-and-press-enter-bb0aa2449c1a
               - 4. https://www.educative.io/blog/behind-the-screens-what-happens-when-you-type-a-url-in-a-browser






