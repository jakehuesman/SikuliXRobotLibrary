Custom SikuliX Library For Robot Framework
==================================================

TLDR
-----------
Prerequisites: java 8, jython, robotframework, jybot, sikulixapi.jar with tesseract

Setup CLASSPATH AND JYTHONPATH in environment variables:

      CLASSPATH = <path to sikulixapi.jar>
      JYTHONPATH = <path to sikulixapi.jar>\Lib

Install the SikuliXRobotLibrary:

      git clone https://github.com/jaredfin/SikuliXRobotLibrary.git
      cd SikuliXRobotLibrary
      jython setup.py install

Run The Demo:

      jybot -d LOGS -i Demotest demo\calc_test_suite

Introduction
------------

SikuliXRobotLibrary is a gui recognition testing library for Robot Framework
that leverages the SikuliX version 1.1.0 methods.

It is modeled after the Selenium2Library library.

- More information about this library can be found in the `Keyword Documentation`_.
- Installation information is found in the `INSTALL.rst` file.


Directory Layout
----------------

demo/
    A simple demonstration, with calculator application in Windows 8

doc/
    Keyword documentation

src/
    Python source code


Usage
-----

To write tests with Robot Framework and SikuliXRobotLibrary, 
SikuliXRobotLibrary must be imported into your Robot test suite.
See `Robot Framework User Guide`_ for more information.

Preconditions
-------------

SikuliXRobotLibrary supports Jython interpreters supported by the
Robot Framework.

SikuliXRobotLibrary depends on a few other Jython libraries, including
of course Robot Framework. All dependencies are declared in setup.py.

SikuliX must be installed with the Tesseract based OCR features. When running the sikulixsetup-1.1.0.jar,
make sure to select the second and third options.


Installing from source
----------------------

The source code can be retrieved either as a source distribution or as a clone
of the main source repository. The installer requires Jython version 2.7 or
newer. Install by running:

    jython setup.py install

Note: In most linux systems, you need to have root privileges for installation.

Uninstallation is achieved by deleting the installation directory and its
contents from the file system. The default installation directory is
`[JythonLibraries]/site-packages/robotframework_SikuliXRobotLibrary-1.0.0-py2.7.egg`.


Verifying Installation
----------------------

Once you have installed SikuliXRobotLibrary it is a good idea to verify the installation. To verify installation start jython::

     C:\> jython

and then at the Python prompt type::

    >> import SikuliXRobotLibrary
    >>

If the python command line interpretor returns with another prompt ('>>' as shown above) then your installation was successful.

Troubleshooting Installation
----------------------------

The most common issue with installing SikuliXRobotLibrary is missing dependencies. An error like::

    ImportError: No module named sikuli

indicates that you are missing the sikulixapi.jar package.  To correct this problem, install the sikulixapi.jar with tesseract
then add the following in the environment variables::

      CLASSPATH = <path to sikulixapi.jar>
      JYTHONPATH = <path to sikulixapi.jar>\Lib

Similarly if you receive "No module named ..." error message then you have another missing dependency.  To correct, use easy_install to install the missing package.

.. _pip: http://www.pip-installer.org
.. _easy_install: http://pypi.python.org/pypi/setuptools

Running the Demo
----------------

The demo directory contains an easily executable demo for Robot Framework
using SikuliXRobotLibrary. To run the demo, run::

    jybot -d <output directory> -i <tag> <suite directory>

E.g.::

    jybot -d C:\SikuliXRobotLibrary\demo\logs -i Demotest C:\SikuliXRobotLibrary\demo\calc_test_suite
    Note: C:\SikuliXRobotLibrary\demo\logs will be automatically created upon running the script
	

Keyword Documentation
---------------------- 
https://pybot.wordpress.com/2015/10/31/sikulixrobotlibrary-keyword-documentation/

Robot Framework User Guide
---------------------- 
http://code.google.com/p/robotframework/wiki/UserGuide


ELI5 Installation Instructions (Wiindows 7 or 8 Installation)
------------------------------

1. Install Java 8. 

Link: http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html

i. Run java -version in command promt, java version should be displayed, otherwise, add C:\Program Files\Java\jre<version>\bin in Environment Variable

2. Install Jython 2.7:

Link: http://www.jython.org/downloads.html

i. Download the installer then make sure to accept the license agreement during installation
ii. Add 'C:\jython2.7.0\bin' in Environment variables
iii. Check if jython is installed, run 'jython --version' command in command prompt, if successful, the following will be displayed
      Jython 2.7.0

3. Install Robotframework from the source:

Link: https://pypi.python.org/pypi/robotframework

i. Download and extract the rf source (robotframework-2.9.2.tar.gz (md5)) to a local directory
ii. cd to the extracted directory where 'setup.py is located
iii. pen a command prompt and run: jython setup.py install
    * jybot.bat will be created in C:\jython2.7.0\bin
    * C:\jython2.7.0\Lib\site-packages\robotframework-2.9.2-py2.7.egg will be created
iv. Run jybot --version in command prompt, if successful, the following will be displayed:
    Robot Framework 2.9.2 (Jython 2.7.0 on java1.8.0_60)

4. Install SikuliX v1.0.0 setup

Link: https://launchpad.net/sikuli/sikulix/1.1.0

i. Download sikulixsetup-1.1.0.jar (md5) in a local directory
    * I would suggest C:\SikuliX1.1.0
ii. Double-click the sikulixsetup-1.1.0.jar file
iii. Once the dialog for installation is launched, select options 2 and 3, i.e. Pack2 and the tesseract (install the IDE, option 1 later but backup the sikulixapi.jar first)
    *if sucessful, the sikulixapi.jar will be created (must be 24-23MB in size otherwise, there may be some missing files if a smaller jar file is created)

5. Add CLASSPATH: C:\SikuliX1.1.0\sikulixapi.jar and JYTHONPATH: C:\SikuliX1.1.0\sikulixapi.jar\Lib in Environment Variables

i. Right-click > My Computer > Properties > Advanced system settings > Environment Variables
ii. Click New button. In Variable Name field, type CLASSPATH and in Variable Value, type C:\SikuliX1.1.0\sikulixapi.jar
iii. Do the same thing for JYTHONPATH

6. Install SikuliXRobotLibrary from source
Link: https://github.com/jaredfin/SikuliXRobotLibrary
i. Do these in command prompt:
    cd C:\
    git clone https://github.com/jaredfin/SikuliXRobotLibrary.git
    cd SikuliXRobotLibrary
    jython setup.py install

    * see https://github.com/jaredfin/SikuliXRobotLibrary for more installation instructions and troubleshooting

7. Run the demo calculator test
i. Do the following in command prompt:
    cd C:\SikuliXRobotLibrary
    jybot -d LOGS -i Demotest demo\calc_test_suite
    *if successful, this should run the test

Note: sikuli takes over the mouse pointer, make sure to not use the test pc while running the tests