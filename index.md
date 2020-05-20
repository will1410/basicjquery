# Very basic jQuery

<br /><br />

# Very, very basic jQuery

<br /><br />

# Very, very, very basic jQuery

<br /><br />

## Q: What does jQuery have to do with Koha?

Koha has 4 system preferences that allow users to add JavaScript and jQuery to the OPAC, the staff client, the self-check-out system, and the self-check-in system.  Knowing some basic jQuery will allow you to make some changes to the appearance and operation of these components of Koha.

### Q: Next question - what are those 4 system preferences?

* __*IntranetUserJS*__ (adds JavaScript and jQuery to the staff client)
* __*OPACUserJS*__ (adds JavaScript and jQuery to the OPAC)
* __*SCOUserJS*__ (adds JavaScript and jQuery to the self-checkout system)
* __*SelfCheckInUserJS*__ (adds JavaScript and jQuery to the self check-in system)

The easiest ways to access all of these system preferences at once is to use the "Search system preferences" search box on the system administration page and search for __*UserJS*__

<br /><br />

## A: You can use jQuery to modify the way Koha loooks and operates *without* having to do a development.

<br /><br /><br /><br />

## What is jQuery?

jQuery is a JavaScript library.  

### OK.  What's a JavaScript library?

In this context, a *library* is a set of pre-defined functions that can be accessed through a short-hand or abbreviated process.  For example, in JavaScript, the code needed to hide an element could look something like this:

~~~ JavaScript
document.getElementById("selector").style.display = "none";
~~~

while the same command in jQuery can be written this way:

~~~ JavaScript
$("selector").hide();
~~~

_("selector")_ replaces _document.getElementById("selector")_

_.hide()_ replaces _.style.display = "none";_  

<br /><br />

## A: jQuery is simplified JavaScript that anyone can learn.

<br /><br /><br /><br />

## The basic components of a piece of jQuery

All jQuery statements should start with dollar sign and end with a semicolon.  Then you'll need a pair of parentheses that includes an html selector in quotes and a jQuery event or effect.

### What is a selector?

A selector is an HTML element used by jQuery to tell jQuery which part of the page your code is going to manipulate.

### What is an event or effect?



<br /><br />

## How do I change the name of a label?

<br /><br />

## How do I prefill an input field?

<br /><br />

## How do I emphasize content?
