Emokit-c
======

Emokit-c is a C based library for user space access to the raw stream
data from the Emotiv EPOC headset. Note that this will not give you
processed data (i.e. anything available in the Emo Suites in the
software), just the raw sensor data.

The C library is backed by hidapi, and should work on any platform
that hidapi also works on.

Python Library
==============

Please note that the python and C libraries are now in different
repos. If you would like to use the python version of emokit, the repo
is at

http://www.github.com/openyou/emokit

Information
===========

FAQ (READ BEFORE FILING ISSUES): https://github.com/openyou/emokit/blob/master/FAQ.md

If you have a problem not covered in the FAQ, file it as an
issue on the github project.

PLEASE DO NOT EMAIL OR OTHERWISE CONTACT THE DEVELOPERS DIRECTLY.
Seriously. I'm sick of email and random facebook friendings asking for
help. What happens on the project stays on the project.

Issues: http://github.com/openyou/emokit-c/issues

Required Libraries
==================

* CMake - http://www.cmake.org
* libmcrypt - https://sourceforge.net/projects/mcrypt/
* hidapi - http://www.signal11.us/oss/hidapi/

Usage
=====

See emokitd.c example

Bindings
========

Go: https://github.com/fractalcat/emogo

Platform Specifics Issues
=========================

Linux
-----

Due to the way hidapi works, the linux version of emokit can run using
either hidraw calls or libusb. These will require different udev rules
for each. We've tried to cover both (as based on hidapi's example udev
file), but your mileage may vary. If you have problems, please post
them to the github issues page (http://github.com/openyou/emokit/issues).

Your kernel may not support /dev/hidraw devices by default, such as an RPi.
To fix that re-comiple your kernel with /dev/hidraw support

OS X
----

Recent OS versions no longer allow usb devices to become unclaimed by the kernel.
You must use a HIDAPI library.

# Frequently asked questions

 - *What unit is the data I'm getting back in? How do I get volts out of
 it?*

 One least-significant-bit of the fourteen-bit value you get back is
 0.51 microvolts. See the
 [specification](http://emotiv.com/upload/manual/EPOCSpecifications.pdf)
 for more details. (Broken Link)
 
 - *What should my output look like?*
 
 Idling, not on someone's head it should look something like this:  
 Y Reading: 0 Quality: 0  
 F3 Reading: 259 Quality: 0  
 F4 Reading: 576 Quality: 0  
 P7 Reading: 258 Quality: 0  
 FC6 Reading: 878 Quality: 0  
 F7 Reading: 118 Quality: 0  
 F8 Reading: 1060 Quality: 0  
 T7 Reading: 252 Quality: 0  
 P8 Reading: -51 Quality: 0  
 FC5 Reading: 1112 Quality: 0  
 AF4 Reading: 481 Quality: 0  
 Unknown Reading: 30 Quality: 1  
 T8 Reading: 614 Quality: 0  
 X Reading: 0 Quality: 0  
 O2 Reading: 337 Quality: 0  
 O1 Reading: -198 Quality: 0  
 AF3 Reading: 146 Quality: 0  
