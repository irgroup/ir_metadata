# Method

The metadata information about the **Method** should include if the run is automatic or manual, i.e., derived with or without a human-in-the-loop approach, and information regarding the indexing and retrieval. While the indexing is usually composed of several processing steps including tokenization, stemming, and stopword removal, the retrieval method assigns scores between a query and a document. Modern retrieval pipelines are often realized in the form of a multi-stage ranking that is supported by our metadata schema as well. If an additional ranking method reranks the output of a previous retrieval method, it can be reported by the `reranks` entry that refers to the name of the previous method. Likewise, it is possible to report interpolated scores.

## Checklist

- `method` &rarr; `automatic`  
**Description:**  
Boolean value indicating if it is a automatic (`true`) or manual (`false`) run.   
**Type:**  
*Boolean*; `true` if automatic, `false` if manual
- `method` &rarr; `score ties`  
**Description:**  
Name of the method used to break score ties in the ranking.  
**Type:**  
*Scalar*; usually a string of characters
- `method` &rarr; `indexing` &rarr; `tokenizer`  
**Description:**  
Name of the tokenizer.   
**Type:**  
*Scalar*; usually a string of characters
- `method` &rarr; `indexing` &rarr; `stemmer`  
**Description:**  
Name of the stemmer.  
**Type:**  
*Scalar*; usually a string of characters
- `method` &rarr; `indexing` &rarr; `stopwords`  
**Description:**  
Name of the stopword list.  
**Type:**  
*Scalar*; usually a string of characters
- `method` &rarr; `retrieval`  
**Description:**  
Each mapping represents one component of a ranking pipeline, i.e., it is also possible to report multi-stage ranking pipelines by referring to previous ranking stages. The following scalars should be reported if required:  
`method` &rarr; `retrieval` &rarr; `name`: Name of the ranking stage component.  
`method` &rarr; `retrieval` &rarr; `method`: Name of the actual retrieval method.  
`method` &rarr; `retrieval` &rarr; `params`: Parameters of the retrieval method.  
`method` &rarr; `retrieval` &rarr; `reranks`: Name of the component whose output will be reranked.  
`method` &rarr; `retrieval` &rarr; `interpolates`: List of components whose output is interpolated.  
`method` &rarr; `retrieval` &rarr; `weight`:  Interpolation weight.   
**Type:**  
*Sequence of mappings*; one mapping represents one component in a multi-stage ranking pipeline


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
