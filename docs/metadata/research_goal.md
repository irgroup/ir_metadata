# Research goal

The **Research goal** describes the purpose of the study. The metadata information about the Research goal should include information about the venue for which the study was made, the corresponding publications, as well as some information about the evaluation. If the [Actor](../actor) is reported as `reproducer`, the `baseline` refers to the tag of the original run that is reimplemented, otherwise, it should be a strong and reasonable baseline if the [Actor](../actor) is the original `experimenter`.

## Checklist

- `research goal` &rarr; `venue` &rarr; `name`  
**Description:** Acronym (if available) or name of the venue (e.g. journal or conference) at which is the study is published.    
**Type:** Scalar  
**Encoding:** [UTF-8](https://www.unicode.org/main.html) encoded string of according to [RFC3629](https://www.ietf.org/rfc/rfc3629.txt)   
- `research goal` &rarr; `venue` &rarr; `year`  
**Description:** Year in which the study was published.  
**Type:** Scalar  
**Encoding:** A decimal integer number  
- `research goal` &rarr; `publication` &rarr; `dblp`  
**Description:** URL of the publication in the [dblp - computer science bibliography](https://dblp.uni-trier.de/).  
**Type:** Scalar  
**Encoding:** URI according to [RFC2396](https://www.ietf.org/rfc/rfc2396.txt)   
- `research goal` &rarr; `publication` &rarr; `doi`  
**Description:** DOI of the publication.  
**Type:** Scalar  
**Encoding:** URI according to [RFC2396](https://www.ietf.org/rfc/rfc2396.txt)  
- `research goal` &rarr; `publication` &rarr; `arxiv`  
**Description:** URL to the [arXiv](https://dblp.uni-trier.de/) publication.    
**Type:** Scalar  
**Encoding:** URI according to [RFC2396](https://www.ietf.org/rfc/rfc2396.txt)   
- `research goal` &rarr; `publication` &rarr; `url`  
**Description:** Custom URL where is the publication is hosted.    
**Type:** Scalar  
**Encoding:** URI according to [RFC2396](https://www.ietf.org/rfc/rfc2396.txt)   
- `research goal` &rarr; `publication` &rarr; `abstract`  
**Description:** Abstract of the publication.    
**Type:** Scalar  
**Encoding:** [UTF-8](https://www.unicode.org/main.html) encoded string of according to [RFC3629](https://www.ietf.org/rfc/rfc3629.txt)  
- `research goal` &rarr; `evaluation` &rarr; `reported_measures`  
**Description:** A list of measures that were evaluated. We propose to follow `trec_eval`'s naming convention of the measures.   
**Type:**  Sequence of scalars  
**Encoding:** [UTF-8](https://www.unicode.org/main.html) encoded string of according to [RFC3629](https://www.ietf.org/rfc/rfc3629.txt) 
- `research goal` &rarr; `evaluation` &rarr; `baseline`  
**Description:** The run tag of the baseline that is used in the experiments. If the [Actor](../actor) is the original `experimenter`, the baseline should be adequate and state-of-the-art. If the Actor is a `reproducer` the baseline refers to the run that is reproduced.  
**Type:** Sequence of scalars  
**Encoding:** [UTF-8](https://www.unicode.org/main.html) encoded string of according to [RFC3629](https://www.ietf.org/rfc/rfc3629.txt) 
- `research goal` &rarr; `evaluation` &rarr; `significance test`  
**Description:** Significance tests that were used as part of the experimental evaluations. If required the corresponding correction method should be reported as well.    
**Type:** Sequence of mappings  
**Encoding:**  [UTF-8](https://www.unicode.org/main.html) encoded string of according to [RFC3629](https://www.ietf.org/rfc/rfc3629.txt)

## Example

```YAML
research goal:
  venue:
    name: ECIR
    year: 2019
  publication:
    dblp: https://dblp.org/rec/conf/ecir/YuXL19
    doi: https://doi.org/10.1007/978-3-030-15712-8_26
    url: https://cs.uwaterloo.ca/~jimmylin/publications/Yu_etal_ECIR2019.pdf
    abstract: We tackle the problem of transferring relevance judgments across document collections for specific information needs by reproducing and generalizing the work of Grossman and Cormack from the TREC 2017 Common Core Track. Their approach involves training relevance classifiers using human judgments on one or more existing (source) document collections and then applying those classifiers to a new (target) document collection. Evaluation results show that their approach, based on logistic regression using word-level tf-idf features, is both simple and effective, with average precision scores close to human-in-the-loop runs. The original approach required inference on every document in the target collection, which we reformulated into a more efficient reranking architecture using widely-available open-source tools. Our efforts to reproduce the TREC results were successful, and additional experiments demonstrate that relevance judgments can be effectively transferred across collections in different combinations. We affirm that this approach to cross-collection relevance feedback is simple, robust, and effective.
  evaluation:
    reported measures:
    - map
    - P_10
    baseline:
    - WCrobust04
    significance test:
      - name: t-test
        correction method: bonferroni
```
