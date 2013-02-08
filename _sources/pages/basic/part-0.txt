.. highlight:: console

=============
What is Unix?
=============

Unix is an operating system.  Operating systems control the computer and are
responsible for opening files, dealing with the memory, allocating tasks to the
processor and creating the underlying interface between the user and the
machine. 

Unix is made up of three basic components: the kernel :ref:`kernel
<the_kernel>`, :ref:`shell <the_shell>` and the :ref:`files and processes
<files_and_processes>`.

.. _the_kernel:

----------
The Kernel
----------

The kernel is the underlying core of the computer and carries out all of the
basic tasks including:

- The allocation of hardware and resources
- File system access
- Network access
- Execution and management of other programs
- Management of output (display and sound)
- Management of input (keystrokes, mouse clicks etc.)


.. _the_shell:

----------
The Shell
----------

The shell, or command-line interpreter (CLI), is a program which provides the
user interface to the kernel.  The user can type commands into the shell which
are then executed.  Example commands include:

- Opening files
- Mounting external drives
- Starting programs

Commands can be run either in the foreground (the shell waits until their
completion before accepting new commands) or in the background (the user may
continue to issue new commands while the original one is still running).

There are a number of available Unix shells.  The most common and earliest is
the Bourne SHell (`sh`) and is found on almost every Unix system.  Others
include:

- The C SHell (`csh`) and associated TC SHell (`tcsh`)
- The Bourne Again SHell (`bash`) *- the default on Mac OS X*
- The Z SHell (`zsh <http://zsh.sourceforge.net/>`_) *- my favorite!*

.. warning::

    Most commands work identically on all shells, however, the syntax
    of configuration and batch scripts often varies which can make it difficult to
    change between different shell incarnations once you have set up one to your
    liking.


.. _files_and_processes:

-------------------
Files and Processes
-------------------

Everything in UNIX is either a file or a process.

A **process** is an executing program identified by a unique PID (process
identifier).

A **file** is a collection of data. They are created by users using text
editors, running compilers etc.

Examples of files include:

- a document (report, essay etc.)
- the text of a program written in some high-level programming language
- instructions comprehensible directly to the machine and incomprehensible to a casual user, for example, a collection of binary digits (an executable or binary file);
- a directory, containing information about its contents, which may be a mixture of other directories (subdirectories) and ordinary files.


