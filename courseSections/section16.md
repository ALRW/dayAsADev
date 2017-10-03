Changing Requirements, Rotting Code and Test Driven Development!
==================================================================

For this final section we're going air a few aspects of developer dirty laundry and look at how we can possibly try and mitigate them.

As if by magic our client has also just come to us with some requirements that nicely illustrate these points. Their UX (User Experience) team have been doing some research with the public on our live prototype website and have come up with some interesting findings.

As the following highly technical graph shows it seems that there is some variation in the way that people contact Prototype Inc.

![graph](../images/graph.png)

Our mysterious client would like to simplify the number of methods of communication and also the number of clicks a user has to make to access contact information.

As the wireframe below shows, they would like us to remove the contact tab and add in a `mailto` link to the navbar that will be available at all times.

![final wireframe](../images/finalWireframe.png)

Why am I deleting everything?
-----------------------------

This is a great example of a common occurance during any development project. Requirements that effect, modify or straight up remove a previous feature. This process multiplied many times leads to what is sometimes known as **[code rot](http://www.agile-process.org/change.html)**. Essentially each new change may lead to new subtle bugs that take time to fix and can themselves lead to even more subtle bugs. Eventually, in a worst case scenario, the cost of maintaining the code-base exceeds the resources available and it is actually more efficient to start from scratch.

This also leads us onto the topic of **[technical debt](https://martinfowler.com/bliki/TechnicalDebt.html)**. In our case for this new requirement we could just delete the `Contact` tab from our navbar. This would nuke that feature in the fastest time possible allowing to get on with adding in the new `mailto` icon. However, we would be left with a whole load of redundant code that could potentially cause bugs in the future. If we needed to get this new feature out to our customers ASAP this might be acceptable but over time, constantly incurring similar debts would leave us in a position where our ability to deliver would grind to a halt. Keeping technical debt under control is crucial in the long run.

As a rule, taking on technical debt should be a conscious choice as well as being the exception rather than the norm. One way to help ensure this is robust tests with code that is written to be easily testable and this leads us nicely to another Agile development practice.

Test Driven Development
----------------------


![TDD](../images/tdd.png)

----------------------------------
[Return to previous section](../courseSections/section14.md) | [Continue to the answers](../tasks/task7.md)
