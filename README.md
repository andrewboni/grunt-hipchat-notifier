# grunt-hipchat-notifier

[![Dependency Status](https://david-dm.org/logankoester/grunt-hipchat-notifier.png)](https://david-dm.org/logankoester/grunt-hipchat-notifier)
[![devDependency Status](https://david-dm.org/logankoester/grunt-hipchat-notifier/dev-status.png)](https://david-dm.org/logankoester/grunt-hipchat-notifier#info=devDependencies)

> Send grunt messages to a Hipchat channel

## Getting Started
This plugin requires Grunt `~0.4.1`

If you haven't used [Grunt](http://gruntjs.com/) before, be sure to check out the [Getting Started](http://gruntjs.com/getting-started) guide, as it explains how to create a [Gruntfile](http://gruntjs.com/sample-gruntfile) as well as install and use Grunt plugins. Once you're familiar with that process, you may install this plugin with this command:

```shell
npm install grunt-hipchat-notifier --save-dev
```

Once the plugin has been installed, it may be enabled inside your Gruntfile with this line of JavaScript:

```js
grunt.loadNpmTasks('grunt-hipchat-notifier');
```

## The "hipchat_notifier" task

### Overview
In your project's Gruntfile, add a section named `hipchat_notifier` to the data object passed into `grunt.initConfig()`.

```js
grunt.initConfig({
  hipchat_notifier: {

    // You probably want to set your Hipchat options globally...

    options: {
      authToken: "", // Create an authToken at https://hipchat.com/admin/api
      roomId: "" // Numeric Hipchat roomId
    },

    // Now create as many messages as you like!

    hello_grunt: {
      options: {
        message: "Hello!", // A message to send
        from: "Grunt", // Name for the sender
        color: "purple" // Color of the message
      }
    },

    // Send dynamic message based off anything Node/Grunt/Javascript can do!
    
    dynamic_hello_grunt: {
      options: {
        message: function() { // Functions must return a string
          var pkg = grunt.config.data.pkg;
          return 'Running grunt on ' + pkg.name + ' on version ' + pkg.name;
        },
        from: function() {  // Return the run-time user, or something more creative.
          return someUsernameGenerator() || process.env['USER'];
        },
        // Change color dynamically based on some global state, function response, etc
        color: function() {
          return (grunt.config.data.someBoolean && allIsWell()) ? 'green' : 'red';
        }
      }
    }

  },
})
```

## Release History

* 0.1.1 - Added support for dynamic messaging
* 0.1.0 - First release


[![Bitdeli Badge](https://d2weczhvl823v0.cloudfront.net/logankoester/grunt-hipchat-notifier/trend.png)](https://bitdeli.com/free "Bitdeli Badge")

