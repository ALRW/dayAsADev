Github
=======

![octocat](../images/octocat.png)

Making all of these changes on your local computer is great, but we'll need osme additional funcitonality provided by [Github](https://github.com/) to collaborate with other developers.

Github does three things. Firstly it displays git repos in a visual way, so you ccan look at them online. Seconldy, it serves as a common place for open source projects, so if you're using some open source library, the chagnes are you can find it on Github. Finally, Github provides a set of tools (forking, issues, etc) to help developers collaborate on projects. If you'd like to see an example Github project, checkout [Bootstrap](https://github.com/twbs/bootstrap). We'll be incorporating this into our project later.

Github is Distributed 
--------------------
Github is really just another computer somehwere in the USA that you can create a repository on. When (as we will do in a minute) you got to Github and create a new repository, Github does `git init` on its local computer.

So Github's web interface is nothing more than a visual interface to git installed on Github's server.

The key feature of git when used in conjunction with Github is the ability to copy code between repositories. If you have a local repository (on your own laptop) and remote repository (on Github), you can copy code in either direction. Crucially you can also move code using git between developers' laptops, even directly if you wish.

Using Github
------------

If you haven't already then signup for a [free Github account](https://github.com/join)

Once you are signed up and signed in click on the green new repository button:

![New repo](../images/newRepo.png)

Enter `prototype-website` into the *Respository name* field, add an optional description and make it public so that others can see it. Don't initialise it with a README. Then when you're happy create the repository:

![Create repository](../images/repoSetup)

You should see the following:

![Empty repo](../images/emptyRepo)

This means that you have a remote repository but it's empty. Github also shows us the steps required for a new repository and for an existing one. Since we already have a reposiroty setup for our application in Cloud9 we only have two steps to do.

The first one is to connect our two repositories together. Right now you have two git repostiories: one on Cloud9 and one on girhub but they don't know of each other. So, we need to connect them first.

Connecting two repositories is done by creating something called a *remote*. This is simply a record in a local repository that it's linked ot another one. Let's take a look at the current list of the remotes for your local git repo. Run the following in the command line:

```
$ git remote -v
```

> What did you get? What do you think this means?

Hopefully, you were thinking that the lack of output means that your local git repo has no associated remotes. Now lets follow the advice that git gave us and set one up:

```
$ git remote add origin git@github.com:[Your username]/prototype-website.git
```

Now if you try `$ git remote -v` again you should see something similar to this:

![added remote](../images/addedRemote.png)

What is origin? Honestly, you can replace origin with anything that you want it's just a conventional name but if you're using one repository to store code remotely (i.e. on github) and you're coordinating the work of a team then it's convention among developers to call that repository origin.

Awesome! Now your local repository knows that it's *linked* to another respoitory somewhere on github.com. Note that no real connection is establishe yet. You could have added a remote while being offline. To actually move the code we have committed locally to the repo on Github (called origin) we need to use the `git push` command. 

Security
--------

Before we do this we need to ensure that we can move our code securely between github and Cloud9, unfortunately this required a little bit of configuration.

On your Cloud9 home-page click on the settings icon and then onto SSH keys. Then copy the contents of the grey box.

![Cloud 9 SSH](../images/cloud9SSH.png)

Then on Github go Click on your account in the top right hand corner and then settings:

![github settings](../images/githubSettings.png)

Once here click on `SSH and GPG keys` then `New SSH key` call the key "Cloud9" and then paste the key into the text area labelled "Key". Finally click `Add SSH key`. 

![github ssh](../images/githubSSH.png)

Congratulations, we can now move on to pushing code securely between our repositories

Pushing your code
---------------

Back in Cloud 9 go to the command line and run the following:

```
$ git push -u origin master
```

You should see some output:

```
Warning: Permanently added 'github.com,192.30.253.112' (RSA) to the list of known hosts.
Counting objects: 6, done.
Delta compression using up to 8 threads.
Compressing objects: 100% (4/4), done.
Writing objects: 100% (6/6), 862 bytes | 0 bytes/s, done.
Total 6 (delta 0), reused 0 (delta 0)
To github.com:ALRW/prototype-website.git
 * [new branch]      master -> master
 ```

 This means that the push went well. Lets just quickly break down the command. It tells git to push code from your local repository (it's implied) to a repository called origin (that's the name of the remote we've just added). The last bit, "master", measn that we're pushing the branch called "master" (the only branch we have right now). We haven't discussed branches yet, so don't worry about it. The "-u" switch means that these parameters should be saved as default, so next time you won't have to type "origin master". You'll be able to simply do:

 ```
 $ git push
 ```

 Try it now. Git will tell you that everything is up to date. This means that there are no local changes that haven't been pushed yet to Github.

 Ok, now let's flick over to Github itself. Refresh the page....What do you see?

 Hopefully, you should see all your code held on github with your readme displayed. Compare it to your local version, each of the files should contain exactly the same content.

 So now you have two repositories, one locally and one on Github, that have the same commits. Now even if you do loose your laptop you'll at least be able to get your code from Github.

Pulling the code from Github
---------------------------

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


