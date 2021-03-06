
===============================
Sphinx Theme for docs.typo3.org
===============================

:Project:  sphinx_typo3_theme
:Team:     TYPO3 Documentation Team
:Author:   Martin Bless <martin.bless@typo3.org>
:License:  MIT
:Demo:     See this demo docs `t3SphinxThemeRtdDemoDocs
           <https://docs.typo3.org/typo3cms/drafts/github/TYPO3-Documentation/t3SphinxThemeRtdDemoDocs/>`__
           which are kind of a "stresstest" and demonstrate what's possible and
           how the theme can be used.

.. image:: https://raw.githubusercontent.com/TYPO3-Documentation/sphinx_typo3_theme/master/img/screenshot.png
   :alt: Sphinx TYPO3 Theme Screenshot


Table of contents:

.. default-role:: code

.. contents::
   :local:
   :depth: 3
   :backlinks: top


Status
======

.. image:: https://github.com/TYPO3-Documentation/sphinx_typo3_theme/workflows/CI/badge.svg?branch=master
   :alt: CI
   :target: https://github.com/TYPO3-Documentation/sphinx_typo3_theme/actions?query=workflow%3ACI

.. image:: https://github.com/TYPO3-Documentation/sphinx_typo3_theme/workflows/CDN/badge.svg?branch=master
   :alt: CDN Deployment
   :target: https://github.com/TYPO3-Documentation/sphinx_typo3_theme/actions?query=workflow%3ACDN

.. image:: https://github.com/TYPO3-Documentation/sphinx_typo3_theme/workflows/Python%20Package/badge.svg?branch=master
   :alt: Python Package
   :target: https://github.com/TYPO3-Documentation/sphinx_typo3_theme/actions?query=workflow%3A%22Python+Package%22


Installation
============

Install the Theme Using PIP
---------------------------

`PIP <https://pip.pypa.io/en/stable/>`__ is the
`Python <https://www.python.org/>`__ packet manager for
`PyPi <https://pypi.python.org/pypi>`__.
'sphinx_typo3_theme' is provided by the TYPO3 Documentation Team
and available from PyPi.

Installation with ``pip``::

   # fetch from PyPi and install latest version:
   pip install --upgrade sphinx-typo3-theme

   # if required for your system, run a superuser:
   pip install --upgrade sphinx-typo3-theme

For your interest: Some quick examples of ``pip`` usage::

   # find help
   pip install --help
   pip --help

   # install locally for this user only
   pip install --upgrade --user sphinx-typo3-theme

   # uninstall - no matter if installed by PIP or setup.py:
   pip uninstall sphinx-typo3-theme

   # search PyPi, the Python packet index
   pip search sphinx-typo3-theme
   pip search sphinx


Install directly using 'setup.py'
---------------------------------

To install directly from the package::

   git clone git@github.com:TYPO3-Documentation/sphinx_typo3_theme.git
   cd sphinx_typo3_theme
   (sudo) python setup.py install

   # or install locally in user's home:
   python setup.py install --user


Usage
=====

To use the theme in your Sphinx project, you will need to add the following to
your ``conf.py`` and add ``sphinx_typo3_theme`` to your `requirements.txt` file:

.. code:: python

   import sphinx_typo3_theme

   extensions = [
       ...
       "sphinx_typo3_theme",
   ]

   html_theme = "sphinx_typo3_theme"


Usage on docs.typo3.org
=======================

All static assets contained in this theme will be uploaded also to the
TYPO3 CDN. The master branch as well as released are available on the CDN
starting with version `4.0.1`.

.. code::

   https://typo3.azureedge.net/typo3documentation/theme/<theme>/<branch|version>/css/theme.css
   https://typo3.azureedge.net/typo3documentation/theme/sphinx_typo3_theme/master/css/theme.css
   https://typo3.azureedge.net/typo3documentation/theme/sphinx_typo3_theme/4.0.1/css/theme.css


Contributing or modifying the theme
===================================

If you would like to help improve the, theme feel free to fork this project
and create a pull request when you're happy with your changes.


Setup minimal development environment
-------------------------------------

1. Install Node

2. Install Yarn::

    npm install yarn

3. Install project dependencies::

    yarn install

4. Compile::

    yarn build

5. Serve::

    yarn serve


Workflows (GitHub Actions)
==========================

Continous Integration (CI)
--------------------------

`.github/workflows/ci.yml`

1. `build-frontend`
   Ensure that the frontend dependencies can be installed and build. After execution it checks that
   there are no changes uncommitted in the working directory.

2. `build-render`
   Ensure that the theme can be used with the current container. It builds an example documentation
   and serves it as an artifact, to manually verify the rendered result. After execution it checks
   that there are no changes uncommitted in the working directory.

This workflow is executed on every `push` or `pull_request`.


Python Package
--------------

`.github/workflows/python-package.yml`

1. `build`
   Install the `requirements` defined in `requirements.txt` and lint included python files.

2. `package`
   Builds an installable package of the module and provides it as downloadable artifact.

3. `sphinx-quickstart-local`
   Builds a sphinx quickstart documentation and uses the current checkout as theme

4. `sphinx-quickstart-package`
   Builds a sphinx quickstart documentation and uses the artifact from step `package` as theme

This workflow is executed on every `push` or `pull_request`.


Publish Python Package
----------------------

`.github/workflows/python-publish.yml`

1. `deploy`
   Build Package and Publish to https://pypi.org/

This workflow is executed on every `release`.


Content Delivery Network (CDN)
------------------------------

`.github/workflows/cdn.yml`

1. `build`
   Prepare and provide an usable artifact to be deployed to the CDN.

2. `deploy`
   Extract the current version number or branch name from `GITHUB_REF` and uses this as identifier
   to store the assets on the TYPO3 Azure CDN.

   .. code::

      https://typo3.azureedge.net/typo3documentation/theme/<theme>/<branch|version>/css/theme.css
      https://typo3.azureedge.net/typo3documentation/theme/sphinx_typo3_theme/master/css/theme.css
      https://typo3.azureedge.net/typo3documentation/theme/sphinx_typo3_theme/4.0.1/css/theme.css

This workflow is executed on every `push` to the `master` branch and `release`.
