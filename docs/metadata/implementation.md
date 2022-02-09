# Implementation

The metadata information about the **Implementation** should include the URL of the open-source repository if available. If so, also the commit at which the code of the repository was used should be made explicit. If the experiments are run from the command line, the corresponding commands including all the arguments and parameters should be added.

## Checklist

- `implementation` &rarr; `executable` &rarr; `cmd`  
**Description:**  
The software command that was used to conduct the experiments, i.e., to make the run.  
**Type:**  
*Scalar*; usually a string of characters
- `implementation` &rarr; `source` &rarr; `lang`  
**Description:**    
All programming languages that were used for the experiments.  
**Type:**   
*Sequence of scalars*; listing of strings 
- `implementation` &rarr; `source` &rarr; `repository`  
**Description:**  
The URL of the corresponding software repository.  
**Type:**  
*Scalar*; usually a string of characters
- `implementation` &rarr; `source` &rarr; `commit`  
**Description:**  
The commit at which the repository was used for the experiments.   
**Type:**  
*Scalar*; usually a string of characters

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
