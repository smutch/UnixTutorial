.. highlight:: console

Part 3
=======

Redirection  
-------------

Most processes initiated by Unix commands write to the standard output
(that is, they write to the terminal screen), and many take their input
from the standard input (that is, they read it from the keyboard). There
is also the standard error, where processes write their error messages,
which is by default again the terminal screen.

We have already seen one use of the ``cat`` command to write the contents of a
file to the screen.

Now type ``cat`` without specifying a file to read from standard input: ::

    % cat

Then type a few words on the keyboard and press the ``Return`` key.

Finally hold the ``Ctrl`` key down and press ``d`` (written as ``^D``
for short) to end the input.

What has happened?

If you run the cat command without specifying a file to read, it reads
the standard input (the keyboard), and on receiving the 'end of file'
(``^D``), copies it to the standard output (the screen).

In Unix, we can redirect both the input and the output of commands.


Redirecting the Output  
------------------------

We use the ``>`` symbol to redirect the output of a command. For example, to
create a file called ``list1.txt`` containing a list of fruit, type: ::

    % cat > list1.txt

Then type in the names of some fruit. Press ``Return`` after each one. ::

    pear
    banana
    apple
    
To stop press ``^D`` (control D).

What happens is the cat command reads the standard input (the keyboard)
and the ``>`` redirects the output, which normally goes to the screen, into
a file called ``list1.txt``.

To read the contents of the file, type: ::

    % cat list1.txt

.. topic:: Exercise 3a

    Using the above method, create another file called ``list2.txt`` containing
    the following fruit: orange, plum, mango, grapefruit. Read the contents
    of ``list2.txt``.

The form ``>>`` appends standard output to a file. So to add more items to
the file ``list1.txt``, type: ::

    % cat >> list1.txt

Then type in the names of more fruit: ::

    peach
    grape
    orange

and then ``^D`` (control D) to stop.

To read the contents of the file, type: ::

    % cat list1.txt

You should now have two files. One contains six fruit, the other
contains four fruit. We will now use the cat command to join
(concatenate) ``list1.txt`` and ``list2.txt`` into a new file called
``biglist.txt``. Type: ::

    % cat list1.txt list2.txt > biglist.txt

What this is doing is reading the contents of ``list1.txt`` and ``list2.txt`` in
turn, then outputting the text to the file ``biglist.txt``.

To read the contents of the new file, type: ::

    % cat biglist.txt

Piping the output of a command to a file can be extremely useful.  For example,
imagine that we are running a large script which carries out some complex
manipulation of our data and takes a long time to complete.  Typically we would
setup our script so that it prints out status messages telling us that certain
tasks have been completed or certain files have been read/written.  By piping
the output of our script to a file we can record these log messages for future
reference or for situations where we may want to leave the script running after
we have logged out (and hence there will be no standard output).


Redirecting the Input  
-----------------------

We use the ``<`` symbol to redirect the input of a command.

The command sort alphabetically or numerically sorts a list. Type: ::

    % sort

Then type in the names of some vegetables. Press ``Return`` after each
one. ::

    carrot
    beetroot
    artichoke
    ^D

The output will be: ::

    artichoke
    beetroot
    carrot

Using ``<`` you can redirect the input to come from a file rather than the
keyboard. For example, to sort the list of fruit, type: ::

    % sort < biglist.txt

and the sorted list will be output to the screen.

To output the sorted list to a file, type: ::

    % sort < biglist.txt > sorted_list.txt

Use cat to read the contents of the file ``sorted_list.txt``.


Pipes
-----

To see who is on the system with you, type: ::

    % who

One method to get a sorted list of names is to type: ::

    % who > names.txt
    % sort < names.txt

This is a bit slow and you have to remember to remove the temporary file
called names when you have finished. What you really want to do is
connect the output of the who command directly to the input of the sort
command. This is exactly what pipes do. The symbol for a pipe is the
vertical bar (``|``).  Pipes are one of the most useful features of Unix...

For example, typing: ::

    % who | sort

will give the same result as above, but quicker and cleaner.

To find out how many users are logged on, type: ::

    % who | wc -l

Pipes can be used to string together multiple commands, making them extremely powerful.  For example, in order to find out out many **other** users (i.e. excluding ourselves) are logged onto the system we could use the following: ::

    % who | grep -v [username] | wc -l

where ``[username]`` should be replaced by your own user name.

What we have done here is run the ``who`` to find out who is logged into the system.  The output has then been piped to the command ``grep`` which has **removed** (as a result of the ``-v`` flag) all lines containing our username.  Finally, this output has been piped to ``wc`` which has counted the number of lines.

.. topic:: Exercise 3b

    Create a file called ``current_users.txt``, that holds a **sorted** list of
    all *other* users (i.e. excluding yourself) that are currently logged in to
    the system.


Summary of commands
--------------------

+-------------------------------+----------------------------------------------------------------+
| ``command > file``            | redirect standard output to a file                             |
+-------------------------------+----------------------------------------------------------------+
| ``command >> file``           | append standard output to a file                               |
+-------------------------------+----------------------------------------------------------------+
| ``command < file``            | redirect standard input from a file                            |
+-------------------------------+----------------------------------------------------------------+
| ``command1 | command2``       | pipe the output of ``command1`` to the input of ``command2``   |
+-------------------------------+----------------------------------------------------------------+
| ``cat file1 file2 > file0``   | concatenate ``file1`` and ``file2`` to ``file0``               |
+-------------------------------+----------------------------------------------------------------+
| ``sort``                      | sort data                                                      |
+-------------------------------+----------------------------------------------------------------+
| ``who``                       | list users currently logged in                                 |
+-------------------------------+----------------------------------------------------------------+

