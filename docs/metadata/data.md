# Data

The **Data** component comprises the input data of the experiment. The metadata information about the Data should include the test collection, training data and others. For the test collection, the data source as well as the location of the qrels and topics files have to be reported. If available, the identifier that is chosen by the data catalog [`ir_datasets`](https://ir-datasets.com/) should be reported as well. The example below uses another test collection as training data, but generally, this entry should be reported as a list, especially if more than one data source is used in the experiments. The third subcomponent `other` covers miscellaneous information related to the data, for instance, about word embeddings or stopwords.

## Checklist

- `data` &rarr; `test collection`  
**Description:** A test collection includes but is not limited to a `name`, `source`, `qrels`, `topics`, and an `ir_datasets` identifier.    
**Type:** Collection of scalars    
- `data` &rarr; `test collection` &rarr; `name`   
**Description:** Name of the test collection.   
**Type:**  Scalar   
**Encoding:**  [UTF-8](https://www.unicode.org/main.html) encoded string of characters ([RFC3629](https://www.ietf.org/rfc/rfc3629.txt)); `!!str`.
- `data` &rarr; `test collection` &rarr; `source`  
**Description:** Official source of the collection.  
**Type:** Scalar  
**Encoding:**  URI according to [RFC2396](https://www.ietf.org/rfc/rfc2396.txt); `!!str`.      
- `data` &rarr; `test collection` &rarr; `qrels`   
**Description:** Source of the qrels.    
**Type:** Scalar  
**Encoding:**  URI according to [RFC2396](https://www.ietf.org/rfc/rfc2396.txt); `!!str`.   
- `data` &rarr; `test collection` &rarr; `topics`  
**Description:** Source of the topic file.   
**Type:** Scalar  
**Encoding:**  URI according to [RFC2396](https://www.ietf.org/rfc/rfc2396.txt); `!!str`.   
- `data` &rarr; `test collection` &rarr; `ir_datasets`  
**Description:** Identifier in [`ir_datasets`](https://ir-datasets.com/).  
**Type:** Scalar  
**Encoding:** [UTF-8](https://www.unicode.org/main.html) encoded string of characters ([RFC3629](https://www.ietf.org/rfc/rfc3629.txt)); `!!str`.  

- `data` &rarr; `training data`  
**Description:** List of different training data sources that are used in the experiments represented as *mappings*, a single mapping usually has a `name` and a `source`.  
**Type:** Sequence of mappings; `!!seq [!!map, !!map, ...]`.   
- `data` &rarr; `training data` &rarr; `name`  
**Description:**  Name of the training data resource.  
**Type:** Scalar  
**Encoding:** [UTF-8](https://www.unicode.org/main.html) encoded string of characters ([RFC3629](https://www.ietf.org/rfc/rfc3629.txt)); `!!str`.
- `data` &rarr; `training data` &rarr; `source`  
**Description:**  Source location of the training data resource.   
**Type:** Scalar  
**Encoding:** URI according to [RFC2396](https://www.ietf.org/rfc/rfc2396.txt); `!!str`.      


- `data` &rarr; `other`  
**Description:** List of other data sources that are used in the experiments, for instance, external stopword lists, thesauri, or word embeddings. These resources are represented as *mappings*, a single mapping usually has a `name` and a `source`.    
**Type:** Sequence of mappings; `!!seq [!!map, !!map, ...]`.  
- `data` &rarr; `other` &rarr; `name`  
**Description:**  Name of the data resource.  
**Type:** Scalar  
**Encoding:** [UTF-8](https://www.unicode.org/main.html) encoded string of characters ([RFC3629](https://www.ietf.org/rfc/rfc3629.txt)); `!!str`.
- `data` &rarr; `other` &rarr; `source`  
**Description:** Source location of the data resource.  
**Type:** Scalar  
**Encoding:** URI according to [RFC2396](https://www.ietf.org/rfc/rfc2396.txt); `!!str`.    


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
