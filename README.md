# behave-ui-hotkeys
A Marionette Behavior that allows you to add hotkey functionality to any view.

## Usage:

```
npm install --save behave-ui-hotkeys
```

Then just require and use as you would any other behavior:

```
var Hotkeys = require('behave-ui-hotkeys'),
    _ = require('underscore');

var View = Marionette.ItemView.extend({
    template: _.template('<h1>Hotkeys!!</h1>'),
    behaviors: {
        Hotkeys: {
            behaviorClass: Hotkeys,
            hotkeys: {
               'cmd:alt:y': 'viewMethod'
            }
        }
    },
    initialize: function() {
        this.on('hotkey:cmd:alt:y', function() {
            // hotkey fired!
        });
    },
    viewMethod: function(e) {
        // hotkey fired!
    }
});
```

NOTES:

 - You can use only one code (f1, 4, a, s, delete, pageup, etc), but as many helper keys (cmd, ctrl, alt, shift) as you would like
 - Codes are case insensitive, F1 will become f1, DELETE will become delete, etc...
 - If you specify a view method that does not exist, it will just call event
 - If you do not want to call a view method pass an empty string as the value, i.e.

```
hotkeys: {
    'ctrl:alt:o': 'open', // will fire event: 'hotkey:ctrl:alt:o', will call: this.view.open()
    'ctrl:alt:p': '' // will only fire event: 'hotkey:ctrl:alt:p', will not call any method
}
```

List of accepted codes:

- backspace
- tab
- enter
- return
- pause
- esc
- space
- pageup
- pagedown
- end
- home
- left
- up
- right
- down
- delete
- 0
- 1
- 2
- 3
- 4
- 5
- 6
- 7
- 8
- 9
- a
- b
- c
- d
- e
- f
- g
- h
- i
- j
- k
- l
- m
- n
- o
- p
- q
- r
- s
- t
- u
- v
- w
- x
- y
- z
- +
- \-
- f1
- f2
- f3
- f4
- f5
- f6
- f7
- f8
- f9
- f10
- f11
- f12

## Dev

To setup the dev environment just run `npm install`
You can then run `grunt watch` to automagically run tests and jshint

## Test

To run tests run either `npm test` or `grunt test`, former is an alias for the latter.

## Release History

- 0.0.1 - Initial Release
- 0.0.2 - Syntax highlighting added to readme
