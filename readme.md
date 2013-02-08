Unix Tutorial
=============

This is the source code.  To see the actual tutorial point your browser [HERE](http://smutch.github.com/UnixTutorial).

Working with the source
-----------------------

To work with the source you must have Python and Sphinx installed.

First clone the master branch of this repo:

```console
git clone git@github.com:smutch/UnixTutorial.git
```

Then re-clone the gh-pages branch of the repo into the directory build\_html:

```console
cd UnixTutorial
git clone -b gh-pages git@github.com:smutch/UnixTutorial.git build_html
```

After that you should be good to go.  Build the site with `make html` and clean with `make clean`.


Using the `chrome_watcher.rb` script
------------------------------------

This script is courtesy of [this article](http://brettterpstra.com/2011/03/07/watch-for-file-changes-and-refresh-your-browser-automatically/) by Brett Terpstra.  It's **very** useful when developing the source.  Try out the following in the `build_html` directory:

```console
python -m SimpleHTTPServer 8020 &
open -a Google\ Chrome http://localhost:8020/index.html
cd ..
ruby chrome_watcher.rb build_html/pages 'localhost:8020'
```

Then every time you run `make html` in source root directory, Google Chrome will automatically refresh! (Unless you have only changed `index.rst`, then you will need to manually refresh...)

