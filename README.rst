About
=====

Abilian SBE (Social Business Engine) is a platform for developing social business applications, and more specifically collaborative / enterprise 2.0 business applications, such as enterprise social networks (ESN).

It is based on the `Abilian Core <http://abilian-core.readthedocs.org/en/latest/>` project which provide the basic services, on top of Flask and SQLAlchemy.

Abilian SBE adds the concept of *communities*, which are collaborative spaces with services such as lightweight document management, discussions, wikis, user timelines.


Install
=======

Prerequisites (native dependencies)
-----------------------------------

- Python 2.7, ``virtualenv``, ``pip``
- `Redis <http://redis.io/>`__
- Sqlite, or a postgresql database.
- A few image manipulation libraries (``libpng``, ``libjpeg``...)
- ``poppler-utils``, ``unoconv``, ``LibreOffice``, ``ImageMagick``.
- `{Less} <http://lesscss.org/>`__ css pre-processor
- A Java environment (JRE 1.7 for example). The `closure compiler
  <https://developers.google.com/closure/compiler/>`__ is used for minifying
  javascript files. You don't have to install the compiler yourself, but a Java
  environment is required.

Get a working application
-------------------------

The following commands will create a virtualenv for the application,
install a script named ``abilian_sbe``, launch development server and
open a setupwizard in your browser:

.. code:: bash

    $ virtualenv sbe
    $ cd sbe; source bin/activate
    $ pip install -U setuptools pip
    $ pip install abilian-sbe
    $ python -m abilian.sbe.app setup_sbe_app

MAC OS + Homebrew
-----------------

You will need to install the following packages using homebrew
(**before** running ``pip install ...``):

::

    brew install python2.7 jpeg git libmagic poppler imagemagick


Testing
=======

Short test
----------

Make sure all the dependencies are installed (cf. above), then run ``make
test``.

With coverage
-------------

Run ``make test-with-coverage``.

Full test suite
---------------

Install `tox <http://pypi.python.org/pypi/tox>`__. Run ``tox -e ALL``.

2 environments are available:

- ``py27``: uses in-memory sqlite
- ``py27_postgres``: uses local postgresql server (you need to first create a
   database, and user/password; tox uses environment variables
   ``POSTGRES_HOST``, ``POSTGRES_PORT``, ``POSTGRES_DB``, ``POSTGRES_USER``,
   ``POSTGRES_PASSWORD``)

Running with gunicorn
---------------------

.. code:: bash

    gunicorn 'abilian.sbe.app.create_app()'

Build Status
============

The project is under continuous integration with Travis:

|Build Status|

.. |Build Status| image:: https://travis-ci.org/abilian/abilian-sbe.svg?branch=master
   :target: https://travis-ci.org/abilian/abilian-sbe