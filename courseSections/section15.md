Continuous Integration and Continuous Delivery
==============================================

[Go to course navigation](../navigation.md)

The two phrases above, often shortened to CI and CD are currently big buzzwords that are often thrown around but rarely understood or used correctly. Throw in other things such as build pipelines and Integration and Feature tests and things can start to get a bit bewildering but at their heart both are simply good Agile practices that help us to deliver quality features directly to the end-user as fast as possible. So let's try and demystify all of this by creating our own Continuous Delivery pipeline for our Prototype website.

Before we go ahead implementing this let's talk first about Continuous Integration. The good news is that you've been practicing most of the key ideas already. Simply put, it is the practice of *integrating* your code into a shared repository as often as practicable. Each check in to this repository is then verified automatically by an automated build. there are a whole load of benefits to working inthis manner but as a developer the key benefits are that each check in is small, quick and easy: if anything does break i is easy to catch ad fix which ultimately means less time fixing bugs and more time adding features. Speaking ofhich:hich: our fantastic Business Analyst has already put together a user story in conjunction with our client.

```
As a prototypical business owner
I want an automated build pipeline
So that I detect integration issues as early as possible
```

Setting up an automated buld pipeline
-------------------------------------



