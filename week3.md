# Week 3 Quiz

1. What is HTML? What is CSS? What is Javascript?

HTML: Hypertext Markup Language. It's the core language in which information is transmitted via HTTP requests and rendered into webpages by browsers.

CSS: Cascading Style Sheets. CSS is used to style HTML documents.

Javascript: We didn't do anything with it this week in this version of the course, but my understanding is that Javascript is a language that is most widely used to provide responsive elements in a web page without retransmitting the whole page, generally by affecting the browser DOM. There are also Javascript-based frameworks such as node.js now that can be used as controllers, if I understand correctly.

2. What are the major parts of an HTTP request?

URL, verb/request type, parameters (if appropriate)

3. What are the major parts of an HTTP response?

Status code, payload/redirect (as appropriate)

4. How do you submit an HTTP POST request, with a "username" attribute set to "bob"? What if we wanted a GET request instead?

<form action="/path" method="post">
  <input type="text" name="username" value="bob">
</form>

site/path?username=bob

5. Why is it important for us, as web developers, to understand that HTTP is a "stateless" protocol?

You need to understand that every time a new request is sent to you or sent from you, there's no information about previous requests. Thus you need to have another way to store data and use it to construct the page you are sending each time. This week, we used the session cookie. More robust applications will generally be using a database.

6. If the internet is just HTTP requests/responses, why do we only use browsers to interface with web applications? Are there any other options?

Browsers turn the HTML sent into something readable by normal humans. One can also use a HTTP client, but then you simply get the raw HTML. There are also other protocols besides HTTP that can be used to transmit data, such as FTP.

7. What is MVC, and why is it important?

It's the basic layout for how modern (non-static) webpages are generated. The user makes a request to the controller, which then interacts with the model to get data, after which it either redirects the user or renders a view.

The below questions are about Sinatra:

8. At a high level, how are requests processed?

Requests are handled via main.rb (controller) via actions (get/post '/path' do blocks.) We use a session cookie as our model, do some data processing, and at some point (possibly after redirects) the controller renders a view, typically an ERB template that is presumably processed into straight HTML. 

9. In the controller/action, what's the difference between rendering and redirecting?

A render draws a new page for the user. A redirect sends them to a different action.

10. In the ERB view template, how do you show dynamic content?

You can insert Ruby code using <% %>, which effectively allows you to turn different parts of the website on or off. If you want to insert information from the controller and have it appear directly, you use <%= dynamic content goes here! %>

11. Given what you know about ERB templates, when do you suppose the ERB template is turned into HTML?

I would suspect it's after the controller has filled in the necessary variables and prior to being sent/rendered. However, I got a bug with rendering an ERB template and then changing a variable within a single action in the controller that makes me think it might not so cut and dried. (Sinatra might try to re-render a view if any of the variables used to construct that view are changed, perhaps?)

12. What's the role of instance variables in Sinatra?

Instance variables are valid only within an action. So far, they've been used to help control what is shown in an ERB template when the persistence of a session element is not necessary. 