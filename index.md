# Very basic jQuery


## How does jQuery relate to Koha?

Koha has 4 system preferences that allow users to add JavaScript and jQuery to the OPAC, the staff client, the self-check-out system, and the self-check-in system.  Knowing some basic jQuery will allow you to make some changes to the appearance and operation of these components of Koha.


## What is jQuery?

jQuery is a JavaScript library.


### OK.  What's a JavaScript library?

In this context, a *library* is a set of pre-defined functions that can be accessed through a short-hand or abbreviated process.  For example, in JavaScript, the code needed to hide an element would look something like this:

~~~ JavaScript
document.getElementById("selector").style.display = "none";
~~~

while the same command in jQuery can be written this way:

~~~ JavaScript
$("selector").hide();
~~~

_("selector")_ replaces _document.getElementById("selector")_

_.hide()_ replaces _.style.display = "none";_


## The basic elements of a piece of jQuery

All jQuery statements should start with dollar sign and end with a semicolon.  Then you'll need a pair of parentheses that includes a selector in quotes.


## What is a selector?

## How do I change the name of a label?

## How do I prefill an input field?

## How do I emphasize content?
