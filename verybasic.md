# Very basic jQuery for Koha

<br /><br />

## Recap

George Williams: ["About" info](https://slides.hopperdietzel.org/about/){:target="_blank"}

jQuery is a JavaScript library that's used on many webpages.

You can add jQuery that you write into the Koha system preferences IntranetUserJS, OPACUserJS, SCOUserJS, and SelfCheckInUserJS.

Those system preferences need to be wrapped in $(document).ready(function() { /* jQuery goes here */ });

The Koha community Wiki has a jQuery library at: [jQuery library](https://wiki.koha-community.org/wiki/JQuery_Library){:target="_blank"}

A piece of jQuery consists of a selector (which tells jQuery what part of a page to modify) and an action (which tells jQuery what to do to the thing you've selected).

In Firefox and Chrome you can use the page inspector (ctrl-shift-i) to examine the code in a page to figure out what elements to select.

The rest of the Very, very basic jQuery presentation focused primarily on one of the simplest things jQuery can do - hiding elements on the page.

You can view the Very, very basic jQuery website here: [Very, very basic jQuery](veryverybasic.md){:target="_blank"}

And you can view the accompanying videorecording at: [Very, very basic jQuery Video](https://youtu.be/SqMqM6iRgvg?t=0){:target="_blank"}

<br /><br />

So, moving on.

I talked about some things after a good description of hiding things, but I didn't go into a lot of details, so I'm going to back-track to the first thing I learned how to do using jQuery.

## How do I change a piece of text on a page

The first pieces of jQuery I learned:

Changing "Surname" to "Last name"

~~~JavaScript
$('label[for="surname"]').text('Last name:');
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

## How do you remember all of the different options for selectors?

I don't.  I find the most useful site for keeping track of selectors is at [w3school's jQuery page](https://www.w3schools.com/jquery/){:target="_blank"}

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

## Can I prefill an input field with data from another input field?

~~~JavaScript
$("#entryform #surname").blur(function(){
  $("#entryform #password, #entryform #password2").val($("#entryform #surname").val());
});
~~~

## What's a function?

A function like this takes an event and tells jQuery what to do when the event happens.  The "what to do" part usually consists of more jQuery.

Right now some people are asking "What's blur?"  It's the opposite of focus:

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

## Can I add something to a page?

Let's add a button to clear messaging textboxes

~~~JavaScript
$("#patron_messaging_prefs_lgd").after("<p id='emailbuttons' style='margin: 5px'><button id='clearemail' type='button' style='margin: 5px'>Clear all</button></p>");
~~~

However, the button is useless until we add some jQuery that tells the button what to do.

~~~JavaScript
$("#clearemail").click( function() {
  $("#email1, #email2, #digest1, #digest2, #email4, #email5, #email6").prop('checked', false);
  $("#memberentry_messaging_prefs table select option[value=0]").attr("selected","selected");
});
~~~

<br /><br />
