Section 6 - Pulling code from Github
====================================

By now you know how to create a repo locally and push your local code to Github. You also need ot know how to get your code back from Github. Let's say you and one other develooper work on a website together. You both have local repos and a Github repository that you both have added as a remote called "origin". Your colleague made some changes to the website and pushed them to github. How do you get them? you need to "pull" them:

```
$ git pull origin master
```

Running this command tells git to get all the latest commits from origin and copy them into your local repository. Try pulling the changes in Cloud9 now. Nothing will happen because there are no remote changes.

Let's make a remote change. We'll use github UI for this but normally this would happen because someone else pushed new code.

Go to your git repo and click on your `README.md` file.

There is an edit button :pencil2:. Click on this and add the following to the readme:

```
PROTOTYPE WEBSITE
=================

The Best Prototype Website Ever
```

![edit on git](../images/editOnGit.png)

Add a commit message and then click on `Commit changes`

Now if you go back to the command line and run 
```
$ git pull origin master
```
If you open up/refresh the `README.md you should now see the changes you made on Github. Neat!

Time Travelling
--------------

So far we have added our code, pushed, made some further changes and then pulled those changes back down from Github.

What if we wanted to go back in time to the first time we made a commit? 

To see all the commits that have been made in the past use the command `$ git log`. You should see something similar to the following:

```
commit 743d0c7b48698192a367892aeb67f947937e4e81
Author: Andrew Werner <awerner1@googlemail.com>
Date:   Tue Mar 21 17:22:27 2017 +0000

    Updated the readme

commit 094d3a55c05f25623d4f7d3db570e7070bf09d32
Author: Andrew <awerner1@googlemail.com>
Date:   Mon Mar 20 16:39:52 2017 +0000

    My First Commit
```

Now for the exciting part. Copy the commit ID for your first commit and run the *checkout* command like so:

```
$ git checkout 094d3a55c05f25623d4f7d3db570e7070bf09d32
```

Look at your `README.md` now. You have just travelled back to the past. Now to get us back to the present:

```
$ git checkout master
```

You should now see that our changes to the `README.md` have been reinstated. We haven't lost any work and can continue to build our prototype website.

When and how to commit
---------------------

A good rule of thimb is **commit early, commit often**. Whenever you make a meaningful change, make a commit. You don't have to push it to Github straight away: you can make several commits and then push them in one go.

Make a commit when you've done a meaningful piece of work. Ideally, your commit log should document the developement of the project. For example:

 - Intial commit (added Readme file)
 - Added an empty web page
 - Put a welcome message on the page
 - Added a header with a logo
 - Added a footer with a few links
 - Added /contact-us page
 
and so on and so forth (in reality it'll be more detailed and technical. Read [the commit messages of the jQuery project](https://github.com/jquery/jquery/commits/master) to get an idea of what they look like in real life.

Now that we have all the basic of version control we can move ahead with building our prototype website.


