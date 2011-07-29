======
README
======

GNU Screen + a little sugar =  Scrugar

Overview
========

This folder consists of the following:

* Functions and aliases that make it easier to manage screen sessions
* A set of Screen "profile" files

99% of the screen users that I know have one file for setting Screen
preferences, `~/.screenrc`. For me though, this didn't work because I like
to have different terminal sessions available for different types of tasks. 

For example, if I'm troublshooting a web server problem, I may want to have a
*tail*, *vim*, and *mutt* sessions available. If I'm working on a Rails
application, then I would want to have *vim*, *exec*, *mongrel*, *logtail*, and
*git* windows open. Being able to segregate these groups of sessions makes my
workspace less cluttered, which makes it easier for me to focus on my tasks.

Screen supports this type of usage, but you just need a few little functions
to make things easy to manage. And that's what this is.

Setup
=====

:: 

    # Install GNU Screen
    $ cd $HOME
    $ git clone http://github.com/tompurl/scrugar.git
    $ echo "source $HOME/scrugar/aliases" >> ~/.bashrc
    $ echo "source $HOME/scrugar/functions" >> ~/.bashrc
    $ source .bashrc # <= First time only

Example
=======

Let's say that you just started your computer and opened a terminal, and you 
would like to start working on a Ruby script. Let's also assume that you 
already have a profile file under ~/scrugar/ called "rails-foo". You would
start this "session" by typing the following command:

    sa rails-foo

This command does two things:

* Opens a Screen session using the `~/scrugar/rails-foo` profile
* Assigns the title *rails-foo* to the session.

You should now be in your Screen session that is specifici to your *rails-foo*
project. You can navigate between windows by pressing `Ctrl-A "` and then using
the `j` and `k` buttons to move up and down. You can exit the Screen session by
pressing `Ctrl-A d`. These are both standard Screen keyboard commands.

Now let's say that you want to check your system mail using `mutt`. You know
that you have a Screen profile called *localhost* that has a `mutt` window,
so you decide to open it. 

First, if you are already in another screen session, presskk


