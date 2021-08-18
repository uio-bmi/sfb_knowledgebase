# Centre for Bioinformatics Knowledge Base
Knowledge base with links to relevant resources by the Centre for Bioinformatics, UiO.

## Contributing to the knowledge base

### How to update existing content

All the content in the knowledge base is written in the restructured text (rst) format and compiled with Sphinx (for documentation, see https://www.sphinx-doc.org/en/master/).
To edit any of the existing pages, pull the content from the master branch, find the page under the source folder in this repository and edit the rst file. Check that 
you have the latest content from the master again and commit and push the changes to the master branch. This push will trigger a GitHub action which will run Sphinx 
in the background based on the content in the source folder, and create the HTML pages and store them in the docs folder. The changes 
in the newly updated docs folder will be automatically visible at https://uio-bmi.github.io/sfb_knowledgebase/ in a few minutes.

### How to add new content

To add a new page, add a new rst file, add the content, and add the page path without the extension to one of the sidebars by explicitly listing 
it at the page one level up in the hierarchy. For example, the index.rst file contains the following:

```
.. toctree::
   :maxdepth: 2
   :caption: Getting started:

   computational/getting_started_bioinf
   biology/genomics_intro
   biology/immunology_intro
```

From this, Sphinx will generate a sidebar with these three items that will have the text the same as the main title on the corresponding pages.
