Setting up and organizing a project
===================================

.. admonition:: 🌱🌿🌳

  Aim: provide reference for a set of topics as well as further reading material for interested readers

  Level: any 🌱🌿🌳

  More advanced sections are labeled wit 🌿 (apprentice) and 🌳 (journeyman).

This section covers topics in:

- project coordination / management tools,
- version control using git,
- containers like Docker,
- virtual environments and package management with e.g., pip and conda,
- code editors.

Project management tools
--------------------------

For both personal and team projects, projects management tools are extremely useful. The tool most commonly
used at the Centre for Bioinformatics is `Trello <https://trello.com/home>`_. Trello is a free online tool
where it is possible to create project boards with lists and concrete to do items.

There are many alternatives, but only some will be mentioned here:

- `GitHub projects and task lists <https://docs.github.com/en/github/managing-your-work-on-github/about-task-lists>`_
  might be useful for large codebase projects.

Version control with git
-------------------------

Version control systems are used to track changes during the code development. They are useful both for
individuals and teams, and as such should be used in every software project. Git is the most used such system,
and is provided by GitHub and other providers (such as GitLab or Bitbucket).

The Biomedical Informatics research group at the University of Oslo has a GitHub organisation where the
repositories can be created for each project of the group members. For public projects, see
`BMI organization on GitHub <https://github.com/uio-bmi>`_.

To learn about git, see `the CodeRefinery project <https://coderefinery.org/>`_ resources:

- `Introduction to version control with Git <https://coderefinery.github.io/git-intro/>`_
- `Collaborative distributed version control <https://coderefinery.github.io/git-collaborative/>`_
- `Git branch design lesson <https://coderefinery.github.io/git-branch-design/>`_

Alternatively, a lot of public resources for version control are available, such as these Atlassian tutorials
for `learning version control <https://www.atlassian.com/git/tutorials/what-is-version-control>`_ and
`learning about git <https://www.atlassian.com/git/tutorials/what-is-git>`_.

Containers
--------------

With many different operating systems and local setups, it is often a challenging task to get all the
required software up and running. Containers are one possible solution that. They encapsulate the entire
working environment including not only needed applications and packages, but also an operating system.
Their main goal is to handle all dependencies in a standardized and reliable manner and ensure that the
same applications can be run on the new computing environment (laptop, server, HPC, etc. depending on the application).

Docker
~~~~~~~

Docker is one container platform we have used in projects at the Centre.

Docker defines several types of objects, but here we will mention only images and containers. Docker
containers are the same as containers discussed above: the full computing environments taking care of all
dependencies. Docker images, on the other hand, are templates defining how these environments are created.

.. seealso::

  For more information on Docker objects, see the official `Docker object documentation <https://docs.docker.com/get-started/overview/#docker-objects>`_.

This section will cover and link to resources for using the existing Docker images and creating new ones.

Install Docker
````````````````

To install Docker, follow `the official Docker installation guide <https://docs.docker.com/get-docker/>`_.

Run a Docker container locally
````````````````````````````````

.. admonition:: 🌿

  Aim: create and run a Docker container from a publicly available Docker image

  Level: apprentice 🌿

Once Docker is installed and running locally, check the list of available containers by running the
following command from the terminal:

.. code-block:: console

  docker ps -a

If you just installed Docker, this list will be empty. If there are any containers, the list will show
container ID, image from which it was created, when it was created, current status, etc.


Copy the following command in the terminal to pull a public Docker image, create a container from it
and run a sample analysis. As an example, we here use `immuneML <https://immuneml.uio.no>`_ image. immuneML
is a software for machine learning analysis of immune receptors. In this example run, it will generate a synthetic dataset
and try to fit a classifier to predict if a person is sick or healthy for the simulated disease.

This command will:

- make the current working directory (pwd) visible inside the container at path /data
- name the container `my_container`
- download the immuneML Docker image from DockerHub from user milenapavlovic
- in a thus created environment, it will run immune-ml-quickstart as described above and store the output to /data/output/ directory
which will be visible later in the current working directory under `output/`.

.. code-block:: console

  docker run -it -v $(pwd):/data --name my_container milenapavlovic/immuneml immune-ml-quickstart /data/output/

The image reference (here `milenapavlovic/immuneml`) can be replaced with any relevant image, and the
command following the image should then be adapted to the particular use-case for the downloaded image.

.. seealso::

  🌳 For more details on the run command and its parameters, see
  `the reference <https://docs.docker.com/engine/reference/run/>`_.

Create a Docker image and publish it on DockerHub
````````````````````````````````````````````````````

.. admonition:: 🌳

  Aim: provide references for creating a Docker image and publishing it in a public repository DockerHub

  Level: journeyman 🌳

To create a Docker image, follow the `Getting started <https://docs.docker.com/get-started/>`_ guide. Parts 1-4
describe how to come up with an image and publish it on DockerHub, that can then be used as described above.

If you are using GitHub for code development and what to use that code as a basis for a Docker image,
this process can also be automated to create a new image on a certain event and publish it on DockerHub.

For example, see the `action YAML file on immuneML repository <https://github.com/uio-bmi/immuneML/blob/master/.github/workflows/docker-publish.yml>`_.
Every time push is performed to the master branch, the image will be rebuilt based on
`the Dockerfile <https://github.com/uio-bmi/immuneML/blob/master/Dockerfile>`_ at the
repository and published.

Virtual environments and package management
----------------------------------------------

to be added

