## Classes

<dl>
<dt><a href="#Mongo">Mongo</a></dt>
<dd><p>Class representing the MongoDB Client Interface.</p>
</dd>
<dt><a href="#Insert">Insert</a></dt>
<dd><p>Class representing the MongoDB Insert Interface.</p>
</dd>
<dt><a href="#Get">Get</a></dt>
<dd><p>Class representing the MongoDB Get Interface.</p>
</dd>
<dt><a href="#Update">Update</a></dt>
<dd><p>Class representing the MongoDB Update Interface.</p>
</dd>
<dt><a href="#Delete">Delete</a></dt>
<dd><p>Class representing the MongoDB Delete Interface.</p>
</dd>
<dt><a href="#Aggregate">Aggregate</a></dt>
<dd><p>Class representing the MongoDB Delete Interface.</p>
</dd>
</dl>

## Typedefs

<dl>
<dt><a href="#User">User</a></dt>
<dd></dd>
<dt><a href="#AuthResponse">AuthResponse</a></dt>
<dd></dd>
</dl>

## External

<dl>
<dt><a href="#external_LiveQuery">LiveQuery</a></dt>
<dd><p>The LiveQuery Interface.</p>
</dd>
</dl>

<a name="Mongo"></a>

## Mongo
Class representing the MongoDB Client Interface.

**Kind**: global class  

