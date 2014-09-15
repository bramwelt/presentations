
.. Mozilla Socorro slides file, created by
   hieroglyph-quickstart on Thu Sep  4 15:09:10 2014.


Who Am I?
=========

.. figure:: /_static/benny_the_beaver.gif
    :scale: 50 %
    :alt: http://content.sportslogos.net/logos/33/798/full/7hp60p8pey24f17y7da86g4en.gif

    Oregon State University

.. figure:: /_static/osuosl.png
    :scale: 50 %
    :alt: http://osuosl.org/sites/default/files/osllogo-web_0.png

    OSU Open Source Lab

.. note::

    Stuff, things, me.


Overview: What I contributed to Socorro
=======================================

* Reduced The Build Time
* Transitioned to Travis-CI
* Created Native System Packages


Reducing The Build Time
=======================

  * From 20 minutes down to 10 minutes
  * 10 minutes * average 215 builds a month = 2150 minutes saved a month
  * 2150/60 ~= 35.8333 hours ~= 1 week of work

  * Caching on Jenkins

    * pip-cache

  * Redundancies in Build

    * make -> bash -> make -> bash
    * immediate: bootstrap
    * found later: Django compression (webapp-django bootstrap)



Transitioning to Travis-CI
==========================

  * Adds parallelism to builds

    * Current PRs lock builds on Jenkins. Only one PR ran at a time.

  * Equivalent build time without reliance on internal Infra

    * All services are run locally on the Travis VMs.

  * Only allowed Ubuntu on Travis, which is divergent from our RHEL
    deploy.

  * Can ship off packages.

  * Caching dependencies cost extra


Creating Native Packages
========================

  * FPM super easy to use.

  * Now have RPMs

  * deploy.sh -> pre/post-install


Conclusion
==========


Special Thanks
==============

  * Lonnen (mentor)
  * Laura (manager)
  * Jill & Misty (intern-herders)
  * Department of Whimsy (keeping me sane, and good laughs)

.. note::

    Lonnen - For mentoring me and putting up with my blabbering for 3 months.
    Laura - For seeing my potentials and hiring me.
