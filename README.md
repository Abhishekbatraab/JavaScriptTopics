# JavaScriptTopics
## Prototypal inheritance

In programming we have to take something and extend it.

For instance, we have a `user` object with its properties and methods, and you want to make `guest` and `admin` as slightly modified variants of it.
. we'd like to reuse what we have in `user`, not copy/reimplement its methods, just build a new object on top it.

_Prototypal inheritance_ is a language feature that helps in that.

**[[Prototype]]**

In JavaScript, objects have a special hidden property `[[Prototype]]`  that is either `null` or references another object. That object is called “a prototype”:

![prototype](object-prototype-empty.png)

That `[[Prototype]]` has a “magical” meaning. When we want to read a property from `object`, and it’s missing, 
JavaScript automatically takes it from the prototype. In programming, such thing is called “prototypal inheritance”. 
Many cool language features and programming techniques are based on it.

The property [[Prototype]] is internal and hidden, but there are many ways to set it.
One of them is to use `__proto__`, like this:

```
let animal = {
  eats: true
};
let rabbit = {
  jumps: true
};
rabbit.__proto__ = animal;
// we can find both properties in rabbit now:
alert( rabbit.eats ); // true (**)
alert( rabbit.jumps ); // true
```

