================
Software Testing
================

How to write tests, what to write tests for, and why they’re important, etc

Overview
========

Brief History
-------------
SUnit[6] -> JUnit -> PyUnit

What Testing Give You
---------------------

* Confidence, not Proof
* 100% != No bugs

Types of Testing
================

Smoke
-----

* “Kicking the Tires”
* ”Build Verification”
* ”Does it start?”

Unit
----

  * branch
  * statement
  * randomization of data
  * fixtures
  * Mocks (python mock)

    * fakes (& verified)
    * stubs (& verified)

Integration
-----------

  * randomization of test runs

Acceptance
----------

System
------

Usability/UX
------------

  * aka: user testing

Regression
----------

Fuzz
----

  * Protocol aware

Test Methodologies
==================

BDD
---
Behavior Driven Development

TDD
---
Test Driven Development

DDD
---
Documentation Driven Development

  * Also called README Driven Development
  * Docs -> Tests -> Code

Testing Tools
=============

* Load: ab, siege, jmeter
* Fuzz: ????
* Interface: selenium
* Jenkins
* TravisCI

Testing Concerns
================

* Coverage

  * false positives
  * import issues
  * ignore files

* Brittleness
* Randomness & Heisenbugs
* “Test the Tests” - Turtles
* Asynchronicity (drive tests synchronously)
* The ‘Un-mockable’ - mock the mock that mocks the mock
* Broken Window Theory [5]

Careers
-------

* Quality Assurance
* Usability Engineering

Resources
=========

* Test Wiki [4]
* Udacity test course [2]
* Alberto Savoia: Beautiful Tests (Chapter 7 of Beautiful Code) [3]

Real World Examples
-------------------

* OSUOSL - GWM
* Rackspace - Otter
* Opscode - Cookbooks

References
----------
[1] http://www.xprogramming.com/testfram.htm
[2] https://www.udacity.com/course/viewer#!/c-cs258/l-48587906/m-48713560
[3] http://cdn.ttgtmedia.com/searchSoftwareQuality/downloads/BeautifulTests.pdf
[4] https://en.wikipedia.org/wiki/Software_testing
[5] https://en.wikipedia.org/wiki/Broken_windows_theory
[6] https://en.wikipedia.org/wiki/SUnit
