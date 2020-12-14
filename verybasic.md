# Very basic jQuery for Koha

<br /><br />

Recap - website updated

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
