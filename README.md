# ObliquePlaneMicroscopy
Shearing and Deconvolution Routines for OPM (Snouty)

Python and MATLAB routines for shearing and deconvolving data, respectively.  

The shearing program was developed in Python 3.6 operating in an Anaconda environment on a Linux operating system.  Changes would need to be made in order to use it on a Windows Machine.  Use the code at your own risk, and expect bugs.  Changes will be made in the future to improve readability and reduce redundancy, but time is of the essence during manuscript submission.

Our data acquisition software saves data according to the following structure:  .../cellType/label/date/cell#/1_CH0#_######.tif.  Thus, all of the information is provided in the file path itself.  A hypothetical example is MCF7/AktPH-GFP/200218/Cell5/1_CH00_000003.tif.
The deskewing software is designe dto be operated at the date level of the path.  It then goes through that directory, identifies the number of Cell# subdirectories, and then within those directories, the number of channels, and timepoints.  It then deskews all of these files in a parallel process.  You execute the software as follows: python deskewDirectory.py MCF7/AktPH-GFP/200218/Cell5/

The lateral pixel size, z step size, oblique illumination angle, and number of parallel threads, is all specified within the function itself.

The deconvolution software is used on the raw, non-sheared data.  It uses an experimentally measured PSF as a prior, and updates this PSF with a double blind deconvolution process.  This code is written in MATLAB.  The experimentally measured PSF needs to have the same voxel dimensions as the data that was acquired, or be appropriately scaled.  After deconvolution, the image is then sheared using the aforementioned Python code.

- Kevin Dean
