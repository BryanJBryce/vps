# vps

## Question #1

### Considering the audience is somebody already technical and willing to go into the details, but they don't know how the web works, could you writeup an explanation of the various technical things that have to happen from when a user starts at their browser through to when they receive a web page, and everything in between?

#### In order to make thinking and working in web technology more tractable to reason about we can think about web technology in terms of layers of abstraction.

#### Let's start with a high level of abstraction and move into lower levels from there: Your computer/browser is what we would call a client or frontend and the server(s) that hosts the website and data you want to access is the backend. When you enter a URL into your browser and hit, "enter" you begin a client request to the backend for a resource. (That's why we use the acronym URL, it stands for Uniform Resource Locator.) A resource can be a file to download, or a web page (which often consists of several files), etc.

#### The top level of that URL you entered, for example, google.com or neocities.org gets translated into a server IP address, something that looks more like: 206.128.79.176 or 2001:0db8:85a3:0000:0000:8a2e:0370:7334 that uniquely addresses the server from which you are requesting data. The request is routed and sent to that specific server. In order to get to its end destination the request may have to go through several other networks to reach the server you are addressing.

#### When the request arrives at the server the server looks at the next part of the URL you entered. For example: /cat-videos/42 and the server checks to see if that resource exists. If it doesn’t, the server usually responds letting your browser know that. If it finds the resource then it will send it back for your computer/browser to render.

#### Let’s go a layer deeper. The web can be used to make various types of requests. Let’s assume that you’re making an HTTP request which is the typical request protocol used for websites, it means Hypertext Transfer Protocol. Hypertext is just a fancy way of saying, “documents that contain links to other documents,” like the websites you know and love.

#### In order to make an HTTP request you have to follow the protocol (set of rules) required to make a valid request. 

#### The request line is the first part of the protocol that needs to be followed. The first part of the request line is the request method. There are different types of requests that you can make, you can request to only read a resource, this would use the GET request method. Or maybe you want to update a resource, like updating your phone number in an online profile, this would require a POST or PUT. And of course if you want to delete something you’d use the DELETE method. There are more methods but these are the most commonly used.

#### Next in the request line comes the address on the server of the resource, like we talked about before /cat-videos/42 is an example. And then the protocol being used, so the entire request line may look like this: GET /cat-videos/42 HTTP/1.0.

#### After the request line comes header fields which can be used to further specify the request with things like specifying the language of the resource or a data format or even implement security through passwords or tokens and cookies.

#### After the headers the request can optionally include a message body. When the request requires information to update the resource on the server such as with POST and PUT requests the body is required.

#### That’s a complete message that gets sent to the server of HTTP.

#### Let’s take a deeper look at what is happening with many types of web application servers.

#### Many times the applications servers have a proxy server that sits in front of them to route traffic, deflect security threats, etc. This proxy server will decide, for example, which application server is the least busy and send the request to that specific server over a private network. Once the application server receives the request it will parse the request and find or dynamically create the resource to respond with. To do this the application server may leverage a database, other application servers, third-party services, cloud storage buckets, etc.

#### Once the request is ready to be sent an HTTP response is formed. First comes the status. This is a set of predefined codes to quickly tell the client, we found it or we completed your request! here it is! (200), we don’t have this anymore, but you can find it here (302), we’re not sure what you’re talking about, we didn’t find that, (404), something went wrong on our end (500). And many more.

#### After the status line come response header fields, these are like the request header fields. If the request was for a webpage then perhaps the response header field will include the header Content-Type: text/html, etc.

#### After the headers comes the response body. This includes the resource that you were asking for the whole time. When the server is done construction the response it sends it back to your client/browser.

#### Let’s go a little deeper about how the browser shows the response. Let’s assume that the resource you asked for was an html page which came along with some css and Javascript. 

#### The HTML does what the acronym says (Hyperext Markup Language). It’s a structure for the web page content that includes designations for things like headers, paragraphs, links and tables. CSS (cascading style sheets) give the content it’s design, the location of the text, the colors and animations. Javascript can provide capabilities beyond the first two by editing the HTML in the browser. The job of the browser is to take all of these files and display the result of them to the user and accept input and perhaps make more requests.

Question #2

You are given the following work request. Assuming the dev and deployment environment is any you are familiar with (current or past work environs), and it's part of an existing web service which you can change the backend and frontend of, what would your development through software delivery steps look like? (i.e. what would you do to figure out the details of what you are implementing, how you'd implement it, etc).
Visiting the page (/hotcars), it queries all available cars. If only one car is available, it shows that car. Otherwise a list of possible cars is presented for selection.
Question #3

Have you ever had to deal with transitive dependencies in data, and if so what was your problem and resolution?
Coding Exercise

Write a program which pulls from the Star Wars API and reports a list of starships and ALL pilots who have used the starship. Which programming language you use, how it is done, and the rest are up to you. The exercise constraints:
The script should run from the alpine:latest docker image.
Report output in a readable manner as a list of starships and ALL pilots. Output format is up to you -- console or web.
Create a repository on github, push your code and Dockerfile to it, and send us the link.
Your end result should be something we can run, so please include instructions for running it that an engineer who might not be familiar with your tech stack could follow.
Email us when you are done.
Only submit your own work. You can use libraries and frameworks, but make sure you wrote the script itself.
The project is deliberately open-ended because we want to see how you build it--there is not any preferred way to get to the end result.
