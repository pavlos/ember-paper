# Contributing to ember-paper

## Coordination, communication and community

Many ember-paper contributor hang out on the [ember-paper channel on slack](https://embercommunity.slack.com/messages/ember-paper/). Not a slack user? [Get your invitation.](https://ember-community-slackin.herokuapp.com/)

## Coding style

* ember-paper uses the [ember-suave](https://github.com/DockYard/ember-suave) coding style.

* Before submitting a pull request,
check for coding style issues with  `jscs -c .jscsrc app addon`.

* Require action closures rather than strings representing action names.
`{{some-component someAction=(action "myAction")}}`, not `{{some-component someAction="myAction"}}`.

## Capitalization and naming

* Use camelCase for variable names, formal arguments, parameters, and all other uses, except as below.

* This includes action names, even those that correspond to JavaScript native events, such as
`{{some-component onClick=(action "someAction")}}`, not `{{some-component onclick=(action "someAction")}}`.

* Use SHOUTING_SNAKE_CASE for constants. `const NUMBER_OF_THINGIES = 10;`.

* As required by Ember, component names, module names, and file name should continue to be kebab-cased, such as
`{{paper-input}}` and the filepath `ember-paper/addon/components/paper-input.js`.

## Importing

* Import the module, then use const object destructing to extract the desired methods. For example,
```javascript
import Ember from 'ember';
const { computed } = Ember;
```

* When the destructured object assignment statement exceeds 80 columns, put each variable it its own line:
```javascript
const {
  $,
  Mixin,
  String: { htmlSafe },
  RSVP: { Promise },
  computed,
  on,
  inject: { service },
  run: { scheduleOnce }
} = Ember;
```
* Order the imported variables in order of appearance, or other logical order.

## Converting components from Angular Material

* Use an ember-paper name for components. Convert angular elements attributes to ember boolean properties.
```javascript
<md-tabs md-dynamic-height md-border-bottom>
```
becomes
```javascript
{{paper-tabs dynamicHeight=true borderBottom=true}}
```

* Seek to provide feature parity using Angular Material styles, but implemented in an Ember-centric way.