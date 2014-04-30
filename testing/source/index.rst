================
Software Testing
================

* Trevor Bramwell
* @bramwelt
* http://github.com/bramwelt

Outline
=======

* What is Testing?
* Types of Tests
* Methodologies
* Tools
* Concerns

What is Testing?
----------------

**Test** */tɛst/*

* "The means by which the presence, quality, or
genuineness of anything is determined; a means of trial."

What Testing Give You
---------------------

* Confidence, not Proof

  * "Beware of bugs in the above code; I have only proved it correct,
    not tried it." -- *Donald Knuth*
    
* 100% Coverage != 0 Bugs

Types of Testing
================

Smoke
-----

* “Kicking the Tires”
* ”Build Verification”
* ”Does it start?”

Unit
----

* Branch
* Statement
* Fixtures

Unit Doubles
------------

* Mocks/Fakes
* Stubs
* Spies

Brief History of Unit Testing
-----------------------------

* SUnit_ (Smalltalk) - Kent Beck
* JUnit (Java) - Kent Beck & Erich Gamma

  * CUnit
  * PyUnit
  * QUnit
  * *etc...*

Integration
-----------

* Multiple parts together
* Randomization of test runs

Acceptance
----------

* Does it meet the user requirements?

System
------

* Given an initial input, does it produce a final output?

Usability/UX
------------

* Did we check the user's mental model?
* Are the buttons clickable?

Regression
----------

* Bugs can come back to bite you!

Fuzz
----

* inTFn1fqYkVhXivFbsrH2bReYajwuRA1

Test Methodologies
==================

BDD
---
Behavior Driven Development

* Before ... Expect ... It

TDD
---
Test Driven Development

* Red -> Green -> Refactor

DDD
---
Documentation Driven Development

* Also called README Driven Development
* Docs -> Tests -> Code

Testing Tools
=============

* Load: ab, siege, jmeter
* Fuzz: ????
* Interface: Selenium
* Jenkins
* TravisCI

Testing Concerns
================

Coverage
--------

* Test ALL the code!

**Issues**
* False positives
* Import issues
* Ignore files

Other Concerns
--------------

* Brittleness
* Randomness & Heisenbugs

  * Randomization of data

* “Test the Tests” - Turtles
* Asynchronicity (drive tests synchronously)
* The ‘Un-mockable’ - mock the mock that mocks the mock
* `Broken Window Theory`_

Careers
-------

* Quality Assurance
* Usability Engineering

Resources
=========

* `wiki/Software_testing`_
* Udacity_ test course
* Alberto Savoia: `Beautiful Tests`_ (Chapter 7 of Beautiful Code)

Real World Examples
-------------------

* OSUOSL - GWM
* Rackspace - Otter
* Opscode - Cookbooks

.. _Udacity: https://www.udacity.com/course/viewer#!/c-cs258/l-48587906/m-48713560
.. _Beautiful Tests: http://cdn.ttgtmedia.com/searchSoftwareQuality/downloads/BeautifulTests.pdf
.. _wiki/Software_testing: https://en.wikipedia.org/wiki/Software_testing
.. _Broken Window Theory: https://en.wikipedia.org/wiki/Broken_windows_theory
.. _SUnit: http://www.xprogramming.com/testfram.htm
