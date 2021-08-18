Getting started in bioinformatics
==================================

.. note::

  Aim: Provide a reference list of resources to get started in the computational aspects of bioinformatics.

  Level: beginner 🌱

Running an analysis from the command line in UNIX environment
----------------------------------------------------------------

to be added

Running tools from a Docker image
------------------------------------

Docker image is a template, a definition of how a computing environment (including libraries, packages, installations and the operating system) should
look like. Based on a Docker image, a Docker container is created which is the environment itself based on the image.

To run a tool from Docker environment, see the following tutorials: :ref:`Install Docker` and :ref:`Run a Docker container locally`.

Running tools developed at the Centre for Bioinformatics
----------------------------------------------------------

immuneML
~~~~~~~~~~

immuneML, a platform for machine learning analysis of adaptive immune receptors and repertoires, can be ran from the command line, Docker container,
or through an online graphical interface. To get started, graphical user interface might be the most convenient:

- the graphical interface can be accessed at https://galaxy.immuneml.uio.no
- documentation is available at `this link <https://docs.immuneml.uio.no/latest/galaxy.html>`_.

For alternative ways to run immuneML and detailed user documentation, visit `the immuneML documentation website <https://docs.immuneml.uio.no>`_.

GSuite HyperBrowser
~~~~~~~~~~~~~~~~~~~~~~~

To be added

other tools?

Introduction to programming
-------------------------------

To design custom analysis that cannot be run from the existing tools, one could develop specialized scripts to speed up the analysis or to design new
ones. To get started with programming, see :ref:`Getting started with programming` that discusses choosing the programming language, links to useful
courses and other material, as well as provides tasks to test the progress.

Version control
-----------------

Version control allows us to keep track of the changes made in the files: both code and results. To learn more about it, see :ref:`Version control with git`.