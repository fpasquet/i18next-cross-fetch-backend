# Introduction

This is a simple i18next backend to be used in the server and browser. It will load resources from a backend server using cross-fetch.

# Getting started

i18next-cross-fetch-backend requires **cross-fetch 2 or later**.

```
$ npm install i18next-cross-fetch-backend
```

or

```
$ yarn add i18next-xhr-backend
```

Wiring up:

```js
import i18next from 'i18next';
import Backend from 'i18next-cross-fetch-backend';

i18next
  .use(Backend)
  .init(i18nextOptions);
```

- As with all modules you can either pass the constructor function (class) to the i18next.use or a concrete instance.

## Backend Options

```js
{
  // path where resources get loaded from, or a function
  // returning a path:
  // function(lngs, namespaces) { return customPath; }
  // the returned path will interpolate lng, ns if provided like giving a static path
  loadPath: '/locales/{{lng}}/{{ns}}.json',

  // path to post missing resources
  addPath: 'locales/add/{{lng}}/{{ns}}',

}
```

Options can be passed in:

**preferred** - by setting options.backend in i18next.init:

```js
import i18next from 'i18next';
import Backend from 'i18next-cross-fetch-backend';

i18next
  .use(Backend)
  .init({
    backend: options
  });
```

on construction:

```js
  import Backend from 'i18next-cross-fetch-backend';
  const backend = new Backend(null, options);
```

via calling init:

```js
  import Backend from 'i18next-cross-fetch-backend';
  const backend = new Backend();
  backend.init(options);
```