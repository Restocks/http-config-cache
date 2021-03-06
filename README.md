# http-config-cache
Caches JSON configs. Meant for long running processes with configs that update more often than environment variables would.

## Installation 

`npm install http-config-cache`

## Usage

Really simple. Simply include the module and pass it a URL to some JSON. It will then return a promise that returns the config as an object.


### Basic:

```js
const configCache = require('http-config-cache');
const configUrl = 'https://raw.githubusercontent.com/Restocks/http-config-cache/master/static/test.json';

configCache(configUrl).then((data) => {
  console.log(data);
}).catch((err) => {
  console.log(err);
});
```

### While specifying a cache expiry:

By default all objects expire every 10 minutes before they're fetched again. You can change that by passing a `time` variable to the function. `time` is a number in milliseconds.

```js
// 5 second expiry
configCache(configUrl, 5000).then((data) => {
  console.log(data);
}).catch((err) => {
  console.log(err);
});
```

### While forcing a network request

There's also another option to force a network request and ignore the cache entirely. Here's an example of doing that while respecting the standard cache interval.

```js
configCache(configUrl, null, true).then((data) => {
  console.log(data);
}).catch((err) => {
  console.log(err);
});
```

## Development scripts

We follow the [airbnb JS style guide](https://github.com/airbnb/javascript). Tests will fail if you don't. While developing locally, be sure to run `npm run lint` to lint your code to this standard.

`npm run test` also runs the tests for the repo.

## License

MIT (c) Restocks, Inc 2016.
