Task 2 - Getting your code to Git
================================

[:globe_with_meridians: Go to course navigation :globe_with_meridians:](./navigation.md)

Once you have added something like `I want to learn how to be more like [insert name] awesome developer that I know` to your readme and saved it then running 

``` 
$ git status
```

should show you that there are changes to your `README.md` file. Add this

```
$ git add README.md
```

and then commit it.

```
$ git commit -m "Updated the readme with my motivation to learn"
```

then push

```
$ git push -u origin master
```

by following these steps your code should now be up on Github.

:twisted_rightwards_arrows: You should now switch over and on the new driver's laptop pull down the changes by running:

```
$ git pull origin master
``` 

Double check: if you open `README.md` do you see the changes that are held on github? 

Congratulations you now have all the basics of version control.

![Good job](../images/goodJob.png)

Switching
---------

For the rest of this course whenever you see the :twisted_rightwards_arrows: you should add, commit and push your code so that your pair partner can pull down your changes and work away on their own laptop. 

:blue_book: Consider bookmarking this page for quick reference.

Otherwise if everything is good lets get building!

[:arrow_backward: Return to previous section](../courseSections/section6.md) | [Continue to Section 7 :arrow_forward:](../courseSections/section7.md)
