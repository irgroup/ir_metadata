# Metadata module of repro_eval

In order to provide a software interface for developers and experimenters, we have implemented the metadata support into [`repro_eval`](https://github.com/irgroup/repro_eval) - the reproducibility toolkit for system-oriented IR experiments. In the following we provide a brief overview of the [`metadata`]()-module and its classes, for more details we refer the interested reader to the actual implementations in the GitHub repository.

## MetadataHandler

The `MetadataHandler` is used for in- and output operations of annotated run files, e.g., it can be used to annotate run files with a template in the form of a YAML file.

```Python
from repro_eval.metadata import MetadataHandler

metadata_handler = MetadataHandler(run_path='./run.txt', metadata_path='./metadata.yaml')

metadata_handler.write_metadata()
```
## MetadataAnalyzer

The `MetadataAnalyzer` is used to analyze sets of different run files in reference to a run that has be be provided upon instantiation. The `analyze_directory()` method returns a dictionary with PRIMAD identifiers as keys and lists with the corresponding run paths as values.


```Python
from repro_eval.metadata import MetadataAnalyzer

metadata_analyzer = MetadataAnalyzer(run_path='./run.txt')

experiments = metadata_analyzer.analyze_directory(dir_path='./runs/')

...
```

## PrimadExperiment

The `PrimadExperiment` is used to determine the reproducibility measures between a reference run and a set of one or more reproduced run files. Depending on the type of the PRIMAD experiment, several reproducibility measures can be determined. We differentiate between different PRIMAD types by lower- and upper-case letters in the identifier. For instance, if the Method is changed by parameter sweeps, the corresponding identifier results as `priMad` with an upper-case M.

```Python
...

from repro_eval.metadata import PrimadExperiment

run_candidates = experiments.get('priMad')

primad_experiment = PrimadExperiment(primad='priMad', 
                                     ref_base_path='./run.txt',
                                     rep_base=run_candidates,
                                     rpd_qrels='./qrels.txt')

primad_experiment.evaluate()
```