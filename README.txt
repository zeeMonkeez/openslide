OpenSlide

Carnegie Mellon University and others

http://openslide.org/


==========================


What is this?
=============

This library reads whole slide image files (also known as virtual slides).
It provides a consistent and simple API for reading files from multiple
vendors.


What is the license?
====================

This code is licensed under the GNU LGPL version 2.1, not any later version.
See the file lgpl-2.1.txt for the text of the license.


Requirements
============

This library requires zlib, libjpeg, libtiff, OpenJPEG 1.x, libxml2,
cairo >= 1.2, and glib >= 2.16.  Leica support requires libtiff >= 4.

The openslide-write-png program additionally requires libpng.


Features
========

The library can read Aperio, Hamamatsu, Leica, MIRAX, and Trestle formats,
as well as TIFF files that conform to a simple convention. (InterScope
files tend to be readable as this generic TIFF.)

More information about formats is here:
http://openslide.org/formats/

An openslide_t object can be used concurrently from multiple threads
without locking. (But you must lock or otherwise use memory barriers
when passing the object between threads.)


Properties
==========

The library exposes certain properties as string key-value pairs for
a given virtual slide. (These are accessed by way of the
"openslide_get_property_names" and "openslide_get_property_value" calls.)

These properties are generally uninterpreted data gathered from the
on-disk files. New properties can be added over time in subsequent releases
of OpenSlide. A list of some properties can be found at:
http://openslide.org/properties/

OpenSlide itself creates these properties (for now):

 openslide.background-color
   The background color of the slide, given as an RGB hex triplet.
   This property is not always present.

 openslide.comment
   A free-form text comment.

 openslide.mpp-x
   Microns per pixel in the X dimension of level 0. May not be present or
   accurate.

 openslide.mpp-y
   Microns per pixel in the Y dimension of level 0. May not be present or
   accurate.

 openslide.objective-power
   Magnification power of the objective. Often inaccurate; sometimes missing.

 openslide.quickhash-1
   A non-cryptographic hash of a subset of the slide data. It can be used
   to uniquely identify a particular virtual slide, but cannot be used
   to detect file corruption or modification.

 openslide.vendor
   The name of the vendor backend.


Other Documentation
===================

The definitive API reference is in openslide.h. For an HTML version, see
doc/html/openslide_8h.html in this distribution.

Additional documentation is available from the OpenSlide website:
http://openslide.org/

There is also a Carnegie Mellon SCS Technical Report:

 CMU-CS-08-136
 A Vendor-Neutral Library and Viewer for Whole-Slide Images
 Adam Goode, M. Satyanarayanan

 http://reports-archive.adm.cs.cmu.edu/anon/2008/abstracts/08-136.html
 http://reports-archive.adm.cs.cmu.edu/anon/2008/CMU-CS-08-136.pdf

Note that the tech report contains API documentation for a previous,
unreleased version of this library.


Acknowledgements
================

OpenSlide has been supported by the National Institutes of Health and
the Clinical and Translational Science Institute at the University of
Pittsburgh.


How to build?
=============

./configure
make
make install

(If building from the Git repository, you will first need to install
autoconf, automake, libtool, and pkg-config and run "autoreconf -i".)

Good luck!
