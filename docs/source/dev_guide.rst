.. _devguide:

Developer Guide
===============

.. contents::
    :local:
    :depth: 1

.. WARNING:: To create new processes look at examples in Emu_.

Building the docs
-----------------

First install dependencies for the documentation:

.. code-block:: console

  $ make bootstrap_dev
  $ make docs

.. _testing:

Running tests
-------------

Run tests using `pytest`_.

First activate the ``climexp_numerical_wps`` Conda environment and install ``pytest``.

.. code-block:: console

   $ source activate climexp_numerical_wps
   $ conda install pytest flake8  # if not already installed

Run quick tests (skip slow and online):

.. code-block:: console

    $ pytest -m 'not slow and not online'"

Run all tests:

.. code-block:: console

    $ pytest

Check pep8:

.. code-block:: console

    $ flake8

Run tests the lazy way
----------------------

Do the same as above using the ``Makefile``.

.. code-block:: console

    $ make test
    $ make testall
    $ make pep8

Prepare a release
-----------------

Update the Conda specification file to build identical environments_ on a specific OS.

.. note:: You should run this on your target OS, in our case Linux.

.. code-block:: console

  $ make clean
  $ make install
  $ make spec

.. _`environments`: https://conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html#building-identical-conda-environments


Bump a new version
------------------

Make a new version of Climate Explorer WPS service in the following steps:

* Make sure everything is commit to GitHub.
* Update ``CHANGES.rst`` with the next version.
* Dry Run: ``bumpversion --dry-run --verbose --new-version 0.8.1 patch``
* Do it: ``bumpversion --new-version 0.8.1 patch``
* ... or: ``bumpversion --new-version 0.9.0 minor``
* Push it: ``git push``
* Push tag: ``git push --tags``

See the bumpversion_ documentation for details.

.. _bumpversion: https://pypi.org/project/bumpversion/
.. _pytest: https://docs.pytest.org/en/latest/
.. _Emu: https://github.com/bird-house/emu
