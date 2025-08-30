## Objectives

The following are high priorities across the tdaverse.
See the issues at the respective repositories for other desiderata!

### Across all packages

- Standardize {roxygen2} + {rmarkdown} documentation
- Ensure consistent naming conventions for functions, parameters, etc.
    - Use simple whole words, e.g. `dimension` rather than `dim` and `max_dim`
- Write vignettes to illustrate couplings of multiple packages
    - Encourage natural pipelines using `%>%` or `|>`

### Published packages

#### [{tdaunif}](https://corybrunson.github.io/tdaunif/)

- Implement (partial) Latin hypercube sampling for sample remainder when using area-preserving maps ([issue 31](https://github.com/corybrunson/tdaunif/issues/31))
- Write samplers from compact matrix groups ([issue 24](https://github.com/corybrunson/tdaunif/issues/24))

#### [{simplextree}](https://github.com/peekxc/simplextree/)

- Reconcile v1.0.2 with {Mapper}

#### [{interplex}](https://github.com/corybrunson/interplex)

- Add methods for simplicial filtrations ([issue 3](https://github.com/corybrunson/interplex/issues/3))

#### [{ripserr}](https://github.com/rrrlw/ripserr/)

- Recover representative cocycles and cycles ([issue 26](https://github.com/rrrlw/ripserr/issues/26))

#### [{TDAstats}](https://rrrlw.github.io/TDAstats/)

- New methods
    - Write `print()` and `summary()` methods for tests (cf. base R statistical tests)
    - Write [{broom}](https://broom.tidymodels.org/) `tidy()` and `glance()` methods

### Incubating packages

#### [{landmark}](https://github.com/corybrunson/landmark)

- Write a more efficient C++ implementation of lastfirst

#### [{Mapper}](https://peekxc.github.io/Mapper/)

- Reconcile branch [`simplextree-0.9.1`](https://github.com/corybrunson/Mapper/tree/simplextree-0.9.1) with {simplextree} v1.0.2
- New features
    - Add public method to subset data indices or rows of a lens cover set or a pullback cover set
    - Add color bars to annotated plots
- Replace ball and neighborhood covers with {landmark} dependencies
- Implement other validated clustering methods

### Conceived packages

#### {Cover}

- Spinoff the `CoverRef` class and nerve constructors from {Mapper}
- Add support for towers of covers

#### {perrrsist}? | {filtratr}?

- Construct filtrations from point clouds (coordinate matrices or distance objects)
    - Introduce S3 class 'SimplicialFiltration' and subclasses
- Prepare recipes for constructing filtrations
    - Engines: Risper via {ripserr}, PHAT, Dionysus, GUDHI via {TDA}
- Write `cut()` method for filtration classes (generalization of method for class 'hclust')

#### {tidyplex}

- Create wrapper class 'tbl_plex' for simplicial complex objects
    - Activate one dimension at a time, à la [{tidygraph}](https://tidygraph.data-imaginist.com/)'s 'tbl_graph'
    - Manipulate & annotate simplices à la [{ordr}](https://corybrunson.github.io/ordr/)'s 'tbl_ord'

#### mapper meta-package

- coordinate installation/attachment of mapper-related packages
    - {landmark}
    - {simplextree}
    - {Cover}
    - {Mapper}
    - {reebit}
    - {interplex}
    - {tidyplex}

#### persistent homology meta-package

- coordinated installation/attachment of PH-related packages
    - {ripserr}
    - {perrrsist}/{filtratr}
    - {morphom}
    - {phoment}
    - {TDAstats}

### Trans-package objectives

A [CRAN Task View](https://cran.rstudio.com/web/views/) for computational topology and topological data analysis may be in order.
See [this guide to proposing a new CRAN task view](https://github.com/cran-task-views/ctv/blob/main/Proposal.md).
