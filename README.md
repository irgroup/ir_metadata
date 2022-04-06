# `ir_metadata`

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/irgroup/ir_metadata/blob/master/resources/demo.ipynb)
[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.5997491.svg)](https://doi.org/10.5281/zenodo.5997491)

## About

This repository hosts the underlying resources of the `ir_metadata` website.

`ir_metadata` is an extensible metadata schema for information retrieval experiments.

Please visit the [website](https://irgroup.github.io/ir_metadata/) for more information.

## How to edit and contribute to the website

The website is built with [MkDocs](https://www.mkdocs.org/) and the corresponding [Material theme](https://squidfunk.github.io/mkdocs-material/). 

First, install both packages.
```
pip install mkdocs mkdocs-material
```

Having edited the contents, preview the changes locally.
```
mkdocs serve -a localhost:8000
```

Having committed your changes to this repository, update the rendered website with the following commands.
```
mkdocs gh-deploy
```

## License

The source code of the website is available under [MIT License](https://opensource.org/licenses/mit-license.php).

Please note that the dataset in the Zenodo archive is licensed separately.
