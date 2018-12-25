AIJ Testing
===========

This repository contains a plan for a basic system test or "smoke test"
of an AstroImageJ release candidate. The system test also serves as a
terse recipe for doing a transit analysis with AstroImageJ.

Prior to the port of AstroImageJ to Java 8, there were no tests
associated with the sources. Since the diffs of ImageJA from
v1.47i to v1.52i merged into AstroImageJ &mdash; this merge
is a large component of the port of AstroImageJ to Java 8 &mdash; 
are 87357 lines long, the port would obviously be destabilizing
without significant testing.

Acknowledgements
----------------

The author (Brian Hill) would like to acknowledge the help learning
AstroImageJ provided by Dennis Conti's AAVSO CHOICE Course: [Exoplanet
Observing](https://www.aavso.org/exoplanet-observing-choice-course).

The test resources are a portion of the transit data taken and
analyzed with Ariana Hofelmann, and
[jointly presented](http://physics.stmarys-ca.edu/observatory/resources/SteppingStones-AAVSO-2018-11-16.pdf)
along with other transit data, at the November 16, 2018 meeting of the AAVSO.
