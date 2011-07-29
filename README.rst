======
README
======

Catchy Slogan
=============

GNU Screen + a little sugar =  Scrugar

Overview
========

This project consists of the following:

* Functions and aliases that make it easier to manage Screen sessions
* A set of Screen "profile" files

99% of the Screen users that I know have one file for setting Screen
preferences, ``~/.screenrc``. For me though, this didn't work because I
like to have different groups of terminal sessions available for different
types of tasks. 

For example, if I'm troubleshooting a web server problem, I may want to have a
``htop``, ``vim``, and ``mutt`` sessions available. If I'm working on a Rails
application, then I would want to have ``vim``, ``irb``, ``mongrel``,
``logtail``, and ``git`` windows open. Being able to segregate these terminal
sessions into different groups makes my workspace less cluttered, which makes
it easier for me to focus on my tasks.

Screen supports this type of usage, but you just need a few little functions
to make things easy to manage. And that's what this is.

Setup
=====

:: 

    # Install GNU Screen using apt-get or whatever.
    $ cd $HOME
    $ git clone http://github.com/tompurl/scrugar.git
    $ echo "source $HOME/scrugar/aliases" >> ~/.bashrc
    $ echo "source $HOME/scrugar/functions" >> ~/.bashrc
    $ source .bashrc # <= First time only

Examples
========

--------------------------
Attaching To A New Session
--------------------------

Let's say that you just started your computer and opened a terminal, and you 
would like to start working on a Ruby script. Let's also assume that you 
already have a profile file under ``~/scrugar/`` called **rails-foo**. You would
start this "session" by typing the following command::

    $ sa rails-foo

This command does two things:

* Opens a Screen session using the ``~/scrugar/rails-foo`` profile
* Assigns the title **rails-foo** to the session.

You should now be in your Screen session that is specified in your **rails-foo**
project. You can navigate between windows by pressing ``Ctrl-A "`` and then using
the ``j`` and ``k`` buttons to move up and down. You can leave the Screen session by
pressing ``Ctrl-A d``. These are both standard Screen keyboard commands.

-----------------------------------
Re-Attaching To An Existing Session
-----------------------------------

Now let's say that you want to check your system mail using ``mutt``. You know
that you have a Screen profile called **localhost** that has a ``mutt`` window,
so you decide to open it. 

First, if you're still "in" the rails-foo Screen session, simply press the
``Ctrl-A d`` keyboard combination to leave it. Don't worry about losing any of
your terminal windows in this session, because you're not "closing" the Screen
session. You're just detaching from it, and you can come back and re-attach
later. This is actually probably the best feature of Screen.  It allows you to
detach from sessions and come back later.

Now, before you open a *new* Screen session using the **localhost** profile,
let's see if you are already have one running. Usually, it doesn't make sense
to open multiple Screen sessions using the same profile because it's confusing
and wastes resources. So let's see which Screen sessions are already running
on your machine::

    $ sls
    There are screens on:
            4431.rails-foo      (07/28/2011 04:19:37 PM)        (Detached)
            3374.localhost      (07/28/2011 04:01:16 PM)        (Detached)
    2 Sockets in /var/run/screen/S-tom.

What do you know? I already had a **localhost** session running. So let's
reattach to that::

    $ sr localhost

Ta-da! I'm now back in my old **locahost** Screen session. 

-----------------
Closing A Session
-----------------

Now let's say that you would like to close your **rails-foo** session. Maybe
you're done with it for now. Maybe your wrecked it and would like to start
over.  Either way, you basically have two choices:

#. Go into each terminal window in your Screen session and ``exit`` it manually.
#. Leave your Screen session and then type ``sk rails-foo``.

Please note that option 2 executes a ``kill -9`` on the Screen process that is
the parent of the terminal windows in your session. The ``-9`` switch does
**not** shut processes down gracefully, so you should only use the ``sk`` alias
if you closed all of the files and shut down all of the processes in the child
terminal windows.

Commands
========

TODO
