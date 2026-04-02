# PWD.

  Hash and compare passwords with the crypto's pbkdf2.

# Installation

```bash
$ npm install pwd
```

# Example

On signup generate a salt / password hash, and save it somewhere:

```js
var pass = require('pwd');
pass.hash('my password', function(err, salt, hash){
  user.salt = salt;
  user.hash = hash;
})
```

To authenticate load and compare:

```js
var pass = require('pwd');
pass.hash('submitted password', user.salt, function(err, hash){
  if (user.hash == hash) {
    // yay
  }
})
```

Too fast? slow it down:

```js
pass.iterations(20000);
```

# Promises

Functions that take a callback will return a Promise if no callback is provided.

Hashing a password:

```js
var pass = require('pwd');
pass.hash('my password').then(function(result) {
  user.salt = result.salt;
  user.hash = result.hash;
});
```

Authenticating:

```js
var pass = require('pwd');
pass.hash('submitted password', user.salt).then(function(result) {
  if (user.hash === result.hash) {
    // yay
  }
});













































































