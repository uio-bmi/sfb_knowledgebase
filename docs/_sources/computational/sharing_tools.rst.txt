Services to share developed tools
**********************************

This document gives an overview of different services that can be used to share developed tools in the bioinformatics field or when developing tools in general.

The services discussed here are Galaxy, Docker, Binder, Google Colab, and pip/conda.


Galaxy
======
`Galaxy <https://galaxyproject.org/>`_ is a web-based platform for data-intensive biomedical research that allows the user to perform analyses through a user interface set up by the developers. This way, the user can upload and analyze data without working with code, and without the need to install anything locally on their machine.

Behind the scenes, Galaxy will handle the server setup and the storage of the data, so the user can focus on the analysis itself.

Setting up Galaxy
-----------------

Developer's side
^^^^^^^^^^^^^^^^
Setting up a Galaxy instance starts with cloning the Galaxy repository on `GitHub <https://github.com/galaxyproject/galaxy>`_. This provides the developer with a base Galaxy instance that can be customized to fit the workflow of the developed tool. The developer can add and remove tools, add a customized homepage, grant themselves admin access to the instance, etc.

After the instance is set up, the developer can host it on a server or a cloud service of choice, where the user can access it from their internet browser.

Docker
======
`Docker <https://www.docker.com>`_ is a platform that allows developers to develop, share, and run applications regardless of the system details. Usually, when a developed tool is shared with others, it might happen that it would work on one machine but not on the other. This is usually due to the fact that each machine might have its own operating system, dependencies and configuration files, system tools, settings, etc. Docker aims to solve this problem by providing a way to package all these dependencies and system files in one piece of software, which is called a Docker image, such that this image could be shared and run on any system, regardless of its technical details. Once such an image is hosted on a server or run locally on a machine, it becomes a Docker container, i.e. a piece of software that "contains" everything your tool needs to bu run properly. 

Setting up Docker
-----------------

Developer's side
^^^^^^^^^^^^^^^^
To set up a docker image, first, you install Docker on your machine and then write what is known as a docker file. Such a file includes instructions that state which files or requirements are needed to run the tool. The next step is to build a docker image from that file using the :code:`docker build` command. During that process, the Docker engine will go through these instructions one by one and execute the corresponding command. 

Once the image is built you can share it with others or post it on DockerHub.

User's side
^^^^^^^^^^^^^^^^
From the user's side, you also need to install Docker on your machine, and then run the docker image from the command line using the :code:`docker run` command. Depending on you how the developer has set up the docker file, running this command will connect you to a virtual OS where everything is set up for the tool to run properly.

In addition, you can choose to host that image on a server of choice instead of running it on your local machine, in case you need access to more computational resources, for instance.

Binder
======
If you don’t want to go through all of these steps and you don't really need control at a system level, and the tool is developed in Python, then one option would be to use Binder. The idea of Binder is that if you have Jupyter notebooks and you want to run them with as few steps as possible, then you can turn your GitHub repo into an executable environment set up with everything the tool needs. 

Actually, what happens behind the scenes is that BinderHub, the backend of Binder, will create a Docker image, launch it in the Cloud, and connect you to it via your browser.

Binder supports three languages Julia, Python, and R, though, a Binder session ends after a short period of inactivity (10 min) and up to 6 hours of run time, so this is intended for short and quick use instead of running computations that take a lot of time. You also get 2G of RAM. 

Additionally, the repo which you want to turn into such an executable environment should be public, as the Binder development team chose not to handle the security issues related to handling private repositories. Still, if accessing private repositories is a feature you need, Binder gives you the option of building your own BinderHub. Actually, the public service that you would usually use, `mybinder.org <mybinder.org>`_,  is actually where one such deployment lives.


Setting up Binder
-----------------

Developer's side
^^^^^^^^^^^^^^^^
Setting up a Binder instance is a simple procedure that requires only a public GitHub repository, ideally with pre-written Jypyter notebooks. To set this up, you go to `mybinder.org <mybinder.org>`_, fill in the details of the repository, and optionally include a default Jupyter notebook that you would like to be displayed first, once the instance is launched.

Once you add all the information, you can either share the link that Binder provides, or optionally copy a text, also provided by Binder, and paste it into the README file of the repository to show a binder badge from which the users can launch an instance.

User's side
^^^^^^^^^^^^^^^^
From the user's side, launching a binder instance is as easy as opening the link provided by the developers or clicking on the badge on the homepage of the GitHub repository.


Google Colab
============
Another option that offers a similar service is `Google Colab <https://research.google.com/colaboratory/>`_. Colab is a service that allows you to run Jypyter notebooks on Google servers with access to more computational power, more RAM, and more storage if needed. The sessions also allow for up to 90 minutes of inactivity and the session can run for up to 12 hours. One extra feature provided by Colab is that you can connect it to Google Drive, allowing the developer to import data into the notebook and work with them.

If you need more than that, you can upgrade to Pro and Pro+ and get more RAM, better GPUs, and 24 hours of runtime, though currently, it is not available in many countries including Norway.


Setting up Colab
-----------------
Setting a Colab notebook can be performed by either of both, the developer of the tool and a user of it. This is done by simply cloning the GitHub repository using the :code:`clone` command, followed by using and running the Python code written by the developer.

Pip
===
`pip <https://pip.pypa.io/en/stable>`_ is the package installer for Python, which you use to install Python packages that can be downloaded from the Python Package Index (PyPI). Ideally, this is the method that would be used when a Python tool is fully developed. 

Setting up pip
-----------------

Developer's side
^^^^^^^^^^^^^^^^
Once the tool is developed and ready to be published, building it as a (Python) package includes a couple of steps to ensure that it can be installed using pip, while also installing the dependencies and the libraries that the tool needs. The general layout of doing so starts with creating an account and registering yourself on PyPI, installing some tools required to build packages, creating a :code:`setup.py` file along with a LICENCE, followed by compiling the package using the already mentioned tools. Once the package is built, you can share it and make it publicly available by uploading it to PyPI where other users can download it and install it, whether locally or on a server.
