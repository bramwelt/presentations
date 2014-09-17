
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

.. figure:: /_static/breakpad.png
    :class: center-aligned
    :height: 20em
    :alt: http://google-breakpad.googlecode.com/svn/wiki/breakpad.png


.. slide:: "Internship Goal: Fix The Build System"
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


Reducing The Build Time
=======================

.. rst-class:: build

* Cut the build time from 20 minutes to 10 minutes.

* Saving an approximate total of 1 week a month.

.. note::
    20 minutes ➜ 10 minutes = 10 minutes per build
    10 minutes × 216 builds a month = 2150 minutes a month
    2150 minutes ÷ 60 minutes an hour = 35.8333 hours

.. nextslide::
    :increment:

* Ensured the socorro-virtualenv was deleted, but not pip-cache.

.. nextslide::
    :increment:

* Removed build redundancies: Abusing Make.

::

    # scripts/build.sh
    make clean
    make test
    make analysis
    ...

::

    # makefile
    analysis: bootstrap
       ...

    test: bootstrap
       ...


.. slide:: 2. Setting up Travis-CI
    :class: segue large-print


Transitioning to Travis-CI
==========================

* Adds parallelism to builds

  * Current PRs lock builds on Jenkins. Only one PR ran at a time.

.. nextslide::

* Equivalent build time without reliance on internal Infra

  * All services are run locally on the Travis VMs.

.. nextslide::

* Only allowed Ubuntu on Travis, which is divergent from our RHEL
  deploy.

* Can ship off packages.

* Caching dependencies cost extra

.. note::

    Transitioning to Travis-CI provided several benefits. The major one
    being parallel builds.


.. slide:: 3. Packing Socorro
    :class: segue large-print


Creating Native Packages
========================

* FPM super easy to use.

::

    $ fpm -s dir -t rpm -n socorro \
          -v 103 \
          socorro/


* Now have RPMs

* deploy.sh -> pre/post-install


.. slide:: "Benefits, Drawbacks, Opportunities"
    :class: segue large-print

Conclusion
==========


Special Thanks
==============

  * Chris Lonnen
  * Rob Helmer
  * Peter Bengtsson
  * Laura Thomson
  * Jill Alverez & Misty Orr
  * Interns

.. note::

    Lonnen - availablility, guidance
    Rob - ecstatic about my work
    Peter - asking about my family and reminding me that (work != life)
    Laura - For graciously giving me this opportunity
    Jill & Misty - For running an amazing intern program
    Interns - For making this summer super fun
