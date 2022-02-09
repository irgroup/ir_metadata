# Supporting Reproducible IR Experiments with Metadata Annotations of Open Runs

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)]()
[![DOI](https://zenodo.org/badge/DOI/10.1234/zenodo.1234567.svg)]()

Experimentation in information retrieval (IR) research is an inherently data-driven process that often results in experimental artifacts - so called run files. In order to promote the reproduciblity of IR experiments, Voorhees et al. introduced the idea of [Open Runs](http://research.nii.ac.jp/ntcir/workshop/OnlineProceedings12/pdf/evia/04-EVIA2016-VoorheesE.pdf) proposing to provide every run file with an open-source software repository. We build up on the idea of Open runs and propose to make the experimental artifacts even more valuable and reproducible by metadata annotations of run files.  We align the metadata schema to the [PRIMAD model](https://sigir.org/files/forum/2016J/p068.pdf) which provides a conceptual taxonomy for reproducible IR experiments.

From a practical point of view, we propose to add the metadata, similar to a file header, as comments in the beginning of the run file. The commonly used evaluation toolkit [`trec_eval`](https://github.com/usnistgov/trec_eval) allows to [add comments in the run files](https://github.com/usnistgov/trec_eval/issues/20) by starting line comments with `#` and an official support is in development for [`v10.0`](https://github.com/usnistgov/trec_eval/tree/version-10.0-dev).

This website hosts an introduction of the outlined metadata schema of Open Runs for which more details and background information can be found in our SIGIR resource paper. For each PRIMAD component this website provides [checklists](metadata/overview) that can be used as a reference when annotating run files in order to prepare them for reproducibility.

Besides this website, we give an introduction to the metadata and the software support of [`repro_eval`](https://github.com/irgroup/repro_eval) in a [Colab notebook]() that makes use of some annotated runs that are taken from our curated dataset with annotated runs hosted in a [Zenodo]() archive.