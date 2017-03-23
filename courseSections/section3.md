Step 3 - Responding with HTML
=============================

Admittedly, sending a single string 'Hello world!' to a browser window is not very useful. It is, however, worth it to see how much a web framework does for you. All we had to do in our `server.rb` file was define a **path** (`/`) and a response (`Hello world!`).

The path forms part of the URL to which the browser makes a request - it's the bit that comes after the domain (i.e. `https://prototype-website-[Your username].c9users.io/`). The single slash (`'/'`) denotes the **root path** - i.e. `https://prototype-website-[Your username].c9users.io/[Nothing Here]`

Rather than return a single string, let's respond with some HTML. HTML (Hyper Text Markup Language) is the language of the web and it is used to define the *structure* and *content* of a 'page'. Since HTML is just text, you might be tempted to do this:

```ruby
require 'sinatra'

get '/' do
  '<html><body><h1>Hello World</h1></body></html>'
end
```

Try it. You will need to stop and restart your program after making the changes.

> Why is it necessary to stop and restart the program? It may or may not be obvious - but it's good to ask yourself these questions.

Did it work? It should have. But it's not very pretty and HTML pages can get *very long*, so this approach is not going to scale very well. Ideally, we want to separate the HTML into its own file so it's easier to maintain. Again, this is so fundamental it's already built into Sinatra.

Create a new folder in your workspace called `views`. Create a new file inside the `views` folder called `index.erb` with the following content:

```html
<!DOCTYPE html>
<html>
<head>
  <title>Prototype Website</title>
  </head>
  <body>
    <h1>Prototype Website</h1>
      <p>By tonight I'll have a fully-functioning website!</p>
  </body>
</html>
```

Now change the `server.rb` to the following:

```ruby
require 'sinatra'

get '/' do
  erb ":index
end
```

Save the changes and re-run  the program. You might be wondering what the `erb :index` means and why the file is called `index.erb`. If you're not wondering that, then you should be - unless you know already!

Without going too far into the technology of ERB (Embedded Ruby) and how Sinatra uses it, it's sufficient to understand the `erb :index` looks for a file called `./views/index.erb`, loads it, and returns the contents as text (in this case, the text is HTML).

Hopefully, you should see something like this:

![This is what it should look like](../images/indexErb.png)

:twisted_rightwards_arrows: You know what to do.

[Previous page](./section2.md) | [Continue to Step 4](./section4.md)
