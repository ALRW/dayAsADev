Task 1 - Answers
================

Hopefully you found that a relatively straightforward task to begin with.

To create a new route that returned both of your names when accessed you need to add another route to the `server.rb` file like so:

```ruby
get /names do
  '[first name here] and [second name here]'
end
```

Putting in your own names as required. Then make sure you save the upated file. If you have your ruby process running stop in the command-line then stop it by pressing `Ctrl-c`. Startup the process again (or for the first time) with the newly updated ruby file by running:

```
$ ruby server.rb
```

You should now be able to visit `https://prototype-website-[Your username].c9users.io/names` and hopefully both of your names will be displayed for all to see!

Good job! :twisted_rightwards_arrows:

[Back to section 2](../courseSections/section2.md) | [Continue to Section 3](../courseSections/section3.md)
