# Research goal

The metadata information about the **Research goal** should include information about the venue for which the study was made, the corresponding publications, as well as some information about the evaluation. If the [Actor](../actor) is reported as `reproducer`, the `baseline` refers to the tag of the original run that is reimplemented, otherwise, it should be a strong and reasonable baseline if the [Actor](../actor) is the original `experimenter`.

## Checklist

- `research goal` &rarr; `venue` &rarr; `name`
- `research goal` &rarr; `venue` &rarr; `year`
- `research goal` &rarr; `publication` &rarr; `dblp` 
- `research goal` &rarr; `publication` &rarr; `doi` 
- `research goal` &rarr; `publication` &rarr; `arxiv` 
- `research goal` &rarr; `publication` &rarr; `url` 
- `research goal` &rarr; `publication` &rarr; `abstract` 
- `research goal` &rarr; `evaluation` &rarr; `reported_measures`
- `research goal` &rarr; `evaluation` &rarr; `baseline`
- `research goal` &rarr; `evaluation` &rarr; `significance test`&rarr; `name`
- `research goal` &rarr; `evaluation` &rarr; `significance test` &rarr; `correction method`

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
      - name: 't-test'
        correction method: 'bonferroni' 
```
