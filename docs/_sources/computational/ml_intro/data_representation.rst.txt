Data representation in machine learning
===========================================

.. note:: 🌱

  Aim: introduce the idea of data representation and encoding, explain some basic terminology like features, design matrix, and provide an
  intuition for some commonly used data representation techniques

  Level: beginner 🌱

In computational biology, the data to be used for a machine learning (ML) task might be given in form of
sequences (e.g., DNA sequences, or immune receptor sequences). However, machine learning typically cannot use the data as is -
ML algorithms require the data to be represented in some numerical format. And it is not sufficient that this is just some numerical
format: these should be some meaningful numbers for the given problem.

For example, a task could be that for a given set of immune receptor sequences, an ML model needs to be developed so that it can
predict if the sequence will bind to COVID-19 or not:

.. image:: ../../_static/images/sequence_classification.png
   :width: 80%
   :alt: This figure shows a set of immune receptor sequences colored in orange (to indicate that they will bind COVID-19) or grey (to indicate that they will not bind COVID-19). The sequences are in a set, mapped by function f, to another set that contains classes "positive" (specific to COVID-19) and "negative" (not specific to COVID-19).

These sequences could then be represented by their physicochemical properties, for example. Each sequence could be
represented by a vector of numerical values, where each value corresponds to specific physicochemical property. Each of these properties
is called a `feature`. `Feature vector` is a vector of values for all features (here for all the physicochemical properties considered)
for one sequence. That one sequence is also called an example. ML algorithm will them be trained on set of many examples (many sequences).

Feature vectors for examples are organized in a matrix format, and that matrix is called `design matrix` (or `feature matrix`) and is
usually denoted by X.