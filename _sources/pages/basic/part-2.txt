.. highlight:: console

Part 2
======

Copying Files
-------------

``cp`` (copy)
~~~~~~~~~~~~~

The command ``cp file1 file2`` will make a copy of ``file1`` in the
current working directory with the name ``file2``.

What we are going to do now is download a file from the internet, save it to our
``unix_tutorial`` directory and then use the ``cp`` command to copy that file to
our ``backups`` directory (which we created in :ref:`Exercise 1a
<exercise-1a>`).

First point your web browser to `this link (my_first_file.txt)
</UnixTutorial/_static/my_first_file.txt>`_ and save the file using "*Save
as..*" to your ``unix_tutorial`` directory.

.. todo::

    Put a link in here!!!

Now, ``cd`` to your ``unix_tutorial`` directory. ::

    % cd ~/unix_tutorial

Then at the Unix prompt, type::

    % cp my_first_file.txt my_first_file.bu

This command means copy the file ``my_first_file.txt`` to ``my_first_file.bu``.

.. warning::

    The ``cp`` command allows you to use already existing filenames as the
    target for the copy, hence it can be used to overwrite files!   



Moving files
------------

``mv`` (move)
~~~~~~~~~~~~~

The command ``mv file1 file2`` moves (or renames) ``file1`` to ``file2``.

To move a file from one place to another, use the ``mv`` command. This has
the effect of moving rather than copying the file, so you end up with
only one file rather than two.

It can also be used to rename a file, by moving the file to the same
directory, but giving it a different name.

We are now going to move the file ``my_first_file.bu`` to your backup directory.

First, change directories to your ``unix_tutorial`` directory (using the ``cd`` command). Then, inside the ``unix_tutorial`` directory, type::

    % mv my_first_file.bu backups/

Type ``ls`` and ``ls backups`` to see if it has worked.


Removing files and directories
------------------------------

``rm`` (remove), ``rmdir`` (remove directory)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

To delete (remove) a file, use the ``rm`` command. As an example, we are
going to create a copy of the ``my_first_file.txt`` file then delete it.

Inside your ``unix_tutorial`` directory, type::

    % cp my_first_file.txt tempfile.txt
    % ls

You should now see both ``my_first_file.txt`` and ``tempfile.txt`` listed.  Next type::

    % rm tempfile.txt
    % ls

and the file ``tempfile.txt`` should be gone!

You can use the ``rmdir`` command to remove an **empty** directory. Try to
remove the ``backups`` directory.  You will not be able to since Unix will not
let you remove a non-empty directory.


.. topic:: Exercise 2a

    Create a directory called ``Tempstuff`` using mkdir , then remove it
    using the rmdir command.


Displaying the contents of a file on the screen
-----------------------------------------------

``clear`` (clear screen)
~~~~~~~~~~~~~~~~~~~~~~~~

Before you start the next section, you may like to clear the terminal
window of the previous commands so the output of the following commands
can be clearly understood.

At the prompt, type::

    % clear

This will clear all text and leave you with the prompt at the top of the
window.

 

``cat`` (concatenate)
~~~~~~~~~~~~~~~~~~~~~

The command cat can be used to display the contents of a file on the
screen. Type::

    % cat my_first_file.txt

Unfortunately, the file is longer than than the size of the window, so it
scrolls past.  On many modern terminals we can just scroll up to see what we
have missed, however, on older systems this may not be possible!

 
``less``
~~~~~~~~

The command ``less`` writes the contents of a file onto the screen a page at a
time. Type::

    % less my_first_file.txt

Press the ``[space-bar]`` if you want to see another page, of press ``q`` if
you want to quit. Typically, ``less`` is a better option for reading a long
file than ``cat``.  Other useful keys in ``less`` include:

========== =========================
Key        Action
========== =========================
``g``      Return to top of file
``G``      Scroll to bottom of file
``[up]``   Scroll up one line
``[down]`` Scroll down one line
========== =========================


``head``
~~~~~~~~

The ``head`` command writes the first ten lines of a file to the screen.

First clear the screen then type::

    % head my_first_file.txt

Then type::

    % head -5 my_first_file.txt

What difference did the ``-5`` flag do to the head command?


``tail``
~~~~~~~~

The ``tail`` command writes the last ten lines of a file to the screen.

Clear the screen and type::

    % tail my_first_file.txt

.. topic:: Exercise 2b

    Try using the tail command to view the last 15 lines of ``my_first_file.txt``. 

 

Searching the contents of a file
------------------------------------

Simple searching using ``less``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Using ``less``, you can search though a text file for a keyword (or *pattern*).
For example, to search through ``my_first_file.txt`` for the word "science",
type::

    % less my_first_file.txt

then, still in less (i.e. don't press ``q`` to quit), type a forward slash (``/``)
followed by the word you want to search for. i.e. ::

    /science

As you can see, less finds and highlights the keyword. Type ``n`` to search for
the next occurrence of the word.

 

``grep`` (don't ask why it is called grep)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

``grep`` is one of many standard Unix utilities. It searches files for
specified words or patterns. First clear the screen, then type::

    % grep science my_first_file.txt

and ``grep`` will display each line containing the word "science"... *Or has it?*

Try::

    % grep Science my_first_file.txt

The ``grep`` command is case sensitive; it distinguishes between "Science" and
"science".

To ignore upper/lower case distinctions, use the ``-i`` option, i.e. ::

    % grep -i science my_first_file.txt

To search for a phrase or pattern, you must enclose it in single quotes
(`'`). For example to search for "black holes" ::

    % grep -i 'black holes' my_first_file.txt

Some other useful ``grep`` include:

======   ===============================================
Option   Result
======   ===============================================
``-n``   precede each matching line with the line number
``-v``   display those lines that do **not** match
``-c``   print only the total count of matched lines
======   ===============================================

Try some of them and see the different results. Don't forget, you can
use more than one option at a time, for example, the number of lines
without the words "science" or "Science" is::

    % grep -ivc science my_first_file.txt

 

``wc`` (word count)
~~~~~~~~~~~~~~~~~~~

A handy little utility is the ``wc`` command, short for word count. To do a
word count on ``my_first_file.txt``, type::

    % wc -w my_first_file.txt

To find out how many lines the file has, type::

    % wc -l my_first_file.txt


Summary of commands
--------------------

+-------------------------+------------------------------------------------+
| Command                 | Description                                    |
+=========================+================================================+
| ``cp file1 file2``      | copy ``file1`` and call it ``file2``           |
+-------------------------+------------------------------------------------+
| ``mv file1 file2``      | move or rename ``file1`` to ``file2``          |
+-------------------------+------------------------------------------------+
| ``rm file``             | remove a file                                  |
+-------------------------+------------------------------------------------+
| ``rmdir directory``     | remove a directory                             |
+-------------------------+------------------------------------------------+
| ``cat file``            | display a file                                 |
+-------------------------+------------------------------------------------+
| ``more file``           | display a file a page at a time                |
+-------------------------+------------------------------------------------+
| ``head file``           | display the first few lines of a file          |
+-------------------------+------------------------------------------------+
| ``tail file``           | display the last few lines of a file           |
+-------------------------+------------------------------------------------+
| ``grep 'keyword' file`` | search a file for keywords                     |
+-------------------------+------------------------------------------------+
| ``wc file``             | count number of lines/words/characters in file |
+-------------------------+------------------------------------------------+

