Continuous Deployment
=====================

[Go to course navigation](../navigation.md)

So we've setup a Continuous Integration pipeline but how does that help us with the idea of Continuous Delivery and why are we now talking about Continuous Deployment?

In short Continuous Integration is a way for us to produce artifacts that we are confident can be put in front of a user. Think of the life-cycle of a feature. We gather some requirements, build a feature against them and then make what we've built available to the user. Real feedback on this feature will only come at the point that a user is actually interacting with it. If we want to improve our products and features we want to do everything we can to reduce this feedback loop. 

So if we are continuously integrating our code and are happy that it can be used, can we find a way that will enable us to get it to the end user as quickly as possible? The answer is yes, Continuous Delivery: the delivery of features to the user as soon as they are ready. Continuous Deployment is, from a technical perspective, *how* we can achieve this.

Using Travis to Continuously Deploy
-----------------------------------

We have integrated Travis into our project to build our code and run our tests. Seperately we also have a deployed application setup on Heroku. Wouldn't it be great if every time we pushed our code to Github Travis ran all our tests, then if they passed that code was automatically pushed to Heroku and then deployed for all the world to see? Thankfully we've been discussing this because 
