Adding Technical Debt
=====================

[:globe_with_meridians: Go to course navigation :globe_with_meridians:](../navigation.md)

Red
---

The first thing we want to do is write a test for the first, smallest bit of functionality that we want to add:

```ruby
describe 'mailto link' do

  it 'is right justified on the navigation bar' do
    get '/'
    expect(last_response.body).to include "<ul class=\"nav navbar-nav navbar-right\">"
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
4 examples, 1 failure

Failed examples:

rspec ./spec/app_spec.rb:27 # Prototype App displays the mail link with the correct address
```

Great! we have our failing tests. We can now go about implementing this simple feature.

Green
-----

To get this test to pass we need to add our mailto icon to the navbar as specified by our test. In `index.erb` add the following within the `<div class="collapse navbar-collapse>...</div>` after the closing `</ul>`

```html
<ul class="nav navbar-nav navbar-right">
</ul>
```

Ensure that all your changes have been saved and then run your tests hopefully if all has gone well you should be presented with the following:

```
Finished in 0.03435 seconds (files took 0.18052 seconds to load)
4 examples, 0 failures
```

Simple!

Refactor
--------

At this point there are a number of things to consider before we move to refactor. We certainly have a lot of things we know we need to remove but is now the right time? 

The answer is possibly. This is a subjective decision: do you think you're next round of TDD would be helped or hindered by any refactoring at this point? Only you can answer that question. For now we'll make the decision to hold off until our feature is fully implemented and go for another round of Red -> Green -> Refactor.

Red
---

Let's now add our next failing test:

```ruby
it 'displays the mailto link with the correct address' do
  get '/'
  expect(last_response.body).to include "<li id=\"mail\"><a href=\"mailto:example@example.com\"><span class=\"glyphicon glyphicon-envelope\"></span></a></li>"
end
```

Green
-----

And now to make it pass simply insert the following inbetween our `<ul>...</ul>` tags.

```html
<li id="mail"><a href="mailto:example@example.com"><span class="glyphicon glyphicon-envelope"></span></a></li>
```

Fantastic if we run our tests now we should see the following output:

```
Finished in 0.03821 seconds (files took 0.18052 seconds to load)
5 examples, 0 failures
```

Refactor
--------

> Before moving forward take a moment to reflect on what we've just done. Throughout this process we haven't even had to open our browser and refresh the page to check whether our feature is actually there. That's been handled by the code (although you can go and check if you don't belive the tests). I don't know about you but it's a lot faster and involves a lot less switching between tabs, windows and screens.

We're not quite done yet though, the old prototype tab is still there. We need to refactor this out of existence!

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

----------------

[:arrow_backward: Return to previous section](../courseSections/section16.md) | [Continue to the next section :arrow_forward:](../courseSections/section17.md)
