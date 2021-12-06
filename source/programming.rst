Programming
==============

.. note::

  Aim: provide a reference list on best practices in programming with varying level of detail

  Level: 🌱🌿

Most of the bioinformatics projects require at least some coding, where others include developing complex
bioinformatics platforms, like `HyperBrowser <https://hyperbrowser.uio.no/hb/#!mode=advanced>`_ or
`immuneML <https://immuneml.uio.no/>`_. This section covers the best practices in
programming, and is useful for both quick coding and platform development project. It covers:

- choosing a programming language,
- how to organize the code,
- unit and integration testing,
- coding and design guidelines.

If you are new to programming, see the :ref:`Getting started with programming` first before diving into
more specialized topics.

Choosing a programming language 🌱
-----------------------------------

For most projects in the Centre, `Python <https://www.python.org/about/gettingstarted/>`_ is used as the main programming language.

For smaller projects that heavily rely on statistics and visualization, projects often use R. R is also sometimes used in larger projects
together with Python, though rpy2 library that allows R to be called from Python.

When running time or memory could be an issue, e.g., due to large datasets, C++ can also be used. If the running time is an issue
only for some parts of the code, only those parts can be optimized with C++ and `Cython <https://cython.org/>`_ and used together Python.

.. note::

  Even though R and Python can be used together, e.g., by using rpy2 library, it might be a lot of work to set them up
  on different infrastructures.

.. note::

  For more information on recommended development environments, see :ref:`Setting up and organizing a project`.

Organizing the code 🌿
---------------------------------

To maintain a good programming style, increase the quality and readability of the code, try to follow the advice below and also
see the recommended reading for more in-depth coverage of the topics.

1. Make the code modular.
^^^^^^^^^^^^^^^^^^^^^^^^^^

Modularity means that at the very least the code should be organized into functions not longer
than 20-30 lines with understandable, descriptive names. Never write large unstructured stretches of code.
Ensure that the function is doing exactly one task (called
`single responsibility principle <https://en.wikipedia.org/wiki/Single-responsibility_principle>`_ in computer science) and
that it has well-defined input and output. For instance, to make a function that will split a string sequence into subsequences
of a given length, one could name the function `manage_sequence(..)`, but that would not make it clear what the function
actually does. It is then hard to go back after some time and understand the code, regardless who the author is. If instead the
same function would be called `split_sequence_into_kmers(..)` it would be clear over time what exactly that function is doing.

2. Use object-oriented approach.
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Beyond the novice programming level, use object-oriented programming to organize the code, even if the project is small in scope.

3. Design software architecture for larger projects.
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

For larger and more complex projects, it is beneficial to spend some time initially on designing a good software architecture
before implementing anything. The requirements might not all be known from the start, but thinking about the known ones and
planning the architecture accordingly will also make it easier to refactor the code when new requirements arise.

4. Develop software in iterations and refactor often.
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Generally, aim for a simpler, working solution first, try to run the code and obtain the feedback, and then improve the code in
the next iteration. This follows agile approach in software development and is particularly useful in research where the
requirements typically evolve over time.

5. Test the code.
^^^^^^^^^^^^^^^^^^^^^^^^^^^

To ensure the code works and that there were no breaking changes, it is good to test the code.

To test that the individual functions or classes perform as expected, write unit tests. This is especially relevant for complex
codebases where debugging can be inefficient if some of the components fail, where there are various use cases and edge cases might
easily compe up. However, there is a balance between writing tests and research and development. For experimental projects and
prototypes that might not be used again or for small one-time scripts where component validation is less important or less
practical, unit tests might not be necessary. On the other hand, if these scripts end up being reused, then it is good to also
have tests.

Integration tests ensure that all components work together as expected. As such, they might discover a wide range of issues and
edge cases that more realistically reflect the real analysis. They should always be developed, even if unit tests already exist.

Recommended reading 🌿
------------------------

Some recommended resources on this topic:

- `Clean Code: A Handbook of Agile Software Craftsmanship <https://www.oreilly.com/library/view/clean-code-a/9780136083238/>`_, Robert C. Martin, 2008

- `Ten simple rules for quick and dirty scientific programming <https://doi.org/10.1371/journal.pcbi.1008549>`_, Gabriel Balaban, Ivar Grytten, Knut D. Rand,
  Lonneke Scheffer, Geir Kjetil Sandve, 2021


Topics in programming
------------------------

.. toctree::
   :maxdepth: 2
   :caption: Topics:

   computational/programming_intro
   computational/clean_code
