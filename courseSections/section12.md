Refactoring
===========

[:globe_with_meridians: Go to course navigation :globe_with_meridians:](./navigation.md)

Looking at our implementation of the show-hide logic for moving between tabs there is clearly a large amount of duplicated code. But why is this a bad thing? I mean we've tested that it works and we've fulfilled our requirements, surely that should be good enough? Not quite: think about the next time our client asks us to add a tab. It's just a little bit more work that the last time we did it. Now think what would happen if our website had 30 or 40 pages each with their own tab views that now need to be updated. This solution is clumsy and doesn't lend itself to extension.

So what should we do? 

The simple answer is look for a better solution. A key skill to gain is the ability to spot repetition in code. Repetition is almost always a sign that your current implementation has reached its limits and now you need to abstract the common logic. Holding this common logic in one place then provides you with a better, optimised solution to the problem. 

> Take a moment now to look at the code we've written. Grab a piece of paper and try to describe in English how you might **refactor** this problem to remove the repetition.

Abstracting repetition
----------------------

When thinking about the above problem we can see that in our code the only thing that really changes in each of our show/hide methods is the name of the element that we are operating. Ideally we would like some way of creating a default piece of logic that can be passed around that either shows or hides a tab depending on which one has been clicked. 

While there are multiple ways that this could be achieved here is one implemenation. If you want to use it then it should completely replace everything that is in `app.js`.

```javascript
/*global $ */
$(document).ready(function(){
  
  var tabs = ['contact', 'about', 'prototype'];

  function eventHandler(event){
    event.preventDefault();
    tabs.forEach(function(item){
      if(event.currentTarget.id === item){
        $('#' + item).addClass('active');
        $('.'+item).removeClass('hidden');
      } else {
        $('#' + item).removeClass('active');
        $('.' + item).addClass('hidden');
      }
    });
  }

  $('#prototype').click(eventHandler);
  $('#about').click(eventHandler);
  $('#contact').click(eventHandler);

});
```

There are still ways that this code can be improved but for now this should do. Now all we have to do if we're asked to add a new tab is add it to the tabs *array* and then add a call to our `eventHandler` function when it's clicked. Much simpler! Hopefully, this also illustrates how less code can actually do more for you.

Moving on
---------

You'll be glad to hear that our client has decided that the website is ready to be released to the wider world! You've done a great job now all we need to do is find some way of getting this out onto the web permanently.

:twisted_rightwards_arrows: commit and push your code, switch over your driver and navigator and we'll move onto looking at deployment.

[Return to previous section](../tasks/task6.md) | [Continue to next section](../courseSections/section13.md)
