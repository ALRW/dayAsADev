Section 9 - Adding our own style
================================

So what is Bootstrap providing for us under the scenes? So far we've written a little Ruby (telling our computer what to do), a little HTML (decribing the structure of the content we want for our page) and now we come to CSS.

CSS (more formally Cascading Style Sheets) is the technology we use to define the *layout* and *design* of the HTML *structure* we have already written. Without CSS our webpages would just be a load of left-justified, black-text-on-white-backgorund monstrosities.

Bootstrap will take us a long way, particularly when it comes to our page layout and scaling across different devices, but it still leaves a little to be desired in the looks department. So lets get under the hood and add our own styling to take our site to the next level.

Making our homepage pretty
--------------------------

Following a quick show-and-tell with our product owner they remarked that they would like the prototype to adhere to their prototype colour scheme and have provided us with an additional user story and a handy colour palette.

```
As a prototypical business owner
I want my site to be decked out in prototypical colours
So that my eyes are soothed every time I open my web-browser
```

And the colour palette for us to use:

![Prototype colour palette](../images/colourPalette.png)

Inline styling
--------------

Before we get down into the weeds we'll start with soe of the basics.

To style our page we can add some CSS directly to our `index.erb` file by adding the `style` attribute to the HTML tag that you want to apply it to.

So for example, try the following in `index.erb` 

```html
<body style="background-color: red !important">
  ...
</body>
```

How red does your page look now?! 

The CSS we just added tells the browser to render the body of our page - i.e everything that's visible on the screen - with the specified background colour. Once upon a time, all CSS was added directly inline with the HTML like this. However, as with our ruby code this is going to be difficult to read and maintain. We want to put all of our styles in a separate file (or files) and keep our code DRY. As an aside the DRY principle (Don't repeat yourself) is key to being a developer. Essentially Duplication is waste and is likely to lead to code and processes that are harder to understand and much more error prone. Duplication of logic (which we are dealing with here) should be eliminated by abstraction while duplication of processes should be eliminated by automation. 

> Have a think about the many tasks that you do repetitively day in day out - could any of these be automated? If so how? If you can answer those questions maybe there's a startup in the making!

If you would like to know more about DRY and other key principles that guide software development then have a read of this article on the aptly names [Giant Robots Smashing into Other Giant Robots Blog](https://robots.thoughtbot.com/back-to-basics-solid).

Creating our own CSS
--------------------

Remove the inline style that we added in the last step so that you are left with `<body> ... </body>`. Now create a `public` folder in your Cloud9 workspace and then add a `css` folder inside `public`. Finally create a file called `application.css` inside the `css` folder. At the end your file tree should look a little like this:

![file tree](../images/fileTree.png)

Lets firstly change the background colour to be in line with the colour palette we've been given. Add the following:

```css
body {
    background-color: #F0F8FF;
}
```

You can interpret this Css code as being the following instruction to the browser: *render* any `<body>` *element* on the page using the background colour with the Hex value `#F0F8FF`. In the case of `body` there should only ever be one on the page. But if you were refering to paragraph elements: `<p>` there could be many spread across the page.

Refresh your preview. Did it work? Did you expect it to work? It doesn't matter whether you were right or wrong - what matters is how you use that outcome to progress. Take a few moments ot consider the changes we just made and how they might have effected the outcome.

The answer is that the browser doesn't know anything about `public/css/application.css`. Why would it? It's our responsiblity to tell the browser abut this external stylesheet. Fortuantely, that's another fundamental part of the way the web works. In fact you've already done it once before!

In the same way we had to tell our html in `index.erb` to use the bootstrap css framework we now need to tell it to also pull in our newly created `application.css`.

Update your `<head>...</head>` section to include the following:

```html
<link rel="sylesheet" href="/css/application.css" type="text/css">
```

Notice how our `href` is in this case pointing to our local file rather than a remote url and that we don't need to add the `public`. Make sure your `index.erb` file is saved and then switch over to your blank `application.css`.

Now refresh your browser. The background should be *Alice Blue*.

That's probably not the most exciting change you've ever seen so lets start fleshing things out with a bit of styling to our `jumbotron` element. Add the following to `application.css`.

```css
.jumbotron {
  margin-top: 5em;
  background-color: #AFCBFF;
  border: solid 2px #0E1C36;
  color: #0E1C36;
}
```

> Why do you think we've described the jumbotron using `.jumbotron` in our css file? If you're struggling to understand it then maybe [this will help](https://www.w3schools.com/cssref/sel_class.asp).

Now if you refresh your browser you should see a nicely outlined and colourful jumbotron more centrally positioned on our homepage.

Task 4
------

:twisted_rightwards_arrows:

 - [ ] Our work on the current user story is not complete. Our navbar is still looking distincly "off brand". Style the navbar to bring it inline with the rest of our site and the colour palette. Feel free to go rogue and change the colors and value we've used in our CSS so far. The goal is to have a nice colourful site by the end.

[Return to previous section](../courseSections/section8.md) | [Continue to the Answers](../tasks/task4.md)
