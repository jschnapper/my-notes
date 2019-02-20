# NODE

### Fundamentals
* Just creating a file in the project does not mean it will be executed. Make sure the file is required in some part of the project structure. Does not even need to export anything as long as it is simply required.
```js
require('./path/to/file');
```
* Order of `require` statements matters for execution. Check to make sure you aren't referencing something that requires something before it is executed