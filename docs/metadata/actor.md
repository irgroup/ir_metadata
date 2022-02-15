# Actor

The **Actor** component represents the experimenter who conducts the experiments. The metadata information about the Actor should include all available public information about the experimenter who actually executed the software of the experiments. Often this person is hidden behind the co-authorship and the metadata should report how to reach the experimenter for further questions. The `role` identifies if the author is the original `experimenter` or the `reproducer` of a run/experiment.

## Checklist

- `actor` &rarr; `name`  
**Description:** Name of the Actor.  
**Type:** Scalar  
**Encoding:** [UTF-8](https://www.unicode.org/main.html) encoded string of characters according to [RFC3629](https://www.ietf.org/rfc/rfc3629.txt)
- `actor` &rarr; `orcid`  
**Description:** [ORCID](https://orcid.org/) of the Actor.    
**Type:** Scalar  
**Encoding:** [UTF-8](https://www.unicode.org/main.html) encoded string of characters according to [RFC3629](https://www.ietf.org/rfc/rfc3629.txt)
- `actor` &rarr; `team`  
**Description:** Team name of which the Actor is part of.  
**Type:** Scalar  
**Encoding:** [UTF-8](https://www.unicode.org/main.html) encoded string of characters according to [RFC3629](https://www.ietf.org/rfc/rfc3629.txt)
- `actor` &rarr; `fields`  
**Description:** List of the Actor's research fields.  
**Type:** Sequence of scalars  
**Encoding:** [UTF-8](https://www.unicode.org/main.html) encoded string of characters according to [RFC3629](https://www.ietf.org/rfc/rfc3629.txt)
- `actor` &rarr; `mail`  
**Description:** Mail address of the Actor.    
**Type:** Scalar  
**Encoding:** [UTF-8](https://www.unicode.org/main.html) encoded string of characters according to [RFC3629](https://www.ietf.org/rfc/rfc3629.txt)
- `actor` &rarr; `role`  
**Description:** Role of the Actor. Can be `experimenter` if the original experiment is conducted or `reproducer` if the experiment is reproduced.  
**Type:** Scalar  
**Encoding:** [UTF-8](https://www.unicode.org/main.html) encoded string of characters according to [RFC3629](https://www.ietf.org/rfc/rfc3629.txt)
- `actor` &rarr; `degree`  
**Description:** The academic degree of the Actor, e.g., `B.Sc.`, `M.Sc.`, or `Ph.D.`  
**Type:** Scalar  
**Encoding:** [UTF-8](https://www.unicode.org/main.html) encoded string of characters according to [RFC3629](https://www.ietf.org/rfc/rfc3629.txt)
- `actor` &rarr; `github`  
**Description:** URL with the [GitHub](https://www.github.com/) handle of the Actor.  
**Type:** Scalar  
**Encoding:** URI according to [RFC2396](https://www.ietf.org/rfc/rfc2396.txt)    
- `actor` &rarr; `twitter`  
**Description:** URL with the [Twitter](https://www.twitter.com/) handle of the Actor.    
**Type:** Scalar  
**Encoding:** URI according to [RFC2396](https://www.ietf.org/rfc/rfc2396.txt)    

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
