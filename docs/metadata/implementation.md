# Implementation

The metadata information about the **Implementation** should include the URL of the open-source repository if available. If so, also the commit at which the code of the repository was used should be made explicit. If the experiments are run from the command line, the corresponding commands including all the arguments and parameters should be added.

## Checklist

- `implementation` &rarr; `executable` &rarr; `cmd`
- `implementation` &rarr; `source` &rarr; `lang`
- `implementation` &rarr; `source` &rarr; `repository`
- `implementation` &rarr; `source` &rarr; `commit`

## Example

```YAML
implementation:
  executable:
    cmd: python src/main/python/ecir2019_ccrf/generate_runs.py --config src/main/python/ecir2019_ccrf/configs/ccrf.04_core17_BM25+AX.json
  source:
    lang:
    - python
    repository: https://github.com/castorini/anserini
    commit: 9548cd6
```
