$.validateJSON
==============

When called from a form field (such as a textarea) which has
been populated with JSON, the validateJSON jQuery plugin will validate the 
contents, format the result, and call an onSuccess or onError callback.

The JSON validation is jacked straight from [JSON Lint](http://jsonlint.com), but
the plugin part is original. If there's anything broken, it's probably in the 
plugin. 

Options
-------

You can pass any of the following four *optional* params:

**compress**

*Boolean*, Compress the JSON after validation. Default: false.

**reformat**

*Boolean*, Prettify the JSON after validation. Default: true.

**onSuccess (json)**

*Function*, Called upon successful validation of the JSON. Default: noop. Passes a single param 
which contains an object:

```json
{
  valid: true
  json: {}
}
```

**onError**

*Function*, Called upon failed validation of the JSON. Default: noop. Passes a single param 
which contains an error object:

```json
{
  message: "Error message"
}
```

Usage
-----

Call validateJSON from a textarea:

```javascript
$("#json").validateJSON({
  // Compress the result
  // default: false
  compress: false, 
  
  // Prettify the result
  // default: true
  reformat: true, 
  
  // Call on valid
  // default: noop
  onSuccess: function (json) {},
  
  // Call on invalid
  // default: noop
  onError: function (error) {
    // error.message
  }
})
```

Callback Usage
-------------

```javascript
var jsonResults = $("#result");
var jsonInput = $("#json_input");

jsonInput.validateJSON({
  'onSuccess': function(json) {
    jsonResults.removeClass('ui-state-error').text('Valid JSON');
  },
  'onError': function(error) {
    jsonResults.addClass('ui-state-error').text(error.message || "Invalid");
  }
});
```


