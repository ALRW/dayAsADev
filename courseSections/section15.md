Section 15 - Continuous Deployment
==================================

[Go to course navigation](../navigation.md)

So we've setup a Continuous Integration pipeline but how does that help us with the idea of Continuous Delivery and why are we now talking about Continuous Deployment?

In short Continuous Integration is a way for us to produce artifacts that we are confident can be put in front of a user. Think of the life-cycle of a feature. We gather some requirements, build a feature against them and then make what we've built available to the user. Real feedback on this feature will only come at the point that a user is actually interacting with it. If we want to improve our products and features we want to do everything we can to reduce this feedback loop. 

So if we are continuously integrating our code and are happy that it can be used, can we find a way that will enable us to get it to the end user as quickly as possible? The answer is yes, Continuous Delivery: the delivery of features to the user as soon as they are ready. Continuous Deployment is, from a technical perspective, *how* we can achieve this.

Using Travis to Continuously Deploy
-----------------------------------

We have integrated Travis into our project to build our code and run our tests. Seperately we also have a deployed application setup on Heroku. Wouldn't it be great if every time we pushed our code to Github Travis ran all our tests, then if they passed that code was automatically pushed to Heroku and then deployed for all the world to see? 

The first thing we need to be able to do is interact with Travis using the command line. Luckily for us the helpful folks at Travis have created a gem for this exact purpose. Let's add the following into our `Gemfile`:

```ruby
gem "travis"
```

and follow that up with a quick:

```
$ bundle install
```

Now that we have the Travis CLI (Command line interface) installed we can log into Travis, run the following:

```
$ travis login
```

Follow the prompts and enter your credentials to associate Travis with your Github repository. 

At this point we are ready to tell Travis to *Continuously Deploy* our application. Update your `.travis.yml` file to the following:

```yml
script: bundle exec rspec
deploy:
  provider:heroku
  api_key:
    secure:
  app:
```

Here we are telling Travis to deploy our code to our *provider* Heroku. You will also have noticed that we appear to have a few blank fields defined with no data associated with them.

The `api_key` is where we will define credentials that will allow Travis to identify itself to Heroku as being authorised by us. However, there is a catch: remember that we are pushing our code to Github and that our code, being open-source, is therefore visible to anyone with an internet connection. We therefore need to add an encrypted key that can be passed around and decrypted where needed. To do this automagically run the following command:

```
$ travis encrypt $(heroku auth:token) -r [Your github repo name here: e.g. ALRW/prototype-website] --add deploy.api_key
```

If you now open your `.travis.yml` it should look a little like the following:

```yml
script: bundle exec rspec
deploy:
  provider: heroku
    api_key:
        secure: WTD1P6b4f9mxV07XO9hiwCPRsE/a8fzBTL1xZjCM3d+xhQBk5r8G2pDO4zShrfZ7V5Ym2b+VA4TIbRienumGaqMcZqlvbxlYy7NU8W0VPGAUV05Y/vxH5Zi1/XEraNiLso1H4uSPsUfRgtG4/hgyQlASmHI4A6oCoOqFbyHDY4uPTigCbURE3xG95K6o0Xuwbikr+ibpnSkXcbLXJrOQF3GUuXv4OCfauRhsvEiDbnjfBgQB/iE9PG7wbKL9mXja+OsMWLfPu/sZHohl9JF2sG8hAve2HeAn8A5KK6YklQMkACvtJOz1l8yJ6waBRubQwTEuRfNUc2YJXoNvU7xtGsu9orO7QgEoc1Ps3K+zNHIMOuFJEbIKcy7+8jD/LQxyXtWUvl54+A5nJpR/jiiCPQvXXJf9QStRg516UzAj0JP9zBmxTuPBn/ghaORQqnZa6pctbcg96ri/0iuO9jqj1O6Tj6KeuVpg/YBF+m/Cjimt5Ussv6+e4MLqKBpHrK76v4UcJe3bArWu2AItQpVd1XD3AXjuZ2kotlOi7FhAmovAW/2LrmlpYYVPP+YPLbSbRtxBfIupxHe4pO3tMOYFmT/NOy2/79pXXz+0YkDLd8ELL9NRM92WkU93DIe3SgMB5rjebfTYxqZP23YcKNFJUyduV5Q+dIgmsG2XNSGvnqI=
  app:
```

Now that we can easily authenticate with Heroku from Travis we can only need to tell travis the name of our app on Heroku. Update the final line of the `.travis.yml` with the name of your application:

```yml
app: delicious-pie-39548
```

> If you're wondering how to find the name, it can be found [here](https://dashboard.heroku.com/apps).

----------------------------------

:twisted_rightwards_arrows: - When you commit and push your code this time watch the progress of the build on Travis. 

Now have a play around: make a small change, say choose a different prototype image or change some of the text on one of our tabs. Commit and push this, once the build completes does it show up when you access your production environment? 

With all of that working, in your `index.erb` amend the `<h2>Home of the World's Best Prototypes</h2>` to a different title. When you commit and push this what happens? What did you expect?

Finally Let's reset all of these changes before we move forward:

in the command line run the following:
```
$ git reset --hard @~2
```

> If you have made more than two commits that you wish to roll-back then replace 2 with that number

When and only when you are happy that you have your project in the correct state run the following:

```
$ git push -f origin master
```

----------------------------------
[Return to previous section](../courseSections/section14.md) | [Continue to the answers](../tasks/task7.md)
