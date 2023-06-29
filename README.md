generator-api-on-calling
---

API is crucial to the business when developing softwares.

Many companies happen to feel it is not easy to manage various kinds of api when the number of the apis grow up.

So, it comes to a question: is there an easy and efficient request client, which can be auto generated according to some special kind of openapi schema data ?

## generator-api-on-calling

It generate frontend api request client according to an openapi shema url.

The generated request api service always got a calling method, and receive the options object argument.

e.g. GET /pets/{petId}:

```js
/**
 * the request options
 */ 
const requestOptions = {};

await ApiService.pets.$petId.get.calling(requestOptions);
```

1. npm install yeoman globally

```sh
npm install yo -g
```

2. install generator-api-on-calling globally

```sh
npm i generator-api-on-calling -g
```

3. generate some api service according to an openapi shema url ?

- enter some frontend project workspace, e.g. hello

- we want the api service name: ApiService

```sh
cd /some/path/to/your/project/hello

yo api-on-calling --lang=javascript --service=ApiService --schema-url=http://localhost:8080/some-backend-schema-url.json
```

## common required options

1. lang

now only support: *javascript*

2. service

the service name, which is in *camel case* style

e.g. ApiService, UserService, AuthService, ProfileService ...etc.

3. schema-url

the shcema url, an http request url which can be requested by GET .

- suppported data format: json

- supported openapi version: v3.0.3

---

## lang - javascript

command line options

1. javascript-keyword-request

the str of the keyword request, which to indicate how the request is imported.

*default* (cmd line: just type the Enter)

```js
import { request } from '@request';
```

### @attention

this needs webpack config alias field: 

```js
const webpackConfig = {
  alias: {
    "@request": "/some/path/to/your/request"
  }
};
```

2. javascript-prettier-config

the path of the javascript prettier config

*default* (cmd line: just type the Enter)

```js
module.exports = {
  printWidth: 120,
  tabWidth: 2,
  useTabs: false,
  semi: true,
  singleQuote: true,
  quoteProps: 'as-needed',
  trailingComma: 'es5',
  jsxSingleQuote: true,
  trailingComma: 'es5',
  bracketSpacing: true,
  bracketSameLine: false,
  endOfLine: 'lf',
};
```
