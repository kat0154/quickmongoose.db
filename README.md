![version](https://raster.shields.io/npm/v/quick.mongoose.png)![downloads](https://raster.shields.io/npm/dt/quick.mongoose.png?maxAge=3600)

![npm](https://nodei.co/npm/quick.mongoose.png)

# quick.mongoose

an easy to install and easy to use wrapper for the [mongoose cli](https://npmjs.com/packages/mongoose)

# Examples
setup
```js
let mongo = require('quick.mongoose');
let db = new mongo.Connection('mongodb-connectionURL');
let econ = new db.table('economy', {
  UserID: Number,
  Bank: {type: Number, default: 0},
  Credits: {type: Number, default: 0},
  Inventory: Array
});
```
note: ``you can also use 'await' instead` for the below``

example:
```js
let user = await econ.create({UserID: 377271843502948354});
console.log(user);
//{ Bank: 0, Credits: 0, Inventory: [] }
```
note: `await is only valid in an async function`

# Uses

create
```js
econ.create({UserID: 377271843502948354}).then(user => {
    console.log(user);
  //{ Bank: 0, Credits: 0, Inventory: [] }
});
```
add
```js
econ.add({UserID: 377271843502948354},'Bank', 50).then(newBalance => {
  console.log(newBalance);
  //50
});
```
all
```js
econ.all({UserID: 377271843502948354},5).then(arr => {
  console.log(arr);
  //[{Bank: 0, Credits: 0, Inventory: [], UserID: 377271843502948350}]
});
```
fetch
```js
econ.fetch({UserID: 377271843502948354}).then(user => {
  console.log(user);
  //{ Bank: 0, Credits: 0, Inventory: [] }
});
```
get
```js
econ.get({UserID: 377271843502948354}).then(user => {
  console.log(user);
  //{ Bank: 0, Credits: 0, Inventory: [] }
});
```
has
```js
econ.has({UserID: 377271843502948354}).then(bool => {
  console.log(bool);
  //true
});
```
push
```js
econ.push({UserID: 377271843502948354}, 'Inventory', 'Hammer').then(arr => {
  console.log(arr);
  //["Hammer"]
});
```
set
```js
econ.set({UserID: 377271843502948354},'Credits', 50).then(newBalance => {
  console.log(newBalance);
  //50
});
```
subtract
```js
econ.subtract({UserID: 377271843502948354},'Bank', 50).then(newBalance => {
  console.log(newBalance);
  //0
});
```
delete
```js
econ.delete({UserID: 377271843502948354}).then(bool => {
  console.log(bool);
  //true
});
```

# Questions?

`what do i get if i don't use 'await' or '.then'?`
> if no await or .then is used, it returns as
> `Promise { <pending> }`
> though if you're trying to push, add, subtract, or delete, it will still complete the operation

`can i use this wrapper with a discord bot? OwO`
> yes. in fact, the UserID i used with all the examples above was my own
> OwO

`what is there to this wrapper that you aren't telling us?`
> oop, you caught me...
> there are some functions you can use that i don't show above, such as:
> `db.stats()`, `db.getUrl()`, `db.getState()`, `db.getUptime()`, and `db.disconnect()`
