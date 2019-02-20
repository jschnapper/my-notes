# MongoDB

MongoDB is **schemaless**. This means that within a collection, each record can have it's own distinct properties. The properties do not have to be the same. 

MongoDB is composed of many **collections**, like users or posts, and every collection has many different **records**. 

A record is a **js object** containing key-value pairs. 

### Mongoose
A js library to more easily interact with MongoDB

Mongoose creates a **model class** which represents an entire MongoDB collection. 
The model class has function attached to it that are meant to interact with the collection. 

Mongoose provides access to **model instances** – an instance is a js object representing a single record inside the collection.

*Using mongoose, however, does not have the advantage of having random properties for each record within a collection. Because mongoose wants to know ahead of time all the possible properties*. As a result, we must use `mongoose.Schema` to create a schema within a collection.

```js
// The below destructuring can also be written as
// const Schema = mongoose.Schema

const { Schema } = mongoose;
const exampleSchema = new Schema({
  value: Integer
});
```

**Mongoose does allow to freely add and subtract properties from the schema, and it will update accordingly.** 

Anytime you reach out to the database, this is an **asynchronous action**

A mongoose query returns a **promise**

### Hosting
1. You can install a local copy of MongoDB
OR
2. You can a remotely hosted instance, for instance, through mLab

With mLab, `database user` is not a user of the application, but the actual administrative accounts that can manage the database