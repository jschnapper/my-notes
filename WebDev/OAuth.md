# OAuth


## Passport
If using Node and Express. It's helpful to use the `Passport` library which contains two necessary components.

`Passport` handles the general authentication structure.

You then need at least one **passport strategy**. Such as Google, Facebook, or email/password authentication. Each strategy is considered a separate component and needs to be installed. 

`done` is a parameter that is a function returned during the callback function execution to indicate the callback is complete. **Call this function when it is returned in order to continue the flow**. `done` has two parameters
1. An error object to communicate to passport that something went wrong
2. The object that was retrieved from the process 

Passport can manage authentication in many ways. One way is through **cookies**. *Express does not know how to handle cookies, so you will need a helper library* `cookie-session`.

Passport automatically attaches a `user` property to all `req` objects. It also attaches `logout()`. For `logout`, passport takes the cookie that contains the user id and kills the id. `req.user` after the `logout()` is destroyed. 
```js
// contains all the user information
req.user
// logout function for authentication
req.logout()
```

## Google OAuth
To enable Google OAuth API
1. create a new project at **console.developers.google.com**
2. Enable APIs for that project
3. Search for **Google+ Api** this is what is needed in order to authenticate with google
4. Create credentials
5. Selected **OAuth Client ID**

## Tokens
**Access Tokens** provide temporary access to user information such that it can be edited
**Refresh Tokens** are necessary to ask for an access token for a specific user after the access token expires