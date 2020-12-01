# Very, very basic jQuery for Koha

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

## The most basic answer: You can use jQuery to modify the way Koha loooks and operates *without* having to do a development.

<br /><br /><br /><br />

## Q: What is jQuery?

jQuery is a JavaScript library.

You can find out all about jQuery at:

[https://jquery.com/](https://jquery.com/){:target="\_blank"}

[https://www.w3schools.com/jquery/](https://www.w3schools.com/jquery/){:target="\_blank"}

### Q: Followup question - What's a JavaScript library?

In this context, a *library* is a set of pre-defined functions that can be accessed through a short-hand or abbreviated process.  For example, in JavaScript, the code needed to hide an element could look something like this:

~~~ JavaScript
document.getElementById("selector").style.display = "none";
~~~

while the same command in jQuery can be written this way:

~~~ JavaScript
$('selector').hide();
~~~

_('selector')_ replaces _document.getElementById("selector")_

_.hide()_ replaces _.style.display = "none";_

Simplifying the code needed to do something on a page makes it easier to learn how to create the code.

<br /><br />

## The most basic answer: jQuery is simplified JavaScript that anyone can learn.

<br /><br /><br /><br />

## The basic components of a piece of jQuery

All jQuery statements should start with dollar sign and end with a semicolon.  Then you'll need a pair of parentheses that includes an html selector in quotes and a jQuery event, effect, or method.
Starts with:

~~~ JavaScript
$ ;
~~~

Selectors are inside of quotes inside of parentheses

~~~JavaScript
('')
~~~

Events start with a . and are followed by something in parentheses

~~~JavaScript
.()
~~~

Put it all together and you get a basic skeleton for a piece of jQuery

~~~JavaScript
$('').();
~~~

<br /><br />

### Q: What is a selector?

A selector is a piece of code that tells jQuery which HTML element that jQuery is going to modify.

#### Q: What is an HTML element?

HTML elements are the pieces of a web page built by the HTML tags that tell your browser how to display the page.  Paragraphs begin with a \<p\> and end with a \</p\>.  Tables begin with \<table\> and end with \</table\>.  Input boxes have an \<input\> tag, forms have a \<form\> tag, headings have an \<h1\>, \<h2\>, \<h3\>, \<h4\>, \<h5\>, or \<h6\> tag, and so on and so on.

And any HTML tag can have attributes added to those tags that can help you select them.  Attributes like id, class, name and others.  

### The most basic answer:  A selector tells jQuery which part of the page to modify.

<br /><br />

### Q: What is an event, effect, or method?

Once you've selected something, you're going to want to do something with it.  An event is the code that tells jQuery, once something is selected, do something.  An effect tells jQuery, once something is selected, change that thing - or something else.  A method tells jQuery that, once something is selected, modify the HTML or the CSS for that thing - or something else.

Some useful events are .click(), .hover(), .toggle(), .resize()

Some simple effects are .fadeIn(), .fadeOut(), .hide(), and .show()

Some simple methods are .append(), .prePend(), .addClass(), .html(), and dozens others

### The most basic answer: an event, effect, or method takes the thing you've selected and makes something happen to that thing - or possibly to something else.

<br /><br />

## How do I create a selector?

If you are using Firefox or Chrome, type ctrl-shift-i to open the developer tools.

You can then click on the "Inspector" to look at the elements in the page.

<br /><br />

## The IntranetUserJS sytsem preferences

The documentation on the Koha wiki at [https://wiki.koha-community.org/wiki/JQuery_Library](https://wiki.koha-community.org/wiki/JQuery_Library){:target="\_blank"} has information on it about the need for  "$(document).ready(function() {  });"

There are two schools of though on this command.  

One school of thought says put "$(document).ready(function() {" at the beginning of this preference and "});" at the end and then put every piece of jQuery you write in the middle.

The other school of thought is to put each piece of jQuery you write inside of its own "$(document).ready(function() {  });"

Both methods work.  I prefer the first method.

<br /><br />

## A simple first piece of JQuery_Library - selecting by class

Make the "My account" drop-down disappear on all pages

~~~JavaScript
$('.toplinks-myaccount').hide();
~~~

Make the "My checkouts" drop-down disappear on all pages

~~~JavaScript
$('.toplinks-mycheckouts').hide();
~~~

Make the "Set library" drop-down disappear on all pages

~~~JavaScript
$('.toplinks:contains("Set library")').hide();
~~~

<br /><br />

## A simple second piece of JQuery_Library - selecting by ID

Make the subtype limits disappear on the advanced search page

~~~JavaScript
$('#subtype').hide();
~~~

Make the branch drop-down disappear on the login page

~~~JavaScript
$('#main_auth #branch').hide();
~~~

Make the branch drop-down label disappear on the login page

~~~JavaScript
$('#main_auth #loginform label[for="branch"]').hide();
~~~

Make the branch drop-down *and* the label disappear on the login page

~~~JavaScript
$('#main_auth #branch').parent().hide();
~~~

## Hiding just *hides* - *remove* remove_first:

~~~JavaScript
$('#main_auth #branch').parent().remove();
~~~

<br /><br />

## The first pieces of jQuery I learned:

Changing "Surname" to "Last name"

~~~JavaScript
$('label[for="surname"]').html('Last name:');
~~~

Changing "First name" to "First name/middle name"

~~~JavaScript
$('label[for="firstname"]').html('First name +<br />middle name:');
~~~

Changing "Other name" to "Nickname/other name"

~~~JavaScript
$('label[for="othernames"]').html('Nickname/<br />other name:');
~~~

<br /><br />

## How do I prefill an input field?

Password field 1 set to 1234 by default

~~~JavaScript
$('#entryform #password').val('1234');
~~~

Password field 2 set to 1234 by default

~~~JavaScript
$('#entryform #password2').val('1234');
~~~

Both password fields set to 1234 by default

~~~JavaScript
$('#entryform #password, #entryform #password2').val('1234');
~~~

We can do a lot more by creating a function, though:

~~~JavaScript
$("#entryform #surname").blur(function(){
  $("#entryform #password, #entryform #password2").val($("#entryform #surname").val());
});
~~~

A function like this takes an event and tells jQuery what to do when the event happens.  The "what to do" part usually consists of more jQuery.

Some people are asking "What's blur?"  It's the opposit of focus:

~~~JavaScript
$("#catalog_results #search-form").focus();
~~~

So far this has all been about the staff client, so let's flip over to the OPAC

This can hide an item type from the facets - replace BOOK with whatever item type you're trying to hide

~~~JavaScript
$('.facet-label a[title="BOOK"]').parent().hide();
~~~

Do some things on the suggestions page:

Let's make Item Type required

~~~JavaScript
$('#opac-usersuggestions #itemtype').attr('required','required');
~~~

Then we'll make the label red like other required things

~~~JavaScript
$('#opac-usersuggestions label[for="itemtype"]').attr('style','color: red;');
~~~

Then we'll add the word "required" in red after the drop-down

~~~JavaScript
$('#opac-usersuggestions #itemtype').parent().append('<span class="required">Required</span>');
~~~

Then we'll add some ids to the title and item type inputs

~~~JavaScript
$('#opac-usersuggestions #title').parent().attr('id','titleinput');
$('#opac-usersuggestions #itemtype').parent().attr('id','itypedrop');
~~~

Then we'll move the item type drop-down

~~~JavaScript
$('#itypedrop').insertAfter($('#titleinput'));
~~~

When we're done we've got

~~~JavaScript
$('#opac-usersuggestions #itemtype').attr('required','required');
$('#opac-usersuggestions label[for="itemtype"]').attr('style','color: red;');
$('#opac-usersuggestions #itemtype').parent().append('<span class="required">Required</span>');
$('#opac-usersuggestions #title').parent().attr('id','titleinput');
$('#opac-usersuggestions #itemtype').parent().attr('id','itypedrop');
$('#itypedrop').insertAfter($('#titleinput'));
~~~

<br /><br />
