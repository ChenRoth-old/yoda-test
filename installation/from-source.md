---
layout: bt_wiki
title: Installing from sources
category: Installation
draft: false
weight: 500

---

Installing Cloudify from sources is possible from [PyPi](https://pypi.python.org/pypi)
and [GitHub](http://github.com/).

hugo
This method of installation is intended for advanced users or developers.

Installation from sources requires an environment with compilers installed and
configured since some of Cloudify's dependencies are not pure Python modules.

Familiarity with [Virtualenv](https://virtualenv.readthedocs.org/en/latest/) and [Pip](https://pip.pypa.io/en/stable/) is recommended as well.
hugo

hugo
It is recommended to install all of the components below in a virtualenv
in order to avoid polluting the global Python environment on your system and to
remove the requirement for root permissions on some of the systems.
hugo

## Installation Prerequisites
For all users the following components are required:

* [Python 2.7.X](https://www.python.org/downloads/)
* [pip 6.0+](https://pip.pypa.io/en/stable/installing/)
* [virtualenv 12.0+](https://virtualenv.readthedocs.org/en/latest/installation.html)

### For Windows users
* [Microsoft Visual C++ Compiler for Python 2.7](https://www.microsoft.com/en-us/download/details.aspx?id=44266)

### For Linux users
The following should be available in your OS package repository:
* Python header files (`python-dev` in Ubuntu/Debian or `python-devel` in CentOS/RHEL)
* GNU C compiler (`gcc`)

### For OS X users
* [Xcode Command Line Tools](https://developer.apple.com/library/ios/technotes/tn2339/_index.html#//apple_ref/doc/uid/DTS40014588-CH1-DOWNLOADING_COMMAND_LINE_TOOLS_IS_NOT_AVAILABLE_IN_XCODE_FOR_OS_X_10_9__HOW_CAN_I_INSTALL_THEM_ON_MY_MACHINE_)

## Installing from PyPi

PyPi is the official repository for 3rd party Python modules. Cloudify uploads
its Python artifacts to PyPi.

Installing the latest release from PyPi is done by running the following commands
in a terminal:
hugo
$ pip install cloudify
hugo

It's also possible to request a specific version:
hugo
$ pip install cloudify==3.3
hugo

PyPi contains the same [releases](https://github.com/cloudify-cosmo/cloudify-cli/tags) that you can find on GitHub, however naming convention
is a bit different, for example, to get `3.3m6` you'll need to request
`cloudify==3.3a6`.

Full list of PyPi versions is [available here](https://pypi.python.org/pypi/cloudify/json).

## Installing from GitHub

Cloudify uses GitHub as its main online source code repository.

Installing the latest stable version from GitHub can be done by running the following
commands in a terminal:
hugo
$ CFY_VERSION="3.3"
$ pip install "https://github.com/cloudify-cosmo/cloudify-cli/archive/$CFY_VERSION.zip" \
  --requirement "https://raw.githubusercontent.com/cloudify-cosmo/cloudify-cli/$CFY_VERSION/dev-requirements.txt"
hugo

Installing latest bleeding edge release can be done in the similar manner:
hugo
$ CFY_VERSION="master"
$ pip install "https://github.com/cloudify-cosmo/cloudify-cli/archive/$CFY_VERSION.zip" \
  --requirement "https://raw.githubusercontent.com/cloudify-cosmo/cloudify-cli/$CFY_VERSION/dev-requirements.txt"
hugo

You can set the `CFY_VERSION` variable to any desired version from [version list](https://github.com/cloudify-cosmo/cloudify-cli/tags).
