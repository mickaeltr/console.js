# console.js

JavaScript console that sends logs to a remote server.
It also logs unexpected JavaScript global errors.

## Why?

You have plenty of logs for your server-side applications.
You need to know what is happening on your client-side applications too.

## Usage

First insert [jQuery](http://jquery.com/) (or [Zepto](http://zeptojs.com/)):

```html
<script src="//ajax.googleapis.com/ajax/libs/jquery/2.1.0/jquery.min.js"></script>
```

Then insert [console.js](https://github.com/mickaeltr/console.js):

```html
<script src="lib/console.js"></script>
```

Finally initialize the console and play with it!

```html
<script>
    console.init({serverUrl: "/logs"});
    console.warn("Writes a warning log in the JS console and sends it to the server");
</script>
```

This will be sent (POST) to the server URL:

```json
{
    "level": "warn",
    "message": "[<window.location>] Writes a warning log in the JS console and sends it to the server"
}
```

## Configuration

**levels**

* Default value: `["info", "warn", "error"]`
* Description: array of log levels, from the less critical to the most critical; for each level, a method is created on the console object.

**levelEnabledOnServer**

* Default value: first item in the levels list
* Description: minimum level for sending logs to the server

**levelForConsoleLog**

* Default value: first item in the levels list
* Description: level used for `console.log` calls

**levelForGlobalErrors**

* Default value: last item in the levels list
* Description: level used for global JavaScript errors logging

**serverUrl**

* Default value: none
* Description: URL of the server for sending logs

**disableGlobalErrorsLogging**

* Default value: `false`
* Description: flag for disabling the logging of global JavaScript errors (`window.onerror`)

## Credits

This project was inspired by [RESTHub](http://resthub.org/)'s [console.js](https://github.com/resthub/resthub-backbone-stack/blob/master/js/lib/resthub/console.js).
