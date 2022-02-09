# Data

The metadata information about the **Data** should include the test collection, training data and others. For the test collection, the data source as well as the location of the qrels and topics files have to be reported. If available, the identifier that is chosen by the data catalog [`ir_datasets`](https://ir-datasets.com/) should be reported as well. The example below uses another test collection as training data, but generally, this entry should be reported as a list, especially if more than one data source is used in the experiments. The third subcomponent `other` covers miscellaneous information related to the data, for instance, about word embeddings or stopwords.

## Checklist

- `data` &rarr; `test collection`  
**Description:**  
A test collection includes but is not limited to the following components:  
`data` &rarr; `test collection` &rarr; `name`: Name of the test collection.   
`data` &rarr; `test collection` &rarr; `source`: Official source of the collection.      
`data` &rarr; `test collection` &rarr; `qrels`: Source of the qrels.    
`data` &rarr; `test collection` &rarr; `topics`:  Source of the topic file.  
`data` &rarr; `test collection` &rarr; `ir_datasets`: Identifier in [`ir_datasets`](https://ir-datasets.com/).  
**Type:**  
*Collection of scalars*

- `data` &rarr; `training data`  
**Description:**  
List of different training data sources that are used in the experiments.   
`data` &rarr; `training data` &rarr; `name`  
`data` &rarr; `training data` &rarr; `source`  
**Type:**  
*Sequence of mappings*; a mapping usually has a `name` and a `source`

- `data` &rarr; `other`  
**Description:**  
List of other data sources that are used in the experiments, for instance, external stopword lists, thesauri, or word embeddings.    
`data` &rarr; `other` &rarr; `name`  
`data` &rarr; `other` &rarr; `source`  
**Type:**  
*Sequence of mappings*; a mapping usually has a `name` and a `source`

## Example

```YAML
data:
  test collection:
    name: The New York Times Annotated Corpus
    source: https://catalog.ldc.upenn.edu/LDC2008T19
    qrels: https://trec.nist.gov/data/core/qrels.txt
    topics: https://trec.nist.gov/data/core/core_nist.txt
    ir_datasets: https://ir-datasets.com/nyt
  training data:
  - name: TREC disks 4 and 5
    source: https://trec.nist.gov/data/cd45/index.html
    qrels: https://trec.nist.gov/data/robust/qrels.robust2004.txt
    topics: https://trec.nist.gov/data/robust/04.testset.gz
    ir_datasets: https://ir-datasets.com/trec-robust04
  other:
  - name: GloVe embeddings
    source: https://nlp.stanford.edu/projects/glove/
  - name: Indri's stopword list
    source: https://sourceforge.net/projects/lemur/
```
