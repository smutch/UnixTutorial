.. highlight:: console

Part 3
======

Simple calculations in Unix using awk  
-------------------------------------

``awk`` is a powerful Unix command useful for performing line-by-line operations on ascii files (eg. tables of data).  It can be used in two modes: command-line-mode and as a scripting language.  To get an idea of how it works, let's look at the command-line usage first.  Later we will create some simple ``awk`` scripts.

``awk`` on the command line
~~~~~~~~~~~~~~~~~~~~~~~~~~~

The general format of a call to ``awk`` is as follows: ::

    % awk 'PROGRAM' file

Where ``PROGRAM`` denotes what will be executed on each line and ``file`` is the file to be operated-on in a line-by-line fashion.  The simplest program just prints the contents of the file: ::

    % awk 'print' file

``awk`` parses each line into a series of columns.  Each column is referred to as ``$1``, ``$2``, ``$3``, etc.  The entire line is specified as ``$0``.  So, another way to print the whole file is: ::

    % awk 'print $0' file

If you want to just print the first and 3rd columns though, you can do that with: ::

    % awk 'print $1,$3' file

The real power of ``awk`` emerges when you start using it's pattern-matching and column operation functionality.  For instance, assume you want to find all the files in your how directory owned by user ``user_name``.  You could run: ::

    % ls -l | awk '/user_name/ {print $9}'

Here, ``/user_name/`` is a match filter.  For every line that contains the text between the ``/``'s, the code between the ``{}``'s will be executed.  You can have more than one match filter: ::

    % man ls | awk '/-A/ {print $0} /-f/ {print $0}'

Working with our sample data files, say we want to find all the galaxies marked as QSOs in the first file: ::

    % awk '/QSO/ {print $0}' data_file_1.txt

Perhaps we want to keep the header information at the top: ::

    % awk '/#/ {print $0} /QSO/ {print $0}' data_file_1.txt

``awk`` allows for code to be executed before-and-after the line-by-line processing: ::

    % awk 'BEGIN {print "# Below is a list of QSOs"} /#/ {print $0} /QSO/ {print $0} END{print "# Above is a list of QSOs"}' data_file_1.txt

``awk`` can operate on multiple files: ::

    % awk 'BEGIN {print "# Below is a list of QSOs"} /#/ {print $0} /QSO/ {print $0} END{print "# Above is a list of QSOs"}' data_file_1.txt data_file_2.txt

Now, what if we only want the first header line?  Let's stretch ``awk``'s abilities a bit more: ::

    % awk 'BEGIN {print "# Below is a list of QSOs";i=0} /#/ {i=i+1;if(i==1) print $0} /QSO/ {print $0} END{print "# Above is a list of QSOs"}' data_file_1.txt data_file_2.txt
 
Let's make a list of all the R-band magnitudes in the first file: ::

    % awk 'BEGIN {print "# Below is a list of galaxies";i=0} /#/ {i=i+1;if(i==4) print "# "$6} ! /#/{print $9}' data_file_1.txt

Suppose there's a calibration error and we want to remove 0.01 from all magnitudes less than 21.  ``awk`` allows us to perform conditionals and mathematical expressions: ::

    % awk 'BEGIN {print "# Below is a list of galaxies";i=0} /#/ {i=i+1;if(i==4) print "# "$6} ! /#/{if($9<21.) print $9-0.01; else print $9}' data_file_1.txt

``awk`` as a scripting language
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

``awk`` can be used as a scripting language much like a shell script.  Start the script with a line declaring that the file will run ``awk`` in **filter** mode.  Turning our last example into a script you would have: ::

    #!/usr/bin/awk -f
    BEGIN {
        print "# Below is a list of galaxies";
        i=0
    } 

    /#/ {
        i=i+1;
        if(i==4) print "# "$6
    } 

    ! /#/{
        if($9<21.) print $9-0.01; 
        else       print $9
    }

Experiment with ``awk`` it has a lot more functionality than what is shown here and there are many good tutorials online.


