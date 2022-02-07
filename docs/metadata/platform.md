# Platform

The metadata information about the **Platform** should include the underlying hardware, the operating system, and the used software libraries. `software` covers every package or library that is used for the [Implementation](../implementation). If a retrieval toolkit is used, it should be reported explicitly.

## Checklist

- `platform` &rarr; `hardware` &rarr; `cpu` &rarr; `model`
- `platform` &rarr; `hardware` &rarr; `cpu` &rarr; `architecture` 
- `platform` &rarr; `hardware` &rarr; `cpu` &rarr; `operation mode`
- `platform` &rarr; `hardware` &rarr; `cpu` &rarr; `number of cores`
- `platform` &rarr; `hardware` &rarr; `gpu` &rarr; `architecture`
- `platform` &rarr; `hardware` &rarr; `gpu` &rarr; `number of cores`
- `platform` &rarr; `hardware` &rarr; `gpu` &rarr; `ram`
- `platform` &rarr; `hardware` &rarr; `ram` 
- `platform` &rarr; `operating system` &rarr; `kernel` 
- `platform` &rarr; `operating system` &rarr; `distribution` 
- `platform` &rarr; `software` &rarr; `libraries` 
- `platform` &rarr; `software` &rarr; `retrieval toolkit` 

## Example

```YAML
platform:
  hardware:
    cpu:
      model: Intel(R) Xeon(R) Gold 6144 CPU @ 3.50GHz
      architecture: x86_64
      operation mode: 64-bit
      number of cores: 16
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
