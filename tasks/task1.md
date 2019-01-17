Task 1 - Creating a new route
=============================

[:globe_with_meridians: Go to course navigation :globe_with_meridians:](../navigation.md)


To create a new route that returns both of your names you need to add another method to the `server.rb` file like so:

```ruby
get '/names' do
  '[first name here] and [second name here]'
end
```

> Replace the square brackets and their contents with your names

Make sure you save the upated file. If you have your ruby process running then stop it by pressing `Ctrl-c` in the command-line . Startup the process again (or for the first time) with the newly updated ruby file by running:

```
$ ruby server.rb
```

You should now be able to visit `https://[application name, in our case prototypeWebsite]-[Your username].codeanyapp.com/names`
 and hopefully both of your names will be displayed for all to see!

Good job! :twisted_rightwards_arrows:

[:arrow_backward: Back to section 2](../courseSections/section2.md) | [Continue to Section 3 :arrow_forward:](../courseSections/section3.md)
