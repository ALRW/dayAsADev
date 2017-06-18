Section 7 - A Prototype Website
==============================

[Go to course navigation](../navigation.md)

You've come a long way already today and now that we've accumulated a large amount of building-block knowledge lets put it to use and actually build ourselves a prototype website. 

To set the scene. A potential client has expressed interest in revamping their business website and wants to see what we are capable of. They have asked us to produce a prototype website for their "prototype" business. Kindly they have also provided us with a few user stories and a number of wireframes to work with. Fantastic.

To start with.

```
As a prototypical business owner
I need a website
To communicate my prototypes to the world
```

```
As a prototypical user 
I would like a navigation bar
In order to navigate around a prototype website
```

```
As a logo obsessed prototypical business owner
I need to see my prototype logo and company name on the website navigation bar
In order to be able to sleep at night
```

```
As a detail oriented prototypical user
I would like to see a description of my prototype business on the websites home page
In order to understand what a "prototype" business is
```

And an initial wireframe of the page:

![first Wireframe](../images/firstWireframe.png)

Where do I start?!!
-------------------

Ok so we have our starting requirements, but maybe you're thinking "*how am I going to get from the simple page with a bit of text to a pristine looking webpage?*" :confused: that is to say, this looks like a rather large jump in task size. This is a common theme for developers so it is worth discussing now. A developer produces the best results when faced with a small narrowly defined piece of work. However, we live in the real world and as this task demonstrates we need to be able to deliver. So mentally we need to break down the work into smaller bite-size chunks that we can easily reason about and therefore complete.

You may have heard developers talk about **Front end** and **Back end** - the terminology may sound a little dodgy but this is an example of this kind of *breaking down* that allows us to reason about seperate parts of the same task. Concretely, you have already done both front-end and back end development. When you created your ruby program:

```ruby
get '/' do
  erb :index
end
```
that was you programming the back-end server to perform the task of automatically getting you a particular resource when you asked for it.

the `index.erb` that you created is your front end: the resource that will be returned to you and rendered in your web browser. Developers who work creating content for both the front end and back end are known as a full-stack developers.

So onto the first user story. To get this prototype website off the ground we need to have a route setup to serve this page for us. Handily we've already done this with the above piece of code. Why reinvent the wheel when we can reuse the work we've already done. If that feels to easy, don't worry that will all change soon!

Adding a front-end framework
----------------------------

We now want to move on to updating the content. You may remember that we've been using the framework (just a fancy way of saying someone elses code) **Sinatra** to help with our back-end. Well now we are going to do the same with our front-end using a framework called [Bootstrap](https://getbootstrap.com/) to help structure our page and make it look pretty.

As you may also remember the first thing we need to do is tell our program that it needs to incorporate this framework. 

Open up your `index.erb` in Cloud9 and update it to look like this:

```html
<!DOCTYPE html>
<html>
<head>
  <title>Prototype website</title>
  <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css" integrity="sha384-BVYiiSIFeK1dGmJRAkycuHAHRg32OmUcww7on3RYdg4Va+PmSTsz/K68vbdEjh4u" crossorigin="anonymous">
</head>
<body>
   <h1>Prototype Website</h1>
   <p>By tonight I'll have a fully-functioning website!</p>
</body>
</html>
```

This addition of the `<link rel="stylesheet" ... >` tells our html template to go and get the external resource located at the link specified in the `href` attribute. Don't worry too much about the specifics of the other attributes for now, suffice to say they are security related and ensure that we are pulling in what we intend and not some malicious code.

Navbar
-----

Now that we have access to bootstrap lets move forward to the next user story.

Update the `<body> ... </body>` section of your `index.erb` file with the following:

```html
<body>
  <nav class="navbar navbar-default">
    <div class="container-fluid">
    </div>
  </nav>
</body>
```

Remember to save your file and then if you need to, start up your sever again using the commands below, or otherwise just refresh the page.

```
$ ruby server.rb -p $PORT -o $IP
```

Hopefully when you preview your masterpiece you should see the following rather unexciting page.

![blank navbar](../images/blankNavbar.png)

Task 3
------

:twisted_rightwards_arrows: Now's a good opportunity to switch using git to add, commit, push and pull your changes.

Another thing developers spend a large amount of their time on is reading documentation. We've pulled in the bootstrap framework which gives us access to a whole bag of tools, their documentation is how we learn how to use the toolkit so lets do some research:

 - [ ] Using the documentation below add the company logo and name: "Prototype Inc." to the navigation bar to fulfil the following user story

```
As a logo obsessed prototypical business owner
I need to see my prototype logo and company name on the website navigation bar
In order to be able to sleep at night
```

For this task you should have a look at the bootstrap documentation for navbars [bootstrap documentation for navbars](https://getbootstrap.com/components/#navbar). You may also want to look into how the [html <img> tag works](https://www.w3schools.com/tags/tag_img.asp). 

Kindly our client has provided the following logo for us:

![fullLogo](../images/fullLogo.png)

The icon you need to add can be loaded from the following url:

```
https://raw.githubusercontent.com/ALRW/dayAsADev/master/images/glyphicon.png
```

The client has also asked the we add the company name as a `<h4></h4>` size element.

Good luck!

[Return to previous section](../tasks/task2.md) | [Continue to answers](../tasks/task3.md)
