Tools, softwares
----------------

We will need a bunch of tools for the course. The easiest way to get
them all is to rely on a package manager.

### Mac users

[Install Homebrew](https://brew.sh/)

[Install Homebrew-cask](https://caskroom.github.io/)

### Windows users

[Install Chocolatey](https://chocolatey.org/)

### Linux
The package manager is built-in, you should know how to use it.

### Chrome
Chrome will be our default browser.

Using our packages managers (Win, Mac)

```
\# Windows
C:\\\> choco install googlechrome
\# Mac
brew cask install google-chrome
```
If you already have it, make sure you have the latest version.

<img src="task_images/image15.png" width="640" />

### Atom
Atom is an open-source text editor with many helpful plugins.
[https://atom.io/](https://atom.io/)

<img src="task_images/image12.png" width="640" />

```
\# Windows 
C:\\\> choco install atom
\# Mac 
brew cask install atom
```
I recommend to install the following ones (directly from the editor
under packages)
```
  atom-beautify, atom-ternjs, autoclose-html, pigments, advanced-open-file
```

Git and Github
--------------

Git is a free and open source distributed version control system
designed to handle everything from small to very large projects with
speed and efficiency. It is similar to a Google Docs or Shared Dropbox
folder for your code (and your peers).

You will use it extensively for this course. So to get started, the
first steps are:

1.  [Creating a Github account](https://github.com/join)
    (if you don\'t have one)

2.  Installing Git and Git desktop
```
\# Windows
C:\\\> choco install github
\# Mac
brew install git
brew cask install github-desktop
```
3.  Follow 2 tutorials on how to use Git

    a.  [https://try.github.io/levels/1/challenges/1](https://try.github.io/levels/1/challenges/1)

    b.  [http://learngitbranching.js.org/](http://learngitbranching.js.org/)

### A good-looking terminal

If you want to have a good looking terminal (instead of the default ugly one), I suggest you install ConsoleZ on Windows and Oh-my-zsh on mac.

Mac users: [read this tutorial](https://medium.com/@mrkdsgn/install-zsh-and-oh-my-zsh-on-osx-10-11-el-capitan-cfaa0ebb97dc)

Windows users:
```
C:\\\> choco install ConsoleZ
```
[https://github.com/cbucher/console](https://github.com/cbucher/console)

You can now create a \"labs\" folder that you will push on your Github
account. All the code for your labs can go in this folder.