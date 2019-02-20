# API keys

Always keep the secret key private. It is okay if the ClientID is shared, but not if the clientSecret is shared.


### Node

Create a config folder with a keys file. **Add this file to the `.gitignore` file**

Create an object assigned to `module.exports`

```js
module.exports = {
  clientID: 'nums',
  clientSecret: 'nums'
}
```

Import the file and the object where needed