# Deployment setup with Node and Heroku

1. In start file, allow for dynamic port binding with 
``` js
const PORT = process.env.PORT || 5000
/* 
5000 is arbitrary. 
This syntax is to indicate difference between 
production and developlment. 
Use port 5000 when on development
*/
```
2. In `package.json`, indicate `engines` with the version of node and npm developing on to ensure that deployment is successful and using same version of node and npm – prevents crashes if Heroku defaults to older version that doesn't have same functionality
```js
"engines": {
  "node": "10.10.0",
  "npm": "5.6.1"
}
```
`engines` is used to specify the versions and alternative runtime. Can use a version number or range. 
3. Instruct Heroku what command to run to start the server. Indicate in `scripts`.
```js 
"scripts": {
  "start": "node index,js"
}
```
Heroku is going to attempt to execute the script `start`. When Heroku attempts to execute this, it will run the command `node index.js`
4. Create `.gitignore` because don't want to include dependencies since Heroku will do that