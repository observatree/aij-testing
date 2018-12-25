AstroImageJ Test Plan
=====================

The present document is a plan for a basic system test or "smoke test"
of an AstroImageJ release candidate. It also serves reasonably well as
a recipe for doing a transit analysis with AstroImageJ.

Prior to the port of AstroImageJ to Java 8, there were no tests
associated with the sources.  Since the diffs of ImageJA merged into
AstroImageJ as the foundation of the port to Java 8 are 87357 lines
long, the port would obviously be destabilizing without significant
testing.

This test plan resources come from an actual TrES-2 transit and
analysis. See acknowledgements.

Preliminaries and Prerequisites
-------------------------------

For this test plan to be more than cookbook or recipe to be followed,
the tester should be at least somewhat familiar with the theory and
practice of exoplanet transit observation as is thoroughly discussed
in Bruce Gary's book, "Exoplanet Observing for Amateurs." The "Third
Edition" aka "Second Edition (plus)." The book is available as a
[zipped pdf](http://brucegary.net/book_EOA/ExoplanetObservingAmateurs2ndEdition.zip)
directly from the author.

The workflow assumes that you have bias, dark, flat and light images
already taken, such as the TrES-2 transit images in the resources
directory, taken by Ariana Hofelmann and Brian Hill. It also assumes you have
followed the AstroImageJ installation instructions, including the
workaround for clearing the quarantine bit on macOS 10.12 and higher.

Test Plan
---------

1. Use the DP window to make subtracted flat and light images. Then
make the calibrated lights. During this step you can also tell AIJ
exactly what part of the sky is being looking at. With an account at a
web-based plate solver, AIJ can do this automatically. There is also a
place to input the exact time of the pictures and location of the
obseratory (lat/long).

2. Open the calibrated lights as a virtual stack ALWAYS (a "virtual"
stack is a list of images that AIJ does not attempt to keep
simultaneously in memory). Align the images by choosing the inner and
outer radii of the apertures and selecting the target as well as
several reference stars. The best reference stars are fairly close to
the target star, but isolated so other stars are not caught in the
"background" of the star aperture. They should also be towards the
middle of the picture, to ensure that the star did not move out of
frame during the observing session. NB: If for some reason during the
observing session (such as buffeting by wind) the telesope moved so
that the stars jump significantly across the image, set the aperture
radii to a high or highest setting. This will allow AIJ will to find
the stars. Is it sometimes necessary to run multiple alignment
procedues, decreasing the radii each time.

3. Open the final set of now aligned and calibrated lights (as a
virtual stack!). Select "multiple aperture photomety" and set the
radii to the lowest possbile setting. Select the Target star and the
3-4 comparison stars used in the alignment (not necessary, but the
photos were already aligned for these stars and these stars should be
relatively bright, clear, and isolated). Hit enter.

4. Always save the table of measurements once it pops up. 

5. Make a copy of the target star's flux. Not sure why this is part of
the workflow. Graph the fluxes of the target and reference
stars. Ideally each reference star would be close to a straight line
relative to the mean of the reference stars If there is one
significant outlier, consider removing that one from the calculations,
or re-do the whole process with different comparison stars.

6. For the copy of the target star flux, choose the "Norm/Mag Ref" to
be green_white_green. This will use the data from before and after the
transit to calculate the norm of the target star flux. Leave it as all
green for the others. NB: How AIJ is computing a
signal-to-noise-weighted mean of the reference stars is important to
reproduce.

7. For the copy of the target star flux, select the "fit mode" to be
that of an exoplanet. Leave the original target star data. Select a
straight line for the comparison stars. In the "Multi-plot Main"
window, it is possible to input V Marker 1 and V Marker 2, for known
points of ingress and egress although this of course presumes part of
what an unconstrained fit will find. NB: How AIJ does its best fit
(ingress times, egress times, transit depth) is critical to reproduce
exactly for believability/comparability with most members of the
amateur exoplanet community, who typically are using AIJ on Windows.

8. Execute the fit. A window will pop up asking how the fit should be
created. It will also provide values for the ratio of planet to host
star size and its orbit around the star, and can additionally provide
absolute values for the properties of the planet if the properties of
the host star are known.

Acknowledgements
----------------

The author (Brian Hill) would like to acknowledge the help learning
AstroImageJ from Dennis Conti's AAVSO CHOICE Course: [Exoplanet
Observing](https://www.aavso.org/exoplanet-observing-choice-course).

The test resources are a portion of the transit data taken and
analyzed with Ariana Hofelmann, and
[jointly presented](http://physics.stmarys-ca.edu/observatory/resources/SteppingStones-AAVSO-2018-11-16.pdf)
along with other transit data, at the November 16, 2018 meeting of the AAVSO.
