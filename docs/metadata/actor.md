# Actor

The metadata information about the **Actor** should include all available public information about the experimenter who actually executed the software of the experiments. Often this person is hidden behind the co-authorship and the metadata should report how to reach the experimenter for further questions. The `role` identifies if the authors is the original `experimenter` or the `reproducer` of a run/experiment.

## Checklist

- `actor` &rarr; `name` 
- `actor` &rarr; `orcid` 
- `actor` &rarr; `team` 
- `actor` &rarr; `fields` 
- `actor` &rarr; `mail`
- `actor` &rarr; `role` 
- `actor` &rarr; `degree` 
- `actor` &rarr; `github` 
- `actor` &rarr; `twitter` 

## Example

```YAML
actor:
  name: Jimmy Lin
  orcid: 0000-0002-0661-7189
  team: h2oloo
  fields:
  - nlp
  - ir
  - databases
  - large-scale distributed algorithms
  - data analytics
  mail: jimmylin@uwaterloo.ca
  role: reproducer
  degree: Ph.D.
  github: https://github.com/lintool
  twitter: https://twitter.com/lintool
```
