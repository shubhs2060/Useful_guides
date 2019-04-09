## Using Sentry
- You can use Sentry for tracking errors in your project or application.It helps you monitor and fix crashes in real time.

- To get you started you can follow the below steps.

* Install the Sentry Package using npm
  
  ```
  npm install @sentry/node@4.6.6
  ```

* Install Raven
  Raven.js is the official browser JavaScript client for Sentry. It automatically reports uncaught JavaScript exceptions triggered from a browser environment, and provides a rich API for reporting your own errors.
  
  ```
  npm i raven
  ```

* Configure Sentry
  You need to sign in to Sentry and create a new project which will give you an API key
  Create a file in your config called sentry.js
  Add this code to it
  
  ```
  var Raven = require('raven');
  module.exports = {
      raven: function () {
          if (process.env.NODE_ENV == 'production') {
              //production project  
              Raven.config('https://Your-API-KEY@sentry.io/1425685', {
                  sendTimeout: 5
              }).install();
              return Raven;
          } else {
              // for dev and test env you can use a common sentry project called dev  
              Raven.config('https://Your-API-KEY@sentry.io/228733', {
                  sendTimeout: 5
              }).install();
              return Raven;
          }
      }
  };
  

* Configure Your Middleware with Sentry
  Add this code to http.js

  ```
  var Raven = require('./sentry').raven();
  sentryRequestHandler: Raven.requestHandler(),
	sentryerrorHandler: Raven.errorHandler(),
  order: [
    'sentryRequestHandler',
    'sentryerrorHandler',
  ],
  ```