* [Mongo](#Mongo)
    * [new Mongo(appId, url, options, realTime)](#new_Mongo_new)
    * [.get(collection)](#Mongo+get) ⇒ [<code>Get</code>](#Get)
    * [.insert(collection)](#Mongo+insert) ⇒ [<code>Insert</code>](#Insert)
    * [.update(collection)](#Mongo+update) ⇒ [<code>Update</code>](#Update)
    * [.delete(collection)](#Mongo+delete) ⇒ [<code>Delete</code>](#Delete)
    * [.aggr(collection)](#Mongo+aggr) ⇒ [<code>Delete</code>](#Delete)
    * [.liveQuery(collection)](#Mongo+liveQuery) ⇒ [<code>LiveQuery</code>](#external_LiveQuery)
    * [.profile(id)](#Mongo+profile) ⇒ <code>Promise</code>
    * [.editProfile(id, email, name, pass)](#Mongo+editProfile) ⇒ <code>Promise</code>
    * [.profiles()](#Mongo+profiles) ⇒ <code>Promise</code>
    * [.signIn(email, pass)](#Mongo+signIn) ⇒ [<code>Promise.&lt;AuthResponse&gt;</code>](#AuthResponse)
    * [.signUp(email, name, pass, role)](#Mongo+signUp) ⇒ [<code>Promise.&lt;AuthResponse&gt;</code>](#AuthResponse)

<a name="new_Mongo_new"></a>

### new Mongo(appId, url, options, realTime)
Create an instance of the MongoDB Client Interface.


| Param | Type |
| --- | --- |
| appId | <code>string</code> | 
| url | <code>string</code> | 
| options | <code>Object</code> | 
| realTime | <code>Object</code> | 

**Example**  
```js
import { API } from 'space-api';

const api = new API('my-project', 'http://localhost:8080');
const db = api.Mongo();
```
<a name="Mongo+get"></a>

### mongo.get(collection) ⇒ [<code>Get</code>](#Get)
Returns a MongoDB Get Object

**Kind**: instance method of [<code>Mongo</code>](#Mongo)  
**Returns**: [<code>Get</code>](#Get) - MongoDB Get Object  

| Param | Type | Description |
| --- | --- | --- |
| collection | <code>string</code> | The collection to query documents. |

<a name="Mongo+insert"></a>

### mongo.insert(collection) ⇒ [<code>Insert</code>](#Insert)
Returns a MongoDb Insert Object

**Kind**: instance method of [<code>Mongo</code>](#Mongo)  
**Returns**: [<code>Insert</code>](#Insert) - MongoDB Insert Object  

| Param | Type | Description |
| --- | --- | --- |
| collection | <code>string</code> | The collection to insert documents. |

<a name="Mongo+update"></a>

### mongo.update(collection) ⇒ [<code>Update</code>](#Update)
Returns a MongoDb Update Object

**Kind**: instance method of [<code>Mongo</code>](#Mongo)  
**Returns**: [<code>Update</code>](#Update) - MongoDB Update Object  

| Param | Type | Description |
| --- | --- | --- |
| collection | <code>string</code> | The collection to update documents. |

<a name="Mongo+delete"></a>

### mongo.delete(collection) ⇒ [<code>Delete</code>](#Delete)
Returns a MongoDb Delete Object

**Kind**: instance method of [<code>Mongo</code>](#Mongo)  
**Returns**: [<code>Delete</code>](#Delete) - MongoDB Insert Object  

| Param | Type | Description |
| --- | --- | --- |
| collection | <code>string</code> | The collection to delete documents in. |

<a name="Mongo+aggr"></a>

### mongo.aggr(collection) ⇒ [<code>Delete</code>](#Delete)
Returns a MongoDb Aggregate Object

**Kind**: instance method of [<code>Mongo</code>](#Mongo)  
**Returns**: [<code>Delete</code>](#Delete) - MongoDB Insert Object  

| Param | Type | Description |
| --- | --- | --- |
| collection | <code>string</code> | The collection to aggregate documents in. |

<a name="Mongo+liveQuery"></a>

### mongo.liveQuery(collection) ⇒ [<code>LiveQuery</code>](#external_LiveQuery)
Returns a LiveQuery Object

**Kind**: instance method of [<code>Mongo</code>](#Mongo)  
**Returns**: [<code>LiveQuery</code>](#external_LiveQuery) - LiveQuery Object  

| Param | Type | Description |
| --- | --- | --- |
| collection | <code>string</code> | The collection to query documents. |

**Example**  
```js
const onSnapshot = (snapshot, type, docs) => {
   console.log(type, snapshot, docs)
}

const onError = (err) => {
  console.log('Operation failed:', err)
}

let unsubscribe = db.liveQuery('posts').where({}).subscribe(onSnapshot, onError) 

// Unsubscribe to clean up
unsubscribe()
```
<a name="Mongo+profile"></a>

### mongo.profile(id) ⇒ <code>Promise</code>
Fetches the user profile

**Kind**: instance method of [<code>Mongo</code>](#Mongo)  
**Returns**: <code>Promise</code> - Returns a promise containing response from server  

| Param | Type | Description |
| --- | --- | --- |
| id | <code>string</code> | The unique user id |

**Example**  
```js
db.profile(id).then(res => {
  if (res.status === 200) {
    // res.data.user contains user details
    console.log('Response:', res.data.user);
    return;
  }
  // Request failed
}).catch(ex => {
  // Exception occured while processing request
});
```
<a name="Mongo+editProfile"></a>

### mongo.editProfile(id, email, name, pass) ⇒ <code>Promise</code>
Updates the user profile

**Kind**: instance method of [<code>Mongo</code>](#Mongo)  
**Returns**: <code>Promise</code> - Return a promise containing response from server  

| Param | Type | Description |
| --- | --- | --- |
| id | <code>string</code> | The unique user id |
| email | <code>string</code> | The new email id |
| name | <code>string</code> | The new name |
| pass | <code>string</code> | The new password |

**Example**  
```js
db.editProfile(id, email, name, pass).then(res => {
  if (res.status === 200) {
    // User account has been updates successfully
    return;
  }
  // Request failed
}).catch(ex => {
  // Exception occured while processing request
});
```
<a name="Mongo+profiles"></a>

### mongo.profiles() ⇒ <code>Promise</code>
Fetches all the user profiles

**Kind**: instance method of [<code>Mongo</code>](#Mongo)  
**Returns**: <code>Promise</code> - Returns a promise containing response from server  
**Example**  
```js
db.profiles().then(res => {
  if (res.status === 200) {
    // res.data.users contains user details
    console.log('Response:', res.data.users);
    return;
  }
  // Request failed
}).catch(ex => {
  // Exception occured while processing request
});
```
<a name="Mongo+signIn"></a>

### mongo.signIn(email, pass) ⇒ [<code>Promise.&lt;AuthResponse&gt;</code>](#AuthResponse)
Sends a sign in query to the server

**Kind**: instance method of [<code>Mongo</code>](#Mongo)  
**Returns**: [<code>Promise.&lt;AuthResponse&gt;</code>](#AuthResponse) - Returns a promise containing response from server  

| Param | Type | Description |
| --- | --- | --- |
| email | <code>string</code> | The user's email id. |
| pass | <code>string</code> | The user's password. |

**Example**  
```js
db.signIn('demo@example.com', '1234').then(res => {
  if (res.status === 200) {
    // Set the token id to enable crud operations
    api.setToken(res.data.token)

    // res.data contains request payload
    console.log('Response:', res.data);
    return;
  }
  // Request failed
}).catch(ex => {
  // Exception occured while processing request
});
```
<a name="Mongo+signUp"></a>

### mongo.signUp(email, name, pass, role) ⇒ [<code>Promise.&lt;AuthResponse&gt;</code>](#AuthResponse)
Sends a sign up query to the server

**Kind**: instance method of [<code>Mongo</code>](#Mongo)  
**Returns**: [<code>Promise.&lt;AuthResponse&gt;</code>](#AuthResponse) - Returns a promise containing response from server  

| Param | Type | Description |
| --- | --- | --- |
| email | <code>string</code> | The user's email id. |
| name | <code>string</code> | The user's name. |
| pass | <code>string</code> | The user's password. |
| role | <code>string</code> | The user's role. |

**Example**  
```js
db.signUp('demo@example.com', 'UserName', '1234', 'default').then(res => {
  if (res.status === 200) {
    // Set the token id to enable crud operations
    api.setToken(res.data.token)
    
    // res.data contains request payload
    console.log('Response:', res.data);
    return;
  }
  // Request failed
}).catch(ex => {
  // Exception occured while processing request
});
```
<a name="Insert"></a>

## Insert
Class representing the MongoDB Insert Interface.

**Kind**: global class  

* [Insert](#Insert)
    * [new Insert(appId, collection, url, options)](#new_Insert_new)
    * [.one(doc)](#Insert+one) ⇒ <code>Promise</code>
    * [.all(docs)](#Insert+all) ⇒ <code>Promise</code>

<a name="new_Insert_new"></a>

### new Insert(appId, collection, url, options)
Create an instance of the MongoDB Insert Interface.


| Param | Type |
| --- | --- |
| appId | <code>string</code> | 
| collection | <code>string</code> | 
| url | <code>string</code> | 
| options | <code>Object</code> | 

**Example**  
```js
import { API, cond, or, and } from 'space-api';

const api = new API('my-project', 'http://localhost:8080');
const db = api.Mongo();

const doc = { author: 'John', title: 'Title1', _id: 1 };
db.insert('posts').one(doc).then(res => {
  if (res.status === 200) {
    // Document was inserted successfully
    return;
  }
}).catch(ex => {
  // Exception occured while processing request
});
```
<a name="Insert+one"></a>

### insert.one(doc) ⇒ <code>Promise</code>
Makes the query to insert a single document.

**Kind**: instance method of [<code>Insert</code>](#Insert)  
**Returns**: <code>Promise</code> - Returns a promise containing response from server.  

| Param | Type | Description |
| --- | --- | --- |
| doc | <code>Object</code> | The document to be inserted. |

**Example**  
```js
const doc = { author: 'John', title: 'Title1', _id: 1 };
db.insert('posts').one(doc).then(res => ...)
```
<a name="Insert+all"></a>

### insert.all(docs) ⇒ <code>Promise</code>
Makes the query to insert multiple documents.

**Kind**: instance method of [<code>Insert</code>](#Insert)  
**Returns**: <code>Promise</code> - Returns a promise containing response from server.  

| Param | Type | Description |
| --- | --- | --- |
| docs | <code>Array.&lt;Object&gt;</code> | The documents to be inserted. |

**Example**  
```js
const docs = [{ author: 'John', title: 'Title1', _id: 1 }];
db.insert('posts').all(docs).then(res => ...)
```
<a name="Get"></a>

## Get
Class representing the MongoDB Get Interface.

**Kind**: global class  

* [Get](#Get)
    * [new Get(appId, collection, url, options)](#new_Get_new)
    * [.where(...conditions)](#Get+where)
    * [.select(select)](#Get+select)
    * [.sort(...array)](#Get+sort)
    * [.skip(num)](#Get+skip)
    * [.limit(num)](#Get+limit)
    * [.one()](#Get+one) ⇒ <code>Promise</code>
    * [.all()](#Get+all) ⇒ <code>Promise</code>
    * [.distinct()](#Get+distinct) ⇒ <code>Promise</code>
    * [.count()](#Get+count)

<a name="new_Get_new"></a>

### new Get(appId, collection, url, options)
Create an instance of the MongoDB Get Interface.


| Param | Type |
| --- | --- |
| appId | <code>string</code> | 
| collection | <code>string</code> | 
| url | <code>string</code> | 
| options | <code>Object</code> | 

**Example**  
```js
import { API, cond, or, and } from 'space-api';

const api = new API('my-project', 'http://localhost:8080');
const db = api.Mongo();

db.get('posts').where(and(cond('title', '==', 'Title1'))).all().then(res => {
  if (res.status === 200) {
    // res.data contains the documents returned by the database
    console.log('Response:', res.data);
    return;
  }
}).catch(ex => {
  // Exception occured while processing request
});
```
<a name="Get+where"></a>

### get.where(...conditions)
Prepares the find query

**Kind**: instance method of [<code>Get</code>](#Get)  

| Param | Type | Description |
| --- | --- | --- |
| ...conditions | <code>Object</code> | The condition logic. |

<a name="Get+select"></a>

### get.select(select)
Sets the fields to be selected

**Kind**: instance method of [<code>Get</code>](#Get)  

| Param | Type | Description |
| --- | --- | --- |
| select | <code>Object</code> | The select object. |

**Example**  
```js
// Given query will only select author and title fields
const select = { author: 1, title: 1 }
db.get('posts').select(select).all().then(res => ...)
```
<a name="Get+sort"></a>

### get.sort(...array)
Sets the fields to sort result by.

**Kind**: instance method of [<code>Get</code>](#Get)  

| Param | Type | Description |
| --- | --- | --- |
| ...array | <code>string</code> | The fields to sort result by. |

**Example**  
```js
// Given query will sort results first by age (asc) then by age (desc)
db.get('posts').sort('title', '-age').all().then(res => ...)
```
<a name="Get+skip"></a>

### get.skip(num)
Sets the number of documents to skip in the array.

**Kind**: instance method of [<code>Get</code>](#Get)  

| Param | Type | Description |
| --- | --- | --- |
| num | <code>number</code> | The number of documents to skip. |

**Example**  
```js
// Given query will skip the first 10 documents
db.get('posts').skip(10).all().then(res => ...)
```
<a name="Get+limit"></a>

### get.limit(num)
Sets the limit on number of documents returned by the query.

**Kind**: instance method of [<code>Get</code>](#Get)  

| Param | Type | Description |
| --- | --- | --- |
| num | <code>number</code> | The limit on number of documents. |

**Example**  
```js
// Given query will limit the result to 10 documents
db.get('posts').limit(10).all().then(res => ...)
```
<a name="Get+one"></a>

### get.one() ⇒ <code>Promise</code>
Makes the query to return a single document as an object. If no documents are returned, the status code is 400.

**Kind**: instance method of [<code>Get</code>](#Get)  
**Returns**: <code>Promise</code> - Returns a promise containing response from server.  
**Example**  
```js
db.get('posts').one().then(res => ...)
```
<a name="Get+all"></a>

### get.all() ⇒ <code>Promise</code>
Makes the query to return a multiple documents as an array. It is possible for an empty array to be returned.

**Kind**: instance method of [<code>Get</code>](#Get)  
**Returns**: <code>Promise</code> - Returns a promise containing response from server.  
**Example**  
```js
db.get('posts').all().then(res => ...)
```
<a name="Get+distinct"></a>

### get.distinct() ⇒ <code>Promise</code>
Makes the query to return an array of all the distinct values for the given field. It is possible for an empty array to be returned.

**Kind**: instance method of [<code>Get</code>](#Get)  
**Returns**: <code>Promise</code> - Returns a promise containing response from server.  
**Example**  
```js
db.get('posts').distinct('category').then(res => ...)
```
<a name="Get+count"></a>

### get.count()
Makes the query to return the count of total number of documents that were queried.

**Kind**: instance method of [<code>Get</code>](#Get)  
**Example**  
```js
// Given query counts the total number of posts in the 'posts' collection
db.get('posts').count().then(res => ...)
```
<a name="Update"></a>

## Update
Class representing the MongoDB Update Interface.

**Kind**: global class  

* [Update](#Update)
    * [new Update(appId, collection, url, options)](#new_Update_new)
    * [.where(...conditions)](#Update+where)
    * [.set(obj)](#Update+set)
    * [.push(obj)](#Update+push)
    * [.remove(...fields)](#Update+remove)
    * [.rename(obj)](#Update+rename)
    * [.inc(obj)](#Update+inc)
    * [.mul(obj)](#Update+mul)
    * [.max(obj)](#Update+max)
    * [.min(obj)](#Update+min)
    * [.currentTimestamp(...values)](#Update+currentTimestamp)
    * [.currentDate(...values)](#Update+currentDate)
    * [.one()](#Update+one) ⇒ <code>Promise</code>
    * [.all()](#Update+all) ⇒ <code>Promise</code>
    * [.upsert()](#Update+upsert)

<a name="new_Update_new"></a>

### new Update(appId, collection, url, options)
Create an instance of the MongoDB Update Interface.


| Param | Type |
| --- | --- |
| appId | <code>string</code> | 
| collection | <code>string</code> | 
| url | <code>string</code> | 
| options | <code>Object</code> | 

**Example**  
```js
import { API, cond, or, and } from 'space-api';

const api = new API('my-project', 'http://localhost:8080');
const db = api.Mongo();

db.update('posts').where(and(cond('title', '==', 'Title1'))).set({ title: 'Title2' }).all().then(res => {
  if (res.status === 200) {
    // The documents were updated successfully
    return;
  }
}).catch(ex => {
  // Exception occured while processing request
});
```
<a name="Update+where"></a>

### update.where(...conditions)
Prepares the find query

**Kind**: instance method of [<code>Update</code>](#Update)  

| Param | Type | Description |
| --- | --- | --- |
| ...conditions | <code>Object</code> | The condition logic. |

<a name="Update+set"></a>

### update.set(obj)
Sets the value of a field in a document.

**Kind**: instance method of [<code>Update</code>](#Update)  

| Param | Type | Description |
| --- | --- | --- |
| obj | <code>Object</code> | The Object containing fields to set. |

**Example**  
```js
db.update('posts').set({ author: 'Drake' }).all().then(res => ...)
```
<a name="Update+push"></a>

### update.push(obj)
Adds an item to an array.

**Kind**: instance method of [<code>Update</code>](#Update)  

| Param | Type | Description |
| --- | --- | --- |
| obj | <code>Object</code> | The Object containing fields to set. |

**Example**  
```js
db.update('posts').push({ author: 'Drake' }).all().then(res => ...)
```
<a name="Update+remove"></a>

### update.remove(...fields)
Removes the specified field from a document.

**Kind**: instance method of [<code>Update</code>](#Update)  

| Param | Type | Description |
| --- | --- | --- |
| ...fields | <code>string</code> | The fields to remove. |

**Example**  
```js
db.update('posts').remove('age', 'likes').all().then(res => ...)
```
<a name="Update+rename"></a>

### update.rename(obj)
Renames the specified field.

**Kind**: instance method of [<code>Update</code>](#Update)  

| Param | Type | Description |
| --- | --- | --- |
| obj | <code>Object</code> | The object containing fields to rename. |

**Example**  
```js
db.update('posts').rename({ mobile: 'contact' }).all().then(res => ...)
```
<a name="Update+inc"></a>

### update.inc(obj)
Increments the value of the field by the specified amount.

**Kind**: instance method of [<code>Update</code>](#Update)  

| Param | Type | Description |
| --- | --- | --- |
| obj | <code>Object</code> | The object containing fields to increment along with the value. |

**Example**  
```js
// The value of added with 1
db.update('posts').inc({ views: 1 }).all().then(res => ...)
```
<a name="Update+mul"></a>

### update.mul(obj)
Multiplies the value of the field by the specified amount.

**Kind**: instance method of [<code>Update</code>](#Update)  

| Param | Type | Description |
| --- | --- | --- |
| obj | <code>Object</code> | The object containing fields to multiply along with the value. |

**Example**  
```js
// The value of amount will be multiplied by 4
db.update('posts').mul({ amount: 4 }).all().then(res => ...)
```
<a name="Update+max"></a>

### update.max(obj)
Only updates the field if the specified value is greater than the existing field value.

**Kind**: instance method of [<code>Update</code>](#Update)  

| Param | Type | Description |
| --- | --- | --- |
| obj | <code>Object</code> | The object containing fields to set. |

**Example**  
```js
db.update('posts').max({ highScore: 1200 }).all().then(res => ...)
```
<a name="Update+min"></a>

### update.min(obj)
Only updates the field if the specified value is lesser than the existing field value.

**Kind**: instance method of [<code>Update</code>](#Update)  

| Param | Type | Description |
| --- | --- | --- |
| obj | <code>Object</code> | The object containing fields to set. |

**Example**  
```js
db.update('posts').min({ lowestScore: 300 }).all().then(res => ...)
```
<a name="Update+currentTimestamp"></a>

### update.currentTimestamp(...values)
Sets the value of a field to current timestamp.

**Kind**: instance method of [<code>Update</code>](#Update)  

| Param | Type | Description |
| --- | --- | --- |
| ...values | <code>string</code> | The fields to set. |

**Example**  
```js
db.update('posts').currentTimestamp('lastModified').all().then(res => ...)
```
<a name="Update+currentDate"></a>

### update.currentDate(...values)
Sets the value of a field to current date.

**Kind**: instance method of [<code>Update</code>](#Update)  

| Param | Type | Description |
| --- | --- | --- |
| ...values | <code>string</code> | The fields to set. |

**Example**  
```js
db.update('posts').currentDate('lastModified').all().then(res => ...)
```
<a name="Update+one"></a>

### update.one() ⇒ <code>Promise</code>
Makes the query to update a single document which matches first.

**Kind**: instance method of [<code>Update</code>](#Update)  
**Returns**: <code>Promise</code> - Returns a promise containing response from server  
<a name="Update+all"></a>

### update.all() ⇒ <code>Promise</code>
Makes the query to update all documents which matches.

**Kind**: instance method of [<code>Update</code>](#Update)  
**Returns**: <code>Promise</code> - Returns a promise containing response from server  
<a name="Update+upsert"></a>

### update.upsert()
Makes the query to update all, else insert a document.

**Kind**: instance method of [<code>Update</code>](#Update)  
<a name="Delete"></a>

## Delete
Class representing the MongoDB Delete Interface.

**Kind**: global class  

* [Delete](#Delete)
    * [new Delete(appId, collection, url, options)](#new_Delete_new)
    * [.where(...conditions)](#Delete+where)
    * [.one()](#Delete+one) ⇒ <code>Promise</code>
    * [.all()](#Delete+all) ⇒ <code>Promise</code>

<a name="new_Delete_new"></a>

### new Delete(appId, collection, url, options)
Create an instance of the MongoDB Delete Interface.


| Param | Type |
| --- | --- |
| appId | <code>string</code> | 
| collection | <code>string</code> | 
| url | <code>string</code> | 
| options | <code>Object</code> | 

**Example**  
```js
import { API, cond, or, and } from 'space-api';

const api = new API('my-project', 'localhost:8080');
const db = api.Mongo();

db.delete('posts').where(and(cond('title', '==', 'Title1'))).all().then(res => {
  if (res.status === 200) {
    // The documents were deleted successfully
    return;
  }
}).catch(ex => {
  // Exception occured while processing request
});
```
<a name="Delete+where"></a>

### delete.where(...conditions)
Prepares the find query

**Kind**: instance method of [<code>Delete</code>](#Delete)  

| Param | Type | Description |
| --- | --- | --- |
| ...conditions | <code>Object</code> | The condition logic. |

<a name="Delete+one"></a>

### delete.one() ⇒ <code>Promise</code>
Makes the query to delete a single document which matches first.

**Kind**: instance method of [<code>Delete</code>](#Delete)  
**Returns**: <code>Promise</code> - Returns a promise containing response from server.  
**Example**  
```js
db.delete('posts').one().then(res => ...)
```
<a name="Delete+all"></a>

### delete.all() ⇒ <code>Promise</code>
Makes the query to delete all the documents which match.

**Kind**: instance method of [<code>Delete</code>](#Delete)  
**Returns**: <code>Promise</code> - Returns a promise containing response from server.  
**Example**  
```js
db.delete('posts').all().then(res => ...)
```
<a name="Aggregate"></a>

## Aggregate
Class representing the MongoDB Delete Interface.

**Kind**: global class  

* [Aggregate](#Aggregate)
    * [new Aggregate(appId, collection, url, options)](#new_Aggregate_new)
    * [.pipe(pipeObj)](#Aggregate+pipe)
    * [.one()](#Aggregate+one) ⇒ <code>Promise</code>
    * [.all()](#Aggregate+all) ⇒ <code>Promise</code>

<a name="new_Aggregate_new"></a>

### new Aggregate(appId, collection, url, options)
Create an instance of the MongoDB Delete Interface.


| Param | Type |
| --- | --- |
| appId | <code>string</code> | 
| collection | <code>string</code> | 
| url | <code>string</code> | 
| options | <code>Object</code> | 

**Example**  
```js
import { API, cond, or, and } from 'space-api';

const api = new API('my-project', 'http://localhost:8080');
const db = api.Mongo();

const pipe = [
  { $match: { status: 'A' } },
  { $group: { _id: '$cust_id', total: { $sum: '$amount' } } }
]

db.aggr('posts').pipe(pipe).all().then(res => {
  if (res.status === 200) {
    // res.data contains the documents returned by the database
    console.log('Response:', res.data);
    return
  }
}).catch(ex => {
  // Exception occured while processing request
});
```
<a name="Aggregate+pipe"></a>

### aggregate.pipe(pipeObj)
Prepares the Pipe query

**Kind**: instance method of [<code>Aggregate</code>](#Aggregate)  

| Param | Type | Description |
| --- | --- | --- |
| pipeObj | <code>Array.&lt;Object&gt;</code> | The pipeline object. |

<a name="Aggregate+one"></a>

### aggregate.one() ⇒ <code>Promise</code>
Makes the query to return single object.

**Kind**: instance method of [<code>Aggregate</code>](#Aggregate)  
**Returns**: <code>Promise</code> - Returns a promise containing response from server.  
**Example**  
```js
db.aggr('posts').pipe([...]).one().then(res => ...)
```
<a name="Aggregate+all"></a>

### aggregate.all() ⇒ <code>Promise</code>
Makes the query to return all objects.

**Kind**: instance method of [<code>Aggregate</code>](#Aggregate)  
**Returns**: <code>Promise</code> - Returns a promise containing response from server.  
**Example**  
```js
db.aggr('posts').pipe([...]).all().then(res => ...)
```
<a name="User"></a>

## User
**Kind**: global typedef  
**Properties**

| Name | Type | Description |
| --- | --- | --- |
| _id | <code>string</code> | The user's unique id. |
| email | <code>string</code> | The user's email id. |
| name | <code>string</code> | The user's name. |
| role | <code>string</code> | The user's role. |

<a name="AuthResponse"></a>

## AuthResponse
**Kind**: global typedef  
**Properties**

| Name | Type | Description |
| --- | --- | --- |
| status | <code>number</code> | The http status code of response. |
| data | <code>Object</code> | The response payload. |
| data.token | <code>string</code> | The signed token generated for the user. |
| data.user | [<code>User</code>](#User) | Information of the user. |

<a name="external_LiveQuery"></a>

## LiveQuery
The LiveQuery Interface.

**Kind**: global external  
**See**: [https://github.com/spaceuptech/space-api-js/wiki/Realtime](https://github.com/spaceuptech/space-api-js/wiki/Realtime)  
