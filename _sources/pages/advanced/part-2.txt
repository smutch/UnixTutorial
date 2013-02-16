.. highlight:: console

Part 2
======

Other useful Unix commands  
----------------------------

df
~~

The ``df`` command reports on the space left on the file system. For
example, to find out how much space is left on the disk your current
directory is on, type::

    % df .

To get the results in "human-readable" format, use the ``-h`` option::

    % df -h .

du
~~

The ``du`` command outputs the number of kilobyes used by each subdirectory.
Useful if you have gone over quota and you want to find out which
directory has the most files. In your home-directory, type::

    % du

Again, to get the results in "human-readable" format, use the ``-h`` option::

    % du -h

compressing files
~~~~~~~~~~~~~~~~~

This reduces the size of a file, thus freeing valuable disk space. For
example, type::

    % ls -l science.txt

and note the size of the file. Then to compress **science.txt**, type::

    % compress science.txt

This will compress the file and place it in a file called ``science.txt.Z``.

To see the change in size, type ``ls -l`` again.

To uncompress the file, use the ``uncompress`` command. ::

    % uncompress science.txt.Z

A better method of compression is to use ``gzip``.  This also compresses a file, 
but is more efficient than compress. For example, to zip **science.txt**, type::

    % gzip science.txt

This will zip the file and place it in a file called **science.txt.gz**.

To unzip the file, use the ``gunzip`` command. ::

    % gunzip science.txt.gz

Lastly, you can package a group of files together using ``tar``.  Try this by
making a few files::

    % man gcc > gcc.txt
    % man tar > tar.txt
    % man man > man.txt

and package them together using ``tar``::

    % tar cf man_pages.tar *.txt

You can look at the contents of your tar file using::

    % tar tf man_pages.tar

You can also have ``tar`` compress the result on the fly for you::

    % tar cfz man_pages.tgz *.txt

Compare the sizes of the two resulting files using ``ls -l``.

file
~~~~

``file`` classifies the named files according to the type of data they
contain, for example ascii (text), pictures, compressed data, etc.. To
report on all files in your home directory, type::

    % file ~/*

history
~~~~~~~

The shell keeps an ordered list of all the commands that you have
entered. Each command is given a number according to the order it was
entered.  To show this list type::

    % history

If you are using the C shell, you can use the exclamation character (``!``)
to recall commands easily::

    % !! (recall last command)

    % !-3 (recall third most recent command)

    % !5 (recall 5th command in list)

    % !grep (recall last command starting with grep)

You can increase the size of the history buffer by typing::

    % set history=100


