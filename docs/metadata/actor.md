# Actor

The metadata information about the **Actor** should include all available public information about the experimenter who actually executed the software of the experiments. Often this person is hidden behind the co-authorship and the metadata should report how to reach the experimenter for further questions. The `role` identifies if the authors is the original `experimenter` or the `reproducer` of a run/experiment.

## Checklist

- `actor` &rarr; `name`  
**Description:**  
Name of the Actor.  
**Type:**  
*Scalar*; usually a string of characters
- `actor` &rarr; `orcid`  
**Description:**  
[ORCID](https://orcid.org/) of the Actor.  
**Type:**  
*Scalar*; usually a string of characters
- `actor` &rarr; `team`  
**Description:**  
Team name of which the Actor is part of.  
**Type:**  
*Scalar*; usually a string of characters
- `actor` &rarr; `fields`  
**Description:**  
List of the Actor's research fields.  
**Type:**  
*Sequence of scalars*; usually a listing of strings
- `actor` &rarr; `mail`  
**Description:**  
Mail address of the Actor.  
**Type:**  
*Scalar*; usually a string of characters
- `actor` &rarr; `role`  
**Description:**  
Role of the Actor. Can be `experimenter` if the original experiment is conducted or `reproducer` if the experiment is reproduced.  
**Type:**  
*Scalar*; usually a string of characters
- `actor` &rarr; `degree`  
**Description:**  
The academic degree of the Actor, e.g., `B.Sc.`, `M.Sc.`, or `Ph.D.`  
**Type:**  
*Scalar*; usually a string of characters
- `actor` &rarr; `github`  
**Description:**  
[GitHub](https://www.github.com/) handle of the Actor.  
**Type:**  
*Scalar*; usually a string of characters
- `actor` &rarr; `twitter`  
**Description:**  
[Twitter](https://www.twitter.com/) handle of the Actor.  
**Type:**  
*Scalar*; usually a string of characters

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
