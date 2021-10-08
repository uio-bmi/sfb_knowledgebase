.. SfB_knowledge_base documentation master file, created by
   sphinx-quickstart on Wed Apr 28 12:01:32 2021.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

Centre for Bioinformatics - Knowledge Base
===========================================

.. note::

   This website is under development.

For a bioinformatician, a broad variety of topics may be of interest to design and conduct an analysis.
This repository is a collection of resources for these tasks grouped by a common theme. The resources include both custom content
and links to relevant online material and training.

To describe the complexity level of each topic, there will be one of the following signs next to the title to indicate:
🌱 (beginner level, no previous knowledge needed), 🌿 (apprentice level, some previous experience on the topic might be useful to
follow the content) and 🌳 (journeyman level, assuming experience on the given topic and the content might be quite detailed).

Quick start for new members 🌱
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Follow one of these tutorials to set up a demo project. The steps for these projects will ensure that you have access to BMI resources
and some basic understanding of setting up a project. Even if you have a lot of experience, it might still be useful to go through the
tutorials even if only to set up necessary accounts.

- :ref:`Get started with a simple Python project` 🌱
- :ref:`Get started with a simple R project` 🌱

Computational competencies
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Do you have biological background and want to get started in bioinformatics? 🌱
---------------------------------------------------------------------------------------

Visit :ref:`this link <Getting started in bioinformatics>` to read:

- how to run analysis from the command line
- run tools from a Docker image
- using custom tools developed at the centre
- computational thinking? / algorithms?
- intro to programming
- :ref:`Clean code`
- version control

Do you need more information on specific tools developed at the Centre? 🌱
-------------------------------------------------------------------------------

- :ref:`GSuite Hyperbrowser`
- Proto
- :ref:`immuneML` and `immuneML Galaxy <https://galaxy.immuneml.uio.no>`_
- other tools?

Do you need to run large analyses and use servers or HPC clusters?
--------------------------------------------------------------------

- HPC intro
- Fram
- Saga
- TSD
- contact information for immunohub

Do you want to read up on some more specialized/advanced topics in programming? 🌿
-----------------------------------------------------------------------------------
- :ref:`Clean code`
- best coding practices 🌿
- organizing code 🌿
- testing 🌿

Do you need to set up computational workflows? 🌿
-------------------------------------------------

- :ref:`Containers` and :ref:`Docker` 🌿
- :ref:`Services to share developed tools`
- snakemake, nextflow and similar tools 🌿

Do you want to learn more about statistics and machine learning? 🌱
-----------------------------------------------------------------------

- introduction to machine learning for bioinformatics 🌱
- training and evaluation of machine learning methods 🌿
- mathematics for machine learning 🌿
- introduction to statistics 🌱
- specialized topics in machine learning and statistics 🌿

Biological competencies
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Do you have a computational background (computer science, engineering, statistics) and need to learn biology? 🌱
---------------------------------------------------------------------------------------------------------------------------

See the following pages for resources for:

- :ref:`Getting started with genomics` 🌱
- :ref:`Getting started with immunology and adaptive immune receptors` 🌱

.. toctree::
   :maxdepth: 2
   :caption: Getting started:

   computational/getting_started_bioinf
   biology/genomics_intro
   biology/immunology_intro

.. toctree::
   :maxdepth: 2
   :caption: Topics:

   analysis_design
   programming
   setting_up_project
   running_analysis


Indices and tables
==================

* :ref:`genindex`
* :ref:`modindex`
* :ref:`search`
