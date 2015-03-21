nunjucks-date-filter
====================

This defines a `date` filter for [Nunjucks](http://mozilla.github.io/nunjucks/) 
implementing [moment.js](http://momentjs.com/), a rich date manager.


Getting Started
---------------

You may install this plugin with this command:

```shell
npm install nunjucks-date-filter --save-dev
```


Usage
-----

You must first include the filter and then add it to your *nunjucks* environment:

```js
var dateFilter = require('nunjucks-date-filter');

var env = new nunjucks.Environment();

env.addFilter('date', dateFilter);
```

A shortcut is proposed in the package:

```js
var dateFilter = require('nunjucks-date-filter');

dateFilter.install(
    [ env ]                     // by default, current nunjucks environment will be used
    [ , custom_filter_name ]    // by default, the filter will be named "date"
);
```

You can also define a default date format:

```js
var dateFilter = require('nunjucks-date-filter');

dateFilter.setDefaultFormat('YYYY');
```

Once it is installed, you can call the filter in your *nunjucks* templates:

```
// with no format
This blog has been created at {{ creation_date | date }}.

// with a custom format
This blog has been created at {{ creation_date | date("YYYY") }}.

// with an addition first
This blog has been created at {{ creation_date | date("add", 7, "days") | date }}.
```

*Moment* usage
--------------

The moment library embeds [a huge set of methods](http://momentjs.com/docs/#/get-set/) to
manipulate dates. Any of these methods can be called using the filter, passing as many arguments
as needed (see example above).


