# Authentication

**HTTP is stateless**
This means that there is no way to share information between two different requests.

**Example**
**Information between requests is not shared**
*When a client logs in, this sends a request to the server and the server approves this request. If the client were then to ask to do something, the server doesn't know who it is because it is separate request from the login. The information was not shared. So the user information would have to be sent along with this separate request so the server knows who you are.* 

In this way, when you log in, the server often sends a **token**, this private, access token identifies the user as you each time you make a subsequent request while you're logged in.

### Cookie Based Authentication
In the response sent back to browser after some process of authentication, we include a header that contains some property like `set-cookie` that is going to be set to some random token that serves as the unique identification of the person who logs in. 

**The browser will automatically strip the token from the response and store it in the browser's memory using a function we define (serializing the token). The browser will automatically append this cookie which each request sent to the server. (and deserialize to get the token back)**

The server will look at the token inside the cookie. 

