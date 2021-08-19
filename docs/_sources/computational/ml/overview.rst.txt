Brief overview of machine learning in computational biology
================================================================

.. note::

  Aim: get an intuition and high-level understanding of what machine learning is and types of problems it can help solving from a
  computational biology perspective

  Level: beginner 🌱

With the development of sequencing technologies, large amounts of data became available that can be examined for biological properties.
For example, from `the VDJdb database <https://vdjdb.cdr3.net/>`_ (`Bagaev et al. 2020 <https://academic.oup.com/nar/article/48/D1/D1057/5582255>`_),
we can retrieve T-cell receptor sequences specific to the epitope YLQPRTFLL of SARS-CoV-2 and discover motifs in these amino acid sequences with or
without genetic background, as shown below (the motifs and the sequences were obtained from VDJdb):

.. image:: ../../_static/images/TCR_motif_example.png
   :alt: This figure shows a table with a list of immune receptor (TCR) sequences and the motifs that were extracted as common in those sequences when adjusted and when not adjusted for the genetic background.

One way we can approach the analysis of these sequences is to build a position weight matrices showing the product multinomial distribution of amino
acids. In this way we can describe these sequences. On the other hand, if we want to predict for a new sequence if it is specific to a virus or not,
we might need a bit different approach.

Machine learning is a powerful approach to discovering patterns in (biological) data
--------------------------------------------------------------------------------------

Machine learning (and statistics) includes a set of methods that allow for making inference about the data. For example if we want to predict if a
receptor sequence will bind the virus or not, we could fit a logistic regression model on the receptor sequence data and then predict the binding for
the new receptors using the model.

.. image:: ../../_static/images/simple_ML_workflow.png
   :alt: This figure shows
