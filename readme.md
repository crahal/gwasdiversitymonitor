# GWAS Diversity Monitor

[![Generic badge](https://img.shields.io/badge/Python-3.6-<red>.svg)](https://shields.io/)  [![Generic badge](https://img.shields.io/badge/License-MIT-blue.svg)](https://shields.io/)  [![Generic badge](https://img.shields.io/badge/Maintained-Yes-green.svg)](https://shields.io/)

### Introduction

This is a repository which holds an early prototype of the GWAS Diversity Monitor, currently maintained as part of the [Leverhulme Centre for Demographic Science](http://www.demographicscience.ox.ac.uk/). The re-released dashboard can be found at:

<div align="center"> <a href="http://www.gwasdiversitymonitor.com">gwasdiversitymonitor.com</a></div>
<br/><br/>

The interactive plots in this version are written in [Bokeh](https://bokeh.pydata.org/en/latest) and were prototyped on Heroku. Grateful attributions regarding data are made to the [EMBL-EBI GWAS Catalog](https://www.ebi.ac.uk/gwas/). In summary, the dashboard visualizes a systematic interactive review of all GWAS published to date. It borrows a couple of functions from our [Scientometric Review of all GWAS](https://www.nature.com/articles/s42003-018-0261-x). This repo can be cloned and ran on-the-fly to generate a server on localhost as required. The dashboard and associated summary statistics check daily for updates from the Catalog and update with new releases (i.e. we used to run ```generate_date.py``` on a daily cron job and push to the master branch for Heroku to catch).

### Prerequisites

As a pre-requisite to running the Bokeh sever, you will need a working Python 3 installation with all of the necessary dependencies detailed in [requirements.txt](https://github.com/crahal/GWASDiversityMonitor/blob/master/requirements.txt) (generated by pipreqs). We strongly recommend virtual environments and [Anaconda](https://www.anaconda.com/distribution/).  

### Running the Code

This server is operating system independent (through the ``os`` module) and should work on Windows, Linux and OS X all the same. To run: clone this directory, ``cd`` into the directory, and then run ```bokeh serve gwasdiversitymonitor_app --show``` in a terminal to launch the server. In more detail, ``main.py`` generates the figures itself, and contains functions for each of the six plots which are then added to a Jinja2 template using curdoc().add_root(). The template is stored in templates/index.html, and contains html and css to build in additional content (pulling in things like funding templates) and bootstrap it. The ``generate_data.py`` script updates the html with summary statistics from ``gwasdiversitymonitor_app/data/summary/summary.json``.

### Versioning

This dashboard prototype was halted at Version 0.8.0, and wholly represents a prototype. Please note: although the library logs data updates, it could be that additional dictionary based classifications are required with regards to the ```/data/support/dict_replacer_broad.tsv``` file. Please raise an issue in the new page for the project.

### License

This work is free. You can redistribute it and/or modify it under the terms of the MIT license, subject to the conditions imposed by the [EMBL-EBI license](https://www.ebi.ac.uk/about/terms-of-use). The dashboard comes without any warranty, to the extent permitted by applicable law.

### Acknowledgements

We are grateful to comments on the source code and infrastructure from [Ian Knowles](https://github.com/ianknowles), [Yi Liu](https://github.com/YiLiu6240), [Molly Przeworski](https://przeworskilab.com/), [Ben Domingue](https://github.com/ben-domingue), [Sam Trejo](https://cepa.stanford.edu/people/sam-trejo) and the [Sociogenome](http://www.sociogenome.org) group more generally.
