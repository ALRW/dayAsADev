Section 12 - Refactoring
=======================

:construction: **UNDER CONSTRUCTION** :construction:

So looking at our implementation of the show-hide logic when moving between tabs there is obviously a large amount of code that is repeated. Why is this a bad thing? Simply put every time in the future that our client asks us to add another tab we not only need to add a new function to show it, we also need to go back and add the `id` and `class` of our new tab to each of the existing functions.

In addition we have another problem, in order to be certain that we are only showing the correct item we telling the computer to add and remove classes from items that do not have them. While this is currently gracefully handled by JQuery it could lead tobugs and unwanted side-effects in the future. 

This leadsus very nicely to the topic of refactoring.

[Return to previous section](../tasks/task6.md) | [Continue to next section](../courseSections/section13.md)
