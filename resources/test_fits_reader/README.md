Test Fits Images
================

Notes from Karen Collins on test images
---------------------------------------

* LCO_calibrated.fz &mdash; a typical compressed calibrated LCO image that has WCS headers
* LCO_calibrated.fits mdash; the uncompressed version of the same image (with WCS headers)
* TESS_sector2_FFI_example.fits &mdash; a typical single TESS FFI image &mdash; it has a WCS solution in the header, but the image is in an extension and took a hack to the current AIJ FITS reader to get it to open
* 3D_BIAS_with_WCS.fits contains 10 images that should open as a stack
* Io-8-bit-signed.fits has only 141 image values &mdash; see [Issue #8](https://github.com/observatree/AstroImageJ/issues/8)
* 16-bit-unsigned.fits &mdash; should show as ranging from 1233 to 65535 (not -31535 to 32767); see [Issue #9](https://github.com/observatree/AstroImageJ/issues/9)

Additional test images (presently out of scope)
-----------------------------------------------

Additional test images are available: [150 MB zip file](https://www.astro.louisville.edu/software/astroimagej/updates/test_fits_images.zip)

Comments on additional test images:

* LCO_raw.fz &mdash; a typical compressed LCO raw image &mdash; the image is separated into 4 readout quadrant images. Will it open at all? I don't think it has WCS headers, but I am not sure.
* LCO_raw.fits &mdash; the uncompressed version of the same image
* TIC2733208_TESS_sector2.fits &mdash; a typical image sequence for a TESS 2-minute cadence &mdash; this one may be challenging. It has over 18K small TESS postage stamp images and would ideally open as an image stack of 18K+ images. The images are actually in a FITS binary table extension. I don't know if this will work out of the box, or if it will even be practical to do at all. The overall WCS solution in the fits file should be applied to all of the individual fits images. I have attached python code that reads the file and splits it into 18K+ individual fits files that can be opened in AIJ in case it is helpful.
