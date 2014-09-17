
.. Mozilla Socorro slides file, created by
   hieroglyph-quickstart on Thu Sep  4 15:09:10 2014.


About Me
========

.. figure:: /_static/benny_the_beaver.gif
    :height: 8 em
    :width: 8 em
    :class: center-aligned
    :alt: http://content.sportslogos.net/logos/33/798/full/7hp60p8pey24f17y7da86g4en.gif


.. figure:: /_static/osuosl.png
    :class: center-aligned
    :width: 12 em
    :height: 6 em
    :alt: http://osuosl.org/sites/default/files/osllogo-web_0.png


.. figure:: /_static/mozilla-logo.png
    :class: center-aligned
    :width: 12 em
    :height: 8 em
    :alt: http://upload.wikimedia.org/wikipedia/commons/5/5c/Mozilla_dinosaur_head_logo.png

.. note::

    * Senior at Oregon State University studying Applied Computer Science
    * Student System Administrator and Software Developer at Oregon State
        University Open Source Lab
    * Intern at Mozilla working on Socorro


What is Socorro?
================

.. figure:: /_static/socorro_logo.png
    :class: right-aligned

Socorro : /soˈko.ro/ : noun

    1. Reference to the Array Operations Center (AOC) in Socorro, NM
       that controls the Very Long Baseline Array (VLBA).

    2. A distributed system for collecting, processing, and
       analyzing crash reports submitted by the Breakpad library.

.. figure:: /_static/vla.jpg
    :height: 13em
    :width: 17em
    :class: center-aligned
    :alt: https://www.flickr.com/photos/caveman_92223/4750606873

.. nextslide::

.. figure:: /_static/socorro-block-diagram.png
    :class: center-aligned

.. nextslide::

.. figure:: /_static/breakpad.png
    :class: center-aligned
    :height: 20em
    :alt: http://google-breakpad.googlecode.com/svn/wiki/breakpad.png

.. nextslide::

.. figure:: /_static/breakpad-with-socorro.png
    :class: center-aligned
    :height: 20em
    :alt: http://google-breakpad.googlecode.com/svn/wiki/breakpad.png


.. slide:: Overview
    :class: segue large-print


"What would you say...you do here?"
===================================

.. rst-class:: build

Three Major Contributions:

1. Cleaned up the Build System
2. Setup Travis-CI for testing Pull Requests
3. Created Native System Packages (RPMs)

.. note::

    I made three major contributions to Socorro over the Summer.

    The first half I spent removing redundant steps and dependencies
    within the build system. Cutting the build time in half.

    The second half I spent adding Travis-CI support, and updating the
    build to package Socorro as a native appliction. Allowing for easier
    installation and distribution of Socorro.


.. slide:: 1. Cleaning Up The Build
    :class: segue large-print


Cleaning up The Build
=====================

1. Caching Dependencies
2. Removing Build Redundancies


Caching Dependencies
====================

* Build using Jenkins (ci.mozilla.org)
* Runs ``scripts/build.sh``
* Destroys Workspace Each Run

.. nextslide::
    :increment:

* Python Virtualenv Package Poisoning
* pip-cache
* 6 minute saving


Removed Build Redundancies
==========================

Makefile & Bash

::

    # scripts/build.sh
    make clean
    make bootstrap
    make test
    make analysis
    ...

::

    # makefile
    analysis: bootstrap
       ...

    test: bootstrap
       ...

.. nextslide::
    :increment:

* Configuration Variables
* Make Target -> Bash Script

.. nextslide::
    :increment:

Before::

    $ wc -l Makefile
    122 Makefile

After::

    $ wc -l Makefile
    31 Makefile


Cleaning Up The Build
=====================

.. rst-class:: build

* Build Time: 20 minutes down to 10

    * Caching Dependencies (6 minutes)
    * Removing Build Redundancy (4 minutes)

* Total savings: 1 Week a Month

.. note::
    20 minutes ➜ 10 minutes = 10 minutes per build
    10 minutes × 216 builds a month = 2150 minutes a month
    2150 minutes ÷ 60 minutes an hour = 35.8333 hours

.. slide:: 2. Setting up Travis-CI
    :class: segue large-print


Transitioning to Travis-CI
==========================

Problems with Jenkins:

    * Shared Test Infra - Multi-job Build Lock

    * Remote Resources - Networks Fail

.. nextslide::

.travis.yml::

    language: python
    python:
      - "2.6"
    addons:
      postgresql: "9.3"
    services:
      - rabbitmq
      - memcached
      - elasticsearch
    before_install:
      - sudo apt-get update -qq
      - sudo apt-get install -y npm libxml2-dev libxslt1-dev
      - npm install -g less
    script:
      - ./scripts/build.sh

.. nextslide::

Drawbacks:

    * Only Supports Ubuntu - We Run RHEL

    * Caching only available in Travis-Pro

    * No Build Chaining

.. nextslide::

Benefits:

    * Local Test Resources

    * PRs Built in Parallel


.. slide:: 3. Packing Socorro
    :class: segue large-print


Creating Native Packages
========================

FPM - Effing Package Management:

    * Quick and Easy

    * Builds DEBs & RPMs

.. nextslide::

Command Line::

    fpm -s dir -t $BUILD_TYPE \
        -v $BUILD_VERSION \
        -n "socorro" \
        -m "<socorro-dev@mozilla.com>" \
        -C $BUILD_DIR \
        --epoch 1 \
        --license "MPL" \
        --vendor "Mozilla" \
        --url "https://wiki.mozilla.org/Socorro" \
        --description "$DESC" \
        --before-install scripts/package/before-install.sh \
        --after-install scripts/package/after-install.sh \
        --before-remove scripts/package/before-remove.sh \
        --after-remove scripts/package/after-remove.sh \
        --config-files /etc/socorro \
        --exclude *.pyc \
        --exclude *.swp \
        data etc var

.. nextslide::

deploy.sh:

    * pre-install.sh
    * post-install.sh

.. nextslide::

Production Install::

    rpm -i socorro-latest.rpm


.. slide:: What I Learned
    :class: segue large-print

Conclusion
==========

1. Cleaned up the Build System
2. Setup Travis-CI for testing Pull Requests
3. Created Native System Packages (RPMs)

.. nextslide::

Technologies:

    * Make
    * Bash
    * Travis
    * FPM
    * Packer
    * Puppet

Special Thanks
==============

  * Chris Lonnen
  * Rob Helmer
  * Peter Bengtsson
  * Laura Thomson
  * Jill Alverez & Misty Orr
  * Mozilla Interns

.. note::

    Lonnen - availablility, guidance
    Rob - ecstatic about my work
    Peter - asking about my family and reminding me that (work != life)
    Laura - For graciously giving me this opportunity
    Jill & Misty - For running an amazing intern program
    Interns - For making this summer super fun
