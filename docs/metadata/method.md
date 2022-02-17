# Method

The **Method** describes the mapping of query-document pairs to a ranking score.The metadata information about the Method should include if the run is automatic or manual, i.e., derived with or without a human-in-the-loop approach, and information regarding the indexing and retrieval. While the indexing is usually composed of several processing steps including tokenization, stemming, and stopword removal, the retrieval method assigns scores between a query and a document. Modern retrieval pipelines are often realized in the form of a multi-stage ranking that is supported by our metadata schema as well. If an additional ranking method reranks the output of a previous retrieval method, it can be reported by the `reranks` entry that refers to the name of the previous method. Likewise, it is possible to report interpolated scores.

## Checklist

- `method` &rarr; `automatic`  
**Description:** Boolean value indicating if it is a automatic (`true`) or manual (`false`) run.   
**Type:** Scalar  
**Encoding:** Boolean; `!!bool`.        
- `method` &rarr; `score ties`  
**Description:** Name or description of the method used to break score ties in the ranking.  
**Type:** Scalar  
**Encoding:** [UTF-8](https://www.unicode.org/main.html) encoded string of characters ([RFC3629](https://www.ietf.org/rfc/rfc3629.txt)); `!!str`.    
**Naming convention:** `(reverse) alphabetical order`, `external collection`
- `method` &rarr; `indexing` &rarr; `tokenizer`  
**Description:** Name of the tokenizer. If available, it can be reported by the class in the software package (see example below).  
**Type:** Scalar  
**Encoding:** [UTF-8](https://www.unicode.org/main.html) encoded string of characters ([RFC3629](https://www.ietf.org/rfc/rfc3629.txt)); `!!str`.    
- `method` &rarr; `indexing` &rarr; `stemmer`  
**Description:** Name of the stemmer. If possible, the stemmer should be reported by the class name in the software package (see example below). If this is not possible, it should meet the naming conventions below.   
**Type:** Scalar  
**Encoding:** [UTF-8](https://www.unicode.org/main.html) encoded string of characters ([RFC3629](https://www.ietf.org/rfc/rfc3629.txt)); `!!str`.    
**Naming convention**: `Porter`, `Krovetz`, `Lovins`, `Snowball`, `n-grams`, ...  
- `method` &rarr; `indexing` &rarr; `stopwords`  
**Description:** Name of the stopword list. If possible, the stopword list should be reported by the resource name in the software package or by an URI (see example below). If this is not possible, it should meet the naming conventions below, e.g., by naming the corresponding `retrieval toolkit`.  
**Type:** Scalar  
**Encoding:** [UTF-8](https://www.unicode.org/main.html) encoded string of characters ([RFC3629](https://www.ietf.org/rfc/rfc3629.txt)); `!!str`.    
**Naming convention**: `Indri`, `Lucene`, `Smart`, `Terrier`, ...  
- `method` &rarr; `retrieval`  
**Description:** The retrieval approach is documented by a sequence of mappings, where each mapping represents one component of a ranking pipeline, i.e., it is also possible to report multi-stage ranking pipelines by referring to previous ranking stages.  
**Type:** Sequence of mappings; `!!seq [!!map, !!map, ...]`.  
- `method` &rarr; `retrieval` &rarr; `name`  
**Description:** Name of the ranking stage component.  
**Type:** Scalar  
**Encoding:** [UTF-8](https://www.unicode.org/main.html) encoded string of characters ([RFC3629](https://www.ietf.org/rfc/rfc3629.txt)); `!!str`.    
**Naming convention:**  `bm25`, `rm3`, `ax` (axiomatic reranking), `piv` (pivoted normalization method), `dir` (Dirichlet prior method), `monobert`  
- `method` &rarr; `retrieval` &rarr; `method`  
**Description:** Class name of the retrieval method.  
**Type:** Scalar  
**Encoding:** [UTF-8](https://www.unicode.org/main.html) encoded string of characters ([RFC3629](https://www.ietf.org/rfc/rfc3629.txt)); `!!str`.    
- `method` &rarr; `retrieval` &rarr; `params`  
**Description:** Parameter(s) of the retrieval method. Depending on the parameter, a single mapping is defined by the parameter name and a decimal integer or floating number.    
**Type:** Scalar    
**Encoding:** A decimal integer or floating point number; `!!int` or `!!float`.  
- `method` &rarr; `retrieval` &rarr; `reranks`  
**Description:** Name of the component whose output will be reranked.  
**Type:** Scalar  
**Encoding:** [UTF-8](https://www.unicode.org/main.html) encoded string of characters ([RFC3629](https://www.ietf.org/rfc/rfc3629.txt)); `!!str`.    
- `method` &rarr; `retrieval` &rarr; `interpolates`  
**Description:** Name of the component whose output will be reranked.   
**Type:** Sequence of scalars; `!!seq`.    
**Encoding:** [UTF-8](https://www.unicode.org/main.html) encoded string of characters ([RFC3629](https://www.ietf.org/rfc/rfc3629.txt)); `!!str`.    
- `method` &rarr; `retrieval` &rarr; `weight`  
**Description:** Interpolation weight.   
**Type:** Scalar  
**Encoding:** A decimal integer or floating point number; `!!int` or `!!float`.  

## Example

```YAML
method:
  automatic: true
  indexing:
    tokenizer: org.apache.lucene.analysis.en.StandardTokenizer
    stemmer: org.apache.lucene.analysis.en.PorterStemFilter
    stopwords: org.apache.lucene.analysis.standard.StandardAnalyzer.STOP_WORDS_SET
  retrieval:
  - name: bm25
    method: org.apache.lucene.search.similarities.Similarity.BM25Similarity
    b: 0.4
    k1: 0.9
  - name: axiomatic reranker
    method: io.anserini.rerank.lib.AxiomReranker
    rerankCutoff: 20
    axiom.deterministic: true
    reranks: bm25
  - name: lr reranker
    method: sklearn.linear_model.LogisticRegression
    reranks: axiomatic reranker
  - name: svm reranker
    method: sklearn.svm.SVC
    reranks: axiomatic reranker
  - name: lgb reranker
    method: lightgbm
    reranks: axiomatic reranker
  - name: ensemble
    ensembles:
    - lr reranker
    - svm reranker
    - lgb reranker
  - name: interpolation
    weight: 0.6
    interpolates:
    - axiomatic reranker
    - ensemble
```
