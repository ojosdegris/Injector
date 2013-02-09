# Injector

Basic dependency injection for Nodejs.

And when I say basic, I mean basic. The idea with building this module was to create an open, flexible module system and not enforce new structures and coding styles.

## Installation

```
npm install injector
```

## Usage

### Setup

This is where the application is set up (or bootstrapped). It is most likely going to exist before any kind of server or database connection.

```javascript

// Require modules

var Injector = require('injector');
var path = require('path');

// Set up our application

var app = Injector.create('OurApplication', {
    
    // This is the directory where are modules will live
  
    directory: path.join(__dirname, 'modules'), // this would be ./modules
    
    // This is an array of all directories to ignore
    
    exclude: ['modules/models'] // this would be ./modules/models
});
```


### A Basic Module

All module files must start with a basic Nodejs ` module.exports ` and be housed within a ` funciton (app) {} `. The ` app ` variable is our injector object. From this, we can register our modules.

```javascript
module.exports = function (app) {
    
    // Some basic private stuff here ...
    
    // Declare our module here
    
    app.module('SomeModule', function () {
        return {
            someApiMethod: function () {
                //
            }
        }
    });
    
};
```
