# Platform

The **Platform** comprises the hard- and software underlying the actual [Implementation](../implementation). The metadata information about the Platform should include the underlying hardware, the operating system, and the used software libraries. `software` covers every package or library that is used for the Implementation. If a retrieval toolkit is used, it should be reported explicitly.

## Checklist

- `platform` &rarr; `hardware` &rarr; `cpu` &rarr; `model`  
**Description:** Name of the CPU model.  
**Type:** Scalar  
**Encoding:** [UTF-8](https://www.unicode.org/main.html) encoded string of characters ([RFC3629](https://www.ietf.org/rfc/rfc3629.txt)); `!!str`.  
- `platform` &rarr; `hardware` &rarr; `cpu` &rarr; `architecture`  
**Description:** Identifier of the CPU architecture.  
**Type:** Scalar  
**Encoding:** [UTF-8](https://www.unicode.org/main.html) encoded string of characters ([RFC3629](https://www.ietf.org/rfc/rfc3629.txt)); `!!str`.  
- `platform` &rarr; `hardware` &rarr; `cpu` &rarr; `operation mode`  
**Description:** Operation mode of the CPU.  
**Type:** Scalar  
**Encoding:** [UTF-8](https://www.unicode.org/main.html) encoded string of characters ([RFC3629](https://www.ietf.org/rfc/rfc3629.txt)); `!!str`.  
- `platform` &rarr; `hardware` &rarr; `cpu` &rarr; `number of cores`  
**Description:** Number of CPU cores.  
**Type:** Scalar  
**Encoding:** A decimal integer number; `!!int`.    
- `platform` &rarr; `hardware` &rarr; `gpu` &rarr; `architecture`  
**Description:** Name of the GPU architecture.  
**Type:** Scalar  
**Encoding:** [UTF-8](https://www.unicode.org/main.html) encoded string of characters ([RFC3629](https://www.ietf.org/rfc/rfc3629.txt)); `!!str`.   
- `platform` &rarr; `hardware` &rarr; `gpu` &rarr; `number of cores`  
**Description:** Number of GPU cores.    
**Type:** Scalar  
**Encoding:** A decimal integer number; `!!int`.    
- `platform` &rarr; `hardware` &rarr; `gpu` &rarr; `memory`  
**Description:** Amount of available memory of the GPU; string with numbers followed by GB.  
**Type:** Scalar    
**Encoding:** [UTF-8](https://www.unicode.org/main.html) encoded string of characters ([RFC3629](https://www.ietf.org/rfc/rfc3629.txt)); `!!str`.  
- `platform` &rarr; `hardware` &rarr; `ram`   
**Description:** Amount of available RAM; string with numbers followed by GB.  
**Type:** Scalar  
**Encoding:** [UTF-8](https://www.unicode.org/main.html) encoded string of characters ([RFC3629](https://www.ietf.org/rfc/rfc3629.txt)); `!!str`. 
- `platform` &rarr; `operating system` &rarr; `kernel`  
**Description:** The kernel version of the operating system.  
**Type:** Scalar  
**Encoding:**  [UTF-8](https://www.unicode.org/main.html) encoded string of characters ([RFC3629](https://www.ietf.org/rfc/rfc3629.txt)); `!!str`.  
- `platform` &rarr; `operating system` &rarr; `distribution`   
**Description:** The name of the operating system's distribution.   
**Type:** Scalar  
**Encoding:** [UTF-8](https://www.unicode.org/main.html) encoded string of characters ([RFC3629](https://www.ietf.org/rfc/rfc3629.txt)); `!!str`.  
- `platform` &rarr; `software` &rarr; `libraries`  
**Description:** Names and versions of the software libraries and packages underlying the experiment's [Implementation](../implementation) with the following syntax `<libray-name>==<version>`. If possible, libraries and packages of different programming languages should be in separate nodes (see example below).   
**Type:** Sequence of scalars; `!!seq`.  
**Encoding:** [UTF-8](https://www.unicode.org/main.html) encoded string of characters ([RFC3629](https://www.ietf.org/rfc/rfc3629.txt)); `!!str`.  
- `platform` &rarr; `software` &rarr; `retrieval toolkit`  
**Description:** Names and versions of the retrieval toolkits underlying the experiment's [Implementation](../implementation) with the following syntax `<toolkit-name>==<version>`.  
**Type:** Sequence of scalars; `!!seq`.  
**Encoding:** [UTF-8](https://www.unicode.org/main.html) encoded string of characters ([RFC3629](https://www.ietf.org/rfc/rfc3629.txt)); `!!str`.    
**Naming convention:** `indri`, `terrier`, `anserini`, `pyserini`, `pyterrier`, `solr`, `elasticsearch`  

## Example

```YAML
platform:
  hardware:
    cpu:
      model: Intel(R) Xeon(R) Gold 6144 CPU @ 3.50GHz
      architecture: x86_64
      operation mode: 64-bit
      number of cores: 16
    gpu:
      model: NVIDIA RTX A6000
      memory: 48 GB
      number of cores: 10752
    ram: 32 GB
  operating system:
    kernel: GNU/Linux 4.15.0-166-generic
    distribution: Ubuntu 18.04.5 LTS
  software:
    libraries:
      python:
      - blas==1.0
      - libgfortran==3.0.1
      - libxml2==2.9.8
      - lightgbm==2.2.1
      - ncurses==6.1
      - numpy==1.15.4
      - numpy-base==1.15.4
      - scikit-learn==0.20.1
      - scipy==1.1.0
      - setuptools==40.6.2
      java:
      - lucene==7.6
    retrieval toolkit:
    - anserini==0.3.0
```
