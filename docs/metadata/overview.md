## Metadata schema

In the following, we provide an overview of the metadata, but we also refer the interested reader to our SIGIR resource paper where each (sub)component is backed with studies from the literature.

Our metadata schema is based on **PRIMAD** which stands for **P**latform, **R**esearch goal, **I**mplementation, **M**ethod, **A**ctor, **D**ata. Each of these components is essential for reproducible IR experimentation. We align the metadata information to the PRIMAD model and propose subcomponents that should be added to each metadata entry if required.

Besides a short description of each PRIMAD component, we provide a checklist that can be used as a reference when annotating runs and we provide illustratives examples. The current schema-version is `v0.1`.


### General information

The metadata annotations should start and end with the `ir_metadata` identifier, i.e., `ir_metadata.start` in the first line and `ir_metadata.end` in the last line of the metadata header. In general, it has to follow the [YAML formatting conventions](https://yaml.org/). 

At the beginning, the metadata includes some general information about the current schema-version (this version), the version of the run metadata (in case the metadata is updated in the future), and the run tag that usually can be found in the last column of a TREC run. This more general information is followed by the metadata for each PRIMAD component for which we provide checklists and examples on the following sites.

```YAML
ir_metadata.start
schema-version: 0.1
run-version: 1.0
tag: h2oloo.ccrf.04.core17.ax_e3_0.6
platform:
    ...
research goal:
    ...
implementation:
    ...
method:
    ...
actor:
    ...
data:
    ...
ir_metadata.end
```
