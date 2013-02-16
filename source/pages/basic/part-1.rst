.. highlight:: console

Part 1
=======

Listing files and directories
-----------------------------

``ls`` (list)
~~~~~~~~~~~~~

When you first login, your current working directory is your home directory.
Your home directory typically has the same name as your user-name and it is
where your personal files and subdirectories are saved.

To find out what is in your home directory, type::
    
    % ls

The ``ls`` (short for list) command lists the contents of your current working
directory.

There may be no files visible in your home directory, in which case, the Unix
prompt will be returned. Alternatively, there may already be some files created
by the operating system or your System Administrator when your account was
created.

``ls`` does not, in fact, cause all the files in your home directory to be
listed, but only those ones whose name does not begin with a dot (``.``)
Files beginning with a dot (``.``) are known as *hidden* files and usually
contain important program configuration information. They are hidden
because you should generally not change them unless you are familiar with
Unix.

To list all files in your home directory including those whose names
begin with a dot, type::

    % ls -a

``ls`` is an example of a command which can take *flags*: ``-a`` is an example.
Flags change the behaviour of a command. There are manual pages that tell you
which flags a particular command can take, and how each one modifies the
behaviour of the command (see the :ref:`getting help <getting-help>` section).

.. todo::

    Add a link to the section that talks about ``man``.


Making Directories
------------------

``mkdir`` (make directory)
~~~~~~~~~~~~~~~~~~~~~~~~~~

We will now make a subdirectory in your home directory to hold the files
you will be creating and using during the course of this tutorial. To make a
subdirectory called "unix_tutorial" in your current working directory type::

    % mkdir unix_tutorial

Here ``unix_tutorial`` is an *argument* to the ``mkdir`` command.  Some
commands, such as ``mkdir`` require an argument at all times (in this case, the
name of the directory we want to create).  Other commands, such as ``ls`` can
take arguments, but do not necessarily require them.

To see the directory you have just created, type::

    % ls

Notice the lack of an argument for the ``ls`` command here.  This means
"list the contents of my current working directory".  If were to instead type::

    % ls unix_tutorial

we would be presented with the contents of our newly created directory (which
is currently empty though!).


Changing to a different directory 
----------------------------------

``cd`` (change directory)
~~~~~~~~~~~~~~~~~~~~~~~~~

The command ``cd`` changes the current working directory to another one you
specify. The current working directory is the directory you are currently in -
your current position in the file-system tree.

To change to the directory you have just made, type::

    % cd unix_tutorial

Type ``ls`` to see the contents (which should be empty).


.. _exercise-1a:

.. topic:: Exercise 1a

    Make another directory inside the ``unix_tutorial`` directory called
    ``backups``.


The directories ``.`` and ``..``
--------------------------------

Still in the ``unix_tutorial`` directory, type::

    % ls -a

As you can see, in the ``unix_tutorial`` directory (and in all other
directories), there are two special directories called ``.`` and
``..``

In UNIX, ``.`` means the current directory, so typing::

    % cd .

means stay where you are (the ``unix_tutorial`` directory).

.. note:: 

    The space between ``cd`` and the dot is necessary.  ``cd`` is the command
    and ``.`` an argument which we are passing to ``cd``.

This may not seem very useful at first, but using ``.`` as the name of
the current directory will save a lot of typing, as we shall see later
in the tutorial.

 
``..`` means the parent of the current directory, so typing::

    % cd ..

will take you one directory up the hierarchy (back to your home
directory). Try it now.

.. tip:: 

    Typing cd with no argument always returns you to your home
    directory. This is very useful if you are lost in the file system.


Pathnames
---------

``pwd`` (print working directory)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Pathnames enable you to work out where you are in relation to the whole
file-system. For example, to find out the absolute pathname of your
home-directory, type ``cd`` to get back to your home-directory and then
type::

    % pwd

The full pathname **may** look something like this::

    /Users/myname

which means that ``myname`` (your home directory) is in the directory ``Users``,
which itself is located at the root of file-system.


.. topic:: Exercise 1b

    Use the commands ``ls``, ``pwd`` and ``cd`` to explore the file system.

    (Remember, if you get lost, type ``cd`` by itself to return to your
    home-directory)


More about home directories and pathnames
-----------------------------------------

Understanding pathnames
~~~~~~~~~~~~~~~~~~~~~~~

First type ``cd`` to get back to your home-directory, then type::

    % ls unix_tutorial

to list the contents of your ``unix_tutorial`` directory.
 

Now type::

    % ls backups

You will get a message like this::

    backups: No such file or directory

The reason is, ``backups`` is not in your current working directory. To
use a command on a file (or directory) not in the current working
directory (the directory you are currently in), you must either ``cd`` to
the correct directory, or specify its full pathname. Therefore, to list the
contents of your backups directory, you must type::

    % ls unix_tutorial/backups

 

``~`` (your home directory)
~~~~~~~~~~~~~~~~~~~~~~~~~~~

Home directories can also be referred to by the tilde (``~``) character.
It can be used to specify paths starting at your home directory. So
typing::

    % ls ~/unix_tutorial

will list the contents of your ``unix_tutorial`` directory, no matter where you
currently are in the file system.


Summary of commands
-------------------

+------------------+---------------------------------------------------+
| Command          | Description                                       |
+==================+===================================================+
| ``ls``           | list files and directories                        |
+------------------+---------------------------------------------------+
| ``ls -a``        | list all files and directories (including hidden) |
+------------------+---------------------------------------------------+
| ``mkdir``        | make a directory                                  |
+------------------+---------------------------------------------------+
| ``cd directory`` | change to named directory                         |
+------------------+---------------------------------------------------+
| ``cd``           | change to home-directory                          |
+------------------+---------------------------------------------------+
| ``cd ~``         | change to home-directory                          |
+------------------+---------------------------------------------------+
| ``cd ..``        | change to parent directory of current location    |
+------------------+---------------------------------------------------+
| ``pwd``          | display the full path of the current directory    |
+------------------+---------------------------------------------------+

