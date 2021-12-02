Deep Learning
==================================

.. note::

  Aim: provide a broad overview of the concepts relating to the Machine Learning Basics Chapter of the Deep Learning book

  Level: beginner 🌱🌿🌳

Chapter 5.1: Machine Learning Basics
****************
As has been described previously in the Knowledge Base, Machine Learning can be defined in many ways. One principle starting point is with the definition of "learning". With an objective baseline established for learning, progression in decision-making can be effectively measured and evaluated. In the following we explore and build on the concept of learning provided by Tom Mitchell in 1997 and present a real-world example which incorporates this definition.

Definition of "Learning" and a Practical Example
------------------------
-- Mitchell 1997

  "A computer program is said to learn from experience E with respect to some class of tasks T and performance measure P, if its performance at tasks in T, as measured by P, improves with experience E."

Learning as defined by Mitchell is comprised of an **Experience (E)**, **Performance (P)**, and **Task (T)** with the interaction between these elements giving structure to the learning system. The unique combination of these elements therefore articulates the environments, observations and scores that one can expect of the learning system. Let us delve into each individually.

  .. image:: ../../_static/images/learning_system.png
   :align: center
   :alt: This figure shows the elements of a learning system, comprising of a training experience, performance measure and learning task.
Components of a ML Algorithm

1. Task: Tasks describe the kind of observations a learner processes, often times represented by an example (i.e., observation instance) containing a collection of Features. Tasks in the real-world typically are of a classification or regression type.
  * Classification: solving classification tasks involves the learning algorithm producing a function f:R :sup:`n`→ {1, . . . , k} which assigns an input described by vector x to a category identified by numeric code k
  * Regression: solving regression tasks involves the learning algorithm producing a function f:R :sup:`n`→ R which assigns an input described by vector x to a numeric scalar

2. Performance: Performance exacts the quantitative evaluation used to design metrics in a learning system. Measures of performance are tied to the nature of the task, for example metrics can be:
  * In Classification: Accuracy, Precision and Recall, F1-score, AU-ROC
  * In Regression: Mean Absolute Error (MAE), Mean Squared Error (MSE), Root Mean Squared Error (RMSE), R² (R-Squared)

3. Experience: Experience defines the training experience the system will face and this encompasses the scope of learning situations surrounding the learning system. A number of attributes contributes to a training experience. 
  * Feedback: Is the nature of feedback direct or indirect, for example do training observations have direct training outcomes (i.e., labels) or is there indirect information for the learner to infer outcomes 
  * Control: To what extent does the learner control the sequence of training examples, is part of the training experience provided by a random process outside the learner's control? Determining the supervised or unsupervised nature of a learner can help in understanding it's control over the training experience
  * Representation: How well does the learner represent the distribution of examples over which the final system Performance (P) is measured? The learner's experience is more reliable when training examples follow the distribution similar to future test examples

Solving a Logistic Regression Problem
------------------------
------------------------
Machine Learning as Optimizing Search
------------------------
Overcoming Overfitting
------------------------

Recommended literature
------------------------

- Goodfellow IJ, Bengio Y, Courville A. Deep Learning. MIT Press; 2016. https://mitpress.mit.edu/books/deep-learning

...
