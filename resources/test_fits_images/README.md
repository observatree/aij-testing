Test Fits Images
================

Notes from Karen Collins on LCO images
--------------------------------------

* LCO_calibrated.fz - a typical compressed calibrated LCO image that has WCS headers

Additional Test Images
----------------------

Additional test images are available: [150 MB zip file)(https://www.astro.louisville.edu/software/astroimagej/updates/test_fits_images.zip)

Comments on additional test images:

LCO_calibrated.fits - the uncompressed version of the same image (with WCS headers)

LCO_raw.fz - a typical compressed LCO raw image - the image is separated into 4 readout quadrant images. Will it open at all? I don't think it has WCS headers, but I am not sure.
LCO_raw.fits - the uncompressed version of the same image

TESS_sector2_FFI_example.fits - a typical single TESS FFI image - it has a WCS solution in the header, but the image is in an extension and took a hack to the current AIJ FITS reader to get it to open.

TIC2733208_TESS_sector2.fits - a typical image sequence for a TESS 2-minute cadence - this one may be challenging. It has over 18K small TESS postage stamp images and would ideally open as an image stack of 18K+ images. The images are actually in a FITS binary table extension. I don't know if this will work out of the box, or if it will even be practical to do at all. The overall WCS solution in the fits file should be applied to all of the individual fits images. I have attached python code that reads the file and splits it into 18K+ individual fits files that can be opened in AIJ in case it is helpful.

I have a bank of additional test files that I have collected from users over the years. I think the above ones will be the most challenging though. I expect the rest will work if your TheSkyX images work.
