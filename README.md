The AllegroServe Webserver
====================================================

(Portable Fork for use with ZACL, system name is "zaserve")


Table of contents
-----------------

   * Description
   * Author
   * Author comments
   * Portability comments
   * Documentation
   * Platforms
   * Dependencies
   * Installation
   * Configuration
   * Licence
   * Notes
   * Examples
   * Open Source 

Description
-----------

AllegroServe has these components:

 * HTTP/1.1 compliant web server capable of serving static and dynamic pages
 * HTML generation facility that seamlessly merges html tag printing with 
   computation of dynamic content. The HTML generator matches perfectly 
   with the HTML parser (which is in another project) to allow web 
   pages to be read, modifed in Lisp and then regenerated.
 * HTTP client functions to access web sites and retrieve data.
 * Secure Socket Layer (SSL) for both the server and client.
 * Web Proxy facility with a local cache.
 * Comprehensive regression test suite that verifies the functionality 
   of the client, server, proxy and SSL
 * high performance for static and dynamic web page delivery
 * Licensed under terms that ensure that it will always be open source 
   and that encourages its use in commercial settings.
 * A publish function that builds a page from static and 
   dynamic data and handles caching of the result.
 * Access control mechanisms for publishing directories that 
   gives the webmaster the ability to specify which files and 
   directories in the tree should be visible.
 * The ability to run external CGI programs.
 * An improved virtual hosting system that supports different 
   logging and error streams for each virtual host.

We've recently added these features:

 * The ability to compress and inflate files on the fly.
 * Support for chunking and http/1.1
 * Security up through TLS 1.0 (SSL 3.1).

See [the latest Allegro CL Release
Notes](https://franz.com/support/documentation/current/doc/release-notes.htm)
for more information on AllegroServe changes.

Author
------

John Foderaro, Franz Inc.

Author comments
---------------

The server part of AllegroServe can be used either as a standalone web
server or a module loaded into an application to provide a user
interface to the application. AllegroServe's proxy ability allows it
to run on the gateway machine between a company's internal network and
the internet.  AllegroServe's client functions allow Lisp programs to
explore the web.

AllegroServe was also written and open sourced as a way to demonstrate
network programming in Allegro Common Lisp.  AllegroServe was written 
according to a certain coding standard to demonstrate how Lisp programs 
are more readable if certain macros and special forms are avoided.


Portability Comments
--------------------

Although AllegroServe was originally written with portability (to
other CL implementations) as "neither a goal nor a non-goal"
(according to author John Foderaro), it is a testament to the
cleanliness of the AllegroServe codebase, as well as the flexibility
of Common Lisp, and the power of the CL ANSI standard, that some ports
of AllegroServe have in fact been accomplished over the years.

This is the most recent one, and attempts to keep as close as possible
to the official AllegroServe code. It uses a compatibility layer
called ["ZACL"](https://gitlab.common-lisp.net/zbeane/zacl), available
in Quicklisp as `:zacl`.

With this said, please keep in mind that Allegro CL is AllegroServe's
native platform, and as such, AllegroServe will always work and
perform best on Allegro CL. Allegro CL also comes backed with expert
commerical support. So if you have mission-critical or
performance-critical applications, it will be to your advantage to
invest in Allegro CL for developing and running your AllegroServe
applications.


Platforms
---------

Zaserve works on all recent versions SBCL and CCL. Contributions of
[ZACL](https://gitlab.common-lisp.net/zbeane/zacl) ports to other
platforms are welcome.

Dependencies
------------

Zaserve depends on
[ZACL](https://gitlab.common-lisp.net/zbeane/zacl). This dependency is
taken care of for Quicklisp with the included `zaserve.asd` file.

In order to run the allegroserve test suite you'll need to have the
tester module (available at <https://github.com/franzinc>) loaded.

Installation
------------

### start lisp
    
    CL-USER> (ql:quickload :zaserve)

This will not load the example files. 

### start the server

    user(2):  (net.aserve:start :port 8000)

you can omit the port argument on Windows where any process can
allocate port 80 (as long as it's unused). 

### try out the server

go to a web browser and try http://your-machine-name:8000/.  If the 
web browser is on the same machine as AllegroServe is running you can 
use http://localhost:8000/ as well.  Now that you've verified that it 
works, you'll want to create an aserve.fasl that you can load into your 
application.

### change lisp's current directory to the AllegroServe source

    user(3): :cd  <path-to-aserve>
    
### make a distribution

    user(4): (make-aserve.fasl)

now you'll find aserve.fasl in the aserve source directory.

Configuration
-------------

See the doc/aserve.html file that is part of this project for more
information on configuring AllegroServe.

Documentation
-------------

For complete documentation see the contents of the doc directory, 
which is part of this project or visit the online version of the
[AllegroServe documentation](https://franz.com/support/documentation/current/doc/aserve/aserve.html).

### Quick Start Documentation

cd to the directory containing the distribution and start Allegro cl 
(or start Allegro and use the toplevel ":cd" command to cd to the 
directory containing the aserve). 

#### load aserve.fasl

    user(1): :ld aserve.fasl

#### load the examples (either the compiled or source version)

    user(2): :ld examples/examples

#### start the webserver

    user(3):  (net.aserve:start :port 8010)

#### view in a browser

    http://localhost:8010/

#### Usage notes

 * the steps to load the examples and start the server are interchangeable.
 * if you're running on a PC (or running as root on Unix) you
   can allocate port 80, so you don't have to specify a port
   when running the net.aserve:start function.
 * See the doc directory that is part of this project for more
   detailed usage documenation.

License
-------

The aserve source code is licensed under the terms of the
[Lisp Lesser GNU Public License](http://opensource.franz.com/preamble.html), 
known as the LLGPL. The LLGPL consists of a preamble and the
LGPL. Where these conflict, the preamble takes precedence.  This project is
referenced in the preamble as the LIBRARY.

Notes
-----

Webactions is a session-based framework for building web sites mixing
static and dynamic content that builds upon AllegroServe and is part
of this project.

See the webactions/doc/webactions.html file for more information.

For other links that may be of interest are:

 * [Portable AllegroServe](http://sourceforge.net/projects/portableaserve)
 * [Source to the if* macro](https://franz.com/~jkf/ifstar.txt)
 * [CL-HTTP](http://www.ai.mit.edu/projects/iiip/doc/cl-http/home-page.html)

Examples and Information
------------------------

See the doc/tutorial.html file and the contents under the examples
directory that are part of this project for more examples on how to
work with AllegroServe.

Open Source Info
----------------
      
This project's homepage is <https://github.com/gendl/aserve>. The
`master` branch is intended for this "zaserve" portable version, and
the "franzinc-compatible" branch is intended to be kept in synch with
the official [upstream repository maintained by Franz
Inc](https://github.com/franzinc/aserve)

You may file Issues [here](https://github.com/gendl/aserve/issues)
with any questions, comments, or suggestions. You may also fork this
repository and create Pull Requests.
