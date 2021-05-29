Get started with a simple Python project
=========================================

In this short tutorial, we provide steps for setting up a sample Python project.

.. note::

  Aim: set up accounts needed to start developing a project and make sure everything is working.

  Level: any 🌱🌿🌳

  To learn more about mentioned concepts and tools, we provide links to other content throughout this document.

1. Make a Trello board
---------------------------

Trello is a simple project management software where you can create a "board" for a project and organize
to-dos in form of lists and cards with arbitrary level of detail.

Go to https://trello.com and create an account. Once you sign up and log in, in the top menu in the right
corner, press the `+` button and choose "Create a new board" for the dropdown menu.

In the menu that opens, name your new board "demo project" and click 'create'.

When you create a board, you will be redirected to the board page and will be able to make a list. Call it
"To do" and add a card for each of the following items:

- get GitHub account
- set up an IDE
- connect IDE with GitHub account
- make a new GitHub repository under BMI organization and connect it to the new project
- create a project and add "Hello world" Python file
- put changes on GitHub

Create an empty "Done" list and when done with each task, move the corresponding card to "Done".

2. Get a GitHub account
---------------------------

Version control allows tracking of changes in the documents (e.g., in code). BMI has an organization set up
on GitHub (https://github.com - one example of version control software) where the
group members can create their own repositories and put their material and projects. To get access,
ask one of the group members to add you and provide them with your GitHub username or an email you wish
to use for this purpose.

.. seealso::

  For more information on GitHub and version control, see :ref:`Version control with git`.

3. Set up an IDE
-------------------

Integrated development environment (IDE) provides a convenient way to develop small and large projects.
For Python projects, install PyCharm from JetBrains. The community version is free for all, and the
professional version is free for academics and can be accessed for free using the institutional email.

To install PyCharm, follow the steps described on the `PyCharm website <https://www.jetbrains.com/help/pycharm/installation-guide.html>`_.

.. seealso::

  For more information how to use PyCharm, see `their quick start guide <https://www.jetbrains.com/help/pycharm/quick-start-guide.html>`_.

4. Connect IDE with GitHub account
-------------------------------------

When you are added to BMI organization on GitHub with your account (step 2 here), connect your IDE with
your GitHub account so that any changes you make can be added to the repository online.

To do this, follow the steps described on the
`PyCharm website for version control systems (VCS) <https://www.jetbrains.com/help/pycharm/quick-start-guide.html#df750766>`_.

5. Make a new GitHub repository and connect it to the new project
------------------------------------------------------------------

From the GitHub website under BMI organization, choose "New" and enter project details. The repository name could be "demo" and include
your initials.

From PyCharm, connect the project with the repository just created on GitHub as described
`here <https://www.jetbrains.com/help/pycharm/set-up-a-git-repository.html>`_.

6. Create a project and add a "Hello World" Python file
----------------------------------------------------------

When you open PyCharm, choose File > New Project.

In the new window that opens, choose "Pure Python" and provide location for the project. By default, a
new virtual environment will be created automatically. Make sure that 'Base Python' points to Python version 3.

Leave all other options with default values.

.. seealso::

  For more information on virtual environments, see :ref:`Virtual environments and package management`.

When the environment is set up, from the top menu, choose VCS > Get from version control. Enter the URL of
the newly created GitHub repository and check out.

Next, create a file by choosing File > New File > Python file. Name the new file "main.py" and
copy the following content:

.. code-block:: python

  print("Hello world from Python!")

When asked if the file should be added to Git, choose "add". This way the changes in the file will be
tracked automatically.

7. Put changes on GitHub
--------------------------

From the bottom menu in PyCharm, click on Git. It will show local changes and files ready to be updated
in the remote repository. If your new file is not there, right click on the file in the left side bar and
choose Git > Commit file.

When the file is under the Local Changes / Default Changelist, click on the "Default Changelist" and then
click on the green check mark ("Commit") in the menu on the left. The pop up menu will open asking to
enter the commit message. It can be simply "initial commit" but for subsequent changes it is a good practice
to have short yet understandable and informative message describing what changes have been made.

When you have entered the commit message, click on the arrow next to the "Commit" button at the bottom of
the menu and choose "Commit and push" from the menu that opened.

This will push your changes and make them visible when accessing the demo project on GitHub from the browser.

8. Check the Trello board
----------------------------

Check if there are any remaining tasks and finish the remaining ones. When there are no more tasks, this
quick start tutorial is done and you have set up all accounts and procedures for Python projects. Congrats!
