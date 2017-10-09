Adding Technical Debt
=====================

[Go to course navigation](../navigation.md)

Red
---

So first thing we want to do is write our test. Following the convention that we've used so far we'll go for a simple test that checks our page for the presence of our image and link in the correct place as so:

```ruby
describe 'mailto link' do

  it 'is right justified on the navigation bar' do
    get '/'
    expect(last_response.body).to include "<ul class=\"nav navbar-nav navbar-right\">"
  end

  it 'displays the mailto link with the correct address' do
    get '/'
    expect(last_response.body).to include "<li id=\"mail\"><a href=\"mailto:example@example.com\"><span class=\"glyphicon glyphicon-envelope\"></span></a></li>"
  end

end
```

> Note that this describe sits within our 

```ruby
describe 'Prototype App' do
...
end
```

Now running our tests:

```
$ rspec
```

should give us the a large output along with the following status:

```
Finished in 0.11304 seconds (files took 0.40698 seconds to load)
5 examples, 2 failure

Failed examples:

rspec ./spec/app_spec.rb:27 # Prototype App displays the mail link with the correct address
```

Great! we have our failing tests. We can now go about implementing this simple feature.

Green
-----

To get this test to pass we need to add our mailto icon to the navbar as specified by our test. In `index.erb` add the following within the `<div class="collapse navbar-collapse>...</div>` after the closing `</ul>`

```html
<ul class="nav navbar-nav navbar-right">
  <li id="mail"><a href="mailto:example@example.com"><span class="glyphicon glyphicon-envelope"></span></a></li>
</ul>
```

Ensure that all your changes have been saved and then run your tests hopefully if all has gone well you should be presented with the following:

```
Finished in 0.03435 seconds (files took 0.18052 seconds to load)
5 examples, 0 failures
```

Refactor
--------

Take a moment to think that throughout this process we haven't even had to open our browser and refresh the page to check whether our feature is actually there. That's been handled by the code (although you can go and check if you don't belive the tests).

One thing you should see now is that the old prototype tab is still there. We need to refactor this out of existence!

Remove all the offending code from your `index.erb` **and** from our `app.js`.

Ok brilliant, we've refactored our HTML by removing a load of unwanted content but what about improving the quality of our tests, afterall they are part of our code-base.

In each of our tests we start by calling

```ruby
get '/'
```

If we think about it we only need to get this page once for all of our tests so we can remove this from each of our specs and instead at the top of our `app_spec.rb` we can add the following:

```ruby
before(:all) do
  get '/'
end
```

Lastly in many of our specs we are checking the body of the page. It might be nice to encapsulate this fact in a helper method:

```ruby
def body
  last_response.body
end
```

Then in each of our tests:

```ruby
expect(body) to include ...
```

As you can see we're getting to the stage now where in our current state further refactoring will give us only minor gains. This would mark the natural point to start implementing any other new features safe in the knowledge that our features are covered by a good suite of tests.

----------------

Push your code up to Github watch the build progress through Travis CI and all being well deploy automatically to Heroku. Impressive stuff.

[Return to previous section](../courseSections/section16.md) | [Continue to the next section](../courseSections/section17.md)
