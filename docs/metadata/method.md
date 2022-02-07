# Method

The metadata information about the **Method** should include if the run is automatic or manual, i.e., derived with our without a human-in-the-loop approach, and information regarding the indexing and retrieval. While the indexing is usually composed of several processing steps including tokenization, stemming, and stopword removal, the retrieval method assign scores between a query and a document. Modern retrieval pipelines are often realized in the form of a multi-stage ranking that is supported by our metadata schema as well. If an additional ranking method reranks the output of a previous retrieval method, it can be reported by the `reranks` entry that refers to the name of the previous method. Likewise, it is possible to report interpolated scores.

## Checklist

- `method` &rarr; `automatic`
- `method` &rarr; `indexing` &rarr; `tokenizer`
- `method` &rarr; `indexing` &rarr; `stemmer`
- `method` &rarr; `indexing` &rarr; `stopwords`
- `method` &rarr; `retrieval` &rarr; `name`
- `method` &rarr; `retrieval` &rarr; `method`
- `method` &rarr; `retrieval` &rarr; `params`
- `method` &rarr; `retrieval` &rarr; `reranks`
- `method` &rarr; `retrieval` &rarr; `weight`
- `method` &rarr; `retrieval` &rarr; `interpolates`

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
