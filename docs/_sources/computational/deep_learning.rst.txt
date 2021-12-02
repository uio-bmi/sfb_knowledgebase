Deep Learning
==================================

.. note::

  Aim: provide a broad overview of the concepts relating to the Machine Learning Basics chapter of the Deep Learning book

  Level: beginner 🌱🌿🌳

Chapter 5.1: Machine Learning Basics
****************
As has been described previously in the Knowledge Base, Machine Learning can be defined in many ways. One principle starting point is with the definition of "learning". With such an objective baseline established, progression in decision-making can be effectively measured. In the following we explore and build on the concept of learning provided by Tom Mitchell in 1997 and present a real-world example which incorporates this definition.

Definition of "Learning" and a Practical Example
------------------------
-- Mitchell 1997

  "A computer program is said to learn from experience E with respect to some class of tasks T and performance measure P, if its performance at tasks in T, as measured by P, improves with experience E."

Learning as defined by Mitchell is comprised of an **Experience (E)**, **Performance (P)**, and **Task (T)** with the interaction between these elements giving structure to the learning system. The unique combination of these elements articulate the environments, observations and scores that one can expect of the system. Let us delve into each individually.

1. Task: Tasks describe the kind of observations a learner processes represented by an example containing a collection of Features 
Classification: convert input into k categories

2. Performance: Performance marks the quantitative evaluation used to design metrics in a learner
Due to the nature of the task, this can be specific:
Classification: Accuracy, Precision and Recall, F1-score, AU-ROC
Regression: Mean Absolute Error (MAE), Mean Squared Error (MSE), Root Mean Squared Error (RMSE), R² (R-Squared)

3. Experience: Experience defines the training experience the system will learn
Attribute is there direct or indirect feedback, e.g., direct training examples, indirect information and outcomes Attribute degree to which the learner controls the sequence of training examples, this relates to the label or target and the distinction between supervised/unsupervised Attribute how well it represents the distribution of examples over which the final system performance P is measured



Solving a Logistic Regression Problem
------------------------
  .. image:: ../../_static/images/learning_system.png
   :alt: This figure shows the elements of a learning system, comprising of a training experience, performance measure and learning task.
Components of a ML Algorithm
------------------------
Machine Learning as Optimizing Search
------------------------
Overcoming Overfitting
------------------------

Recommended literature
------------------------

- Goodfellow IJ, Bengio Y, Courville A. Deep Learning. MIT Press; 2016. https://mitpress.mit.edu/books/deep-learning

...
