Section 1 - Creating a Development Environment
=============================================

Developers generally work closer to the bare bones of the computer than your average user. That means lots of time in the 'command line' and not relying on 'GUI' (Graphical User Interface) tools. However, to get your computer setup for web development is an are in and of itself - especially on Windows.

Fortunately, there are a number of cloud based development environments available that provide almost identical experience but with everything ready for you out of the box. For this course we will be using [Cloud9](https://c9.io/).


1. [Create a free Cloud9 account](https://c9.io/signup)
2. Choose `Create a new workspace`
3. Call your workspace `prototype-website`
4. Choose a Hosted workspace and make it Pubic
5. Choose `Blank` as a template
6. Create the workspace (This may take a minute or two)

![Cloud9 setup](../images/c9Setup.png)

When your workspace has been created you should see it open in your browser. It will look something like this:

![Cloud9 Initial Page](../images/c9InitialReadme.png)

What you are seeing in this image is an **Integrated Development Environment (IDE)**. IDEs are highly complex applications and take a bit of getting used to. Think Microsoft Word, on steroids, exposed to radiation in a secret nuclear incident and having gained super powers...something like that. Regardless, the important thing is that Cloud9 gives us the four critical components of our developement environment:

 - A **file system** to store our source files (code, images, HTML, CSS and others)
 - An **editor** to edit the above mentioned source files
 - An **operating system** to run the program described by these files
 - Finally, a **command line** or **terminal** to send instructions to the operating system

 Updating the README
----------------------------

You'll notice that a single file has been created for you already - `README.md`. It's a convention of all good projects to have a README file that explains what the project is for and provides information about how to install and run the program.

If you double click the file in the tree view, it will open for editing in the main pane. The file has a `.md` extension, which means it is intended to be written in **Markdown** a popular syntax for lightly styling text files. Markdown is ubiquitous on **Github** [and here is a useful guide to it](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet) For now though, let's just create a basic placeholder for information. 

Delete the contents of the file and replace them with the following:

```
Prototype Website
=================

Built by [Your names here]
```

Makre sure you save the file. Switch to the preview tab: has it been updated with your new content?

Introducing Ruby
---------------


