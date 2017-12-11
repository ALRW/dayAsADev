Task 6 - Adding JavaScript for all of our elements
==================================================

[:globe_with_meridians: Go to course navigation :globe_with_meridians:](../navigation.md)

So first things first, let's create the content that we are going to use. Underneath the `<div class="prototype hidden">...</div>` add the following:

```html
<div class="contact hidden">
  <h2>Contact Us</h2>

  <strong>Via snailmail</strong>
  <address>
  Prototype, Inc.<br>
  1 Prototype Tower<br>
  London<br>
  PO00PP
  </address>

  <strong>Via the Interwebs</strong>
  <a href="mailto:#">example@example.com</a>
</div>
```

Now that we have the content we can extend our javascript in `app.js` to account for this new block.

```javascript
/* global $ */
$(document).ready(function(){

    $('#prototype').click(function(e){
        e.preventDefault();
        $('#contact, #about').removeClass('active');
        $('#prototype').addClass('active');
        $('.contact, .about').addClass('hidden');
        $('.prototype').removeClass('hidden');
    });

    $('#about').click(function(e){
        e.preventDefault();
        $('#about').addClass('active');
        $('#prototype, #contact').removeClass('active');
        $('.about').removeClass('hidden');
        $('.prototype, .contact').addClass('hidden');
    });

    $('#contact').click(function(e){
        e.preventDefault();
        $('#contact').addClass('active');
        $('#prototype, #about').removeClass('active');
        $('.contact').removeClass('hidden');
        $('.about, .prototype').addClass('hidden');
    });
});
```

The above code works and fulfils our user stories. We now have a nice working website and our client should be mightily pleased but should we? 

> Looking at the above code can you see any issues? Take a moment to think about what might be bad practice about the solution we've just implemented.

-----------

[:arrow_backward: Return to Previous Section](../courseSections/section11.md) | [Continue to next section :arrow_forward:](../courseSections/section12.md)
