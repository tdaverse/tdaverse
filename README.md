# tdaverse

## Mission



## Vision



## Desiderata

### Across all packages

- Ensure consistent naming conventions for functions, parameters, etc.
    - Use whole words, e.g. `dimension` rather than `dim`
- Write vignettes to illustrate package couplings

### {tdaunif}

- Implement (partial) Latin hypercube sampling for sample remainder when using area-preserving maps

### {landmark}

### {simplextree}

- Compute simplicial homology

### {interplex}

### {Cover}

- Spinoff the `CoverRef` class from {Mapper}

### {Mapper}

- Reconcile with {simplextree} 1.0.2
- Add public method to subset data indices or rows of a lens cover set or a pullback cover set
- Add color bars to annotated plots
- Replace ball and neighborhood covers with {landmark} dependencies

### {reebit}? | {reebbit}?

- Interface to Tu, Hajij, & Rosen's `ReebGraphPairing` (Java)
- Ensure that hex sticker includes a frog

### {ripserr}

- Recover representative cycles
- Make `print.PHom()` more tibble-esque?

### {perrrsist}? | {filtr}?

- Construct filtrations from point clouds (coordinate matrices or distance objects)
    - Introduce S3 class 'SimplicialFiltration' and subclasses
- Prepare recipes for constructing filtrations
- Write `cut()` method for filtration classes

### {TDAstats}

- Replace spinoff functionality with dependencies
    - {ripserr}
    - {ggtda}
- Write `print()` methods analogous to those for base R statistical tests
    - Write {broom} `tidy()` and `glance()` methods
- Write function to calculate persistent images

### {phomland}?

- Build an R interface to Dłotko & Bubenik's persistence landscapes toolbox (C++)

### {ggtda}

- Write new layers
    - persistent terraces
    - persistent images (call {perrrsist})
- Write `fortify()` and/or `autoplot()` methods for 'PHom' class

### {tidyplex}

- Create wrapper class 'tbl_plex' for simplicial complex objects
    - Activate one dimension at a time, à la {tidygraph}
    - Manipulate & annotate simplicial complexes à la {ordr}
