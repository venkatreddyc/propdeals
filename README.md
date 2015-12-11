# Property Deals System
Property Deals Management System

[![Dependency Status](https://david-dm.org/venkatreddyc/propdeals.svg?theme=shields.io)](https://david-dm.org/venkatreddyc/propdeals)
[![devDependency Status](https://david-dm.org/venkatreddyc/propdeals/dev-status.svg?theme=shields.io)](https://david-dm.org/venkatreddyc/propdeals#info=devDependencies)
[![Build Status](https://travis-ci.org/venkatreddyc/propdeals.svg?branch=master)](https://travis-ci.org/venkatreddyc/propdeals)
[![NPM version](https://img.shields.io/npm/v/jshint.svg?style=flat)](https://www.npmjs.com/package/jshint)
[![Dependency Status](https://img.shields.io/david/venkatreddyc/propdeals.svg?style=flat)](https://david-dm.org/venkatreddyc/propdeals)
[![devDependency Status](https://img.shields.io/david/dev/venkatreddyc/propdeals.svg?style=flat)](https://david-dm.org/venkatreddyc/propdeals#info=devDependencies)
[![Coverage Status](https://img.shields.io/coveralls/venkatreddyc/propdeals.svg?style=flat)](https://coveralls.io/r/venkatreddyc/propdeals?branch=master)

<a href="https://codeclimate.com/github/venkatreddyc/propdeals/coverage"><img src="https://codeclimate.com/github/venkatreddyc/propdeals/badges/coverage.svg" /></a>
<a href="https://codeclimate.com/github/venkatreddyc/propdeals"><img src="https://codeclimate.com/github/venkatreddyc/propdeals/badges/gpa.svg" /></a>
<a href="https://codeclimate.com/github/venkatreddyc/propdeals"><img src="https://codeclimate.com/github/venkatreddyc/propdeals/badges/issue_count.svg" /></a>



## Technology

Server side, Drywall is built with the [Express](http://expressjs.com/)
framework. We're using [MongoDB](http://www.mongodb.org/) as a data store.

The front-end is built with [Backbone](http://backbonejs.org/).
We're using [Grunt](http://gruntjs.com/) for the asset pipeline.

| On The Server | On The Client  | Development |
| ------------- | -------------- | ----------- |
| Express       | Bootstrap      | Grunt       |
| Jade          | Backbone.js    |             |
| Mongoose      | jQuery         |             |
| Passport      | Underscore.js  |             |
| Async         | Font-Awesome   |             |
| EmailJS       | Moment.js      |             |


## Live demo

Coming Soon

## Requirements

You need [Node.js](http://nodejs.org/download/) and
[MongoDB](http://www.mongodb.org/downloads) installed and running.



## Installation

```bash
$ git clone git@github.com:venkatreddyc/propdeals.git && cd ./propdeals
$ npm install
```


## Setup

First you need to setup your config file.

```bash
$ mv ./config.example.js ./config.js #set mongodb and email credentials
```

Next, you need a few records in the database to start using the user system.

Run these commands on mongo via the terminal. __Obviously you should use your
email address.__

```js
use drywall; // or your mongo db name if different
```

```js
db.admingroups.insert({ _id: 'root', name: 'Root' });
db.admins.insert({ name: {first: 'Root', last: 'Admin', full: 'Root Admin'}, groups: ['root'] });
var rootAdmin = db.admins.findOne();
db.users.save({ username: 'root', isActive: 'yes', email: 'your@email.addy', roles: {admin: rootAdmin._id} });
var rootUser = db.users.findOne();
rootAdmin.user = { id: rootUser._id, name: rootUser.username };
db.admins.save(rootAdmin);
```


## Running the app

```bash
$ npm start

# > Drywall@0.0.0 start /Users/jedireza/projects/jedireza/drywall
# > grunt

# Running "copy:vendor" (copy) task
# ...

# Running "concurrent:dev" (concurrent) task
# Running "watch" task
# Running "nodemon:dev" (nodemon) task
# Waiting...
# [nodemon] v1.3.7
# [nodemon] to restart at any time, enter `rs`
# [nodemon] watching: *.*
# [nodemon] starting `node app.js`
# Server is running on port 3000
```

Now just use the reset password feature to set a password.

 - Go to `http://localhost:3000/login/forgot/`
 - Submit your email address and wait a second.
 - Go check your email and get the reset link.
 - `http://localhost:3000/login/reset/:email/:token/`
 - Set a new password.

Login. Customize. Enjoy.


## Philosophy

 - Create a website and user system.
 - Write code in a simple and consistent way.
 - Only create minor utilities or plugins to avoid repetitiveness.
 - Find and use good tools.
 - Use tools in their native/default behavior.


## Features

 - Basic front end web pages.
 - Contact page has form to email.
 - Login system with forgot password and reset password.
 - Signup and Login with Facebook, Twitter, GitHub, Google and Tumblr.
 - Optional email verification during signup flow.
 - User system with separate account and admin roles.
 - Admin groups with shared permission settings.
 - Administrator level permissions that override group permissions.
 - Global admin quick search component.


## Questions and contributing

Any issues or questions (no matter how basic), open an issue. Please take the
initiative to include basic debugging information like operating system
and relevant version details such as:

```bash
$ npm version

# { drywall: '0.0.0',
#   npm: '2.5.1',
#   http_parser: '2.3',
#   modules: '14',
#   node: '0.12.0',
#   openssl: '1.0.1l',
#   uv: '1.0.2',
#   v8: '3.28.73',
#   zlib: '1.2.8' }
```

Contributions are welcome. Your code should:

 - pass `$ grunt lint` without error

If you're changing something non-trivial, you may want to submit an issue
first.


## License

MIT


