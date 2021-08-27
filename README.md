# Centre for Bioinformatics Knowledge Base
Knowledge base with links to relevant resources by the Centre for Bioinformatics, UiO.

## Contributing to the knowledge base

### Updating the existing content

All the content in the knowledge base is written in the restructured text (rst) format and compiled with Sphinx (for documentation, see https://www.sphinx-doc.org/en/master/).
To edit any of the existing pages, pull the content from the master branch, find the page under the source folder in this repository and edit the rst file. Check that 
you have the latest content from the master again and commit and push the changes to the master branch. This push will trigger a GitHub action which will run Sphinx 
in the background based on the content in the source folder, and create the HTML pages and store them in the docs folder. The changes 
in the newly updated docs folder will be automatically visible at https://uio-bmi.github.io/sfb_knowledgebase/ in a few minutes.

### Adding new content

#### Where to add the content

At the website at https://uio-bmi.github.io/sfb_knowledgebase/ in the left sidebar the content is divided into sections: 

- designing an analysis covering machine learning, statistics, genomics, and immunology, 
- programming and best practices,
- setting up and organizing a project covering project management tools, version control, virtual environments etc. and
- running an analysis describing running tools from the command line, using tools like Galaxy, and accessing servers and available infrastructure.

New topics can be added under the existing subsection or if the topic is very specific, it can be added under 'Specialized topics' in the 
corresponding section.

#### How to add the content

To add a new page, add a new rst file in the chosen directory under the source folder, add the content, and add the page path without the extension 
to one of the sidebars by explicitly listing it at the page one level up in the hierarchy. For example, the index.rst file contains the following:

```
.. toctree::
   :maxdepth: 2
   :caption: Getting started:

   computational/getting_started_bioinf
   biology/genomics_intro
   biology/immunology_intro
```

From this, Sphinx will generate a sidebar with these three items that will have the text the same as the main title on the corresponding pages.

Images and other static files are located under source/_static/ and should be included using the relative path from the target page. 
For example, to add an image to the overview.rst file under `computational/ml/`, the following snippet is used:

```

.. image:: ../../_static/images/TCR_motif_example.png
   :alt: This figure shows a table with a list of immune receptor (TCR) sequences and the motifs that were extracted as common in those sequences when adjusted and when not adjusted for the genetic background.

```
