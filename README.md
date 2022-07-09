# tdaverse

## Mission

Topological data analysis (TDA) relies heavily on mature libraries like [PHAT](https://bitbucket.org/phat-code/phat/src/master/), [Dionysus](https://www.mrzv.org/software/dionysus/), and [GUDHI](https://gudhi.inria.fr/).
While these libraries have interfaces to Python and, through [the {TDA} package](https://cran.r-project.org/package=TDA), R, they have been developed primarily by and for statistical topologists.
As TDA matures and standard workflows emerge, the need arises for more accessible and modular implementations.
The [SciKit-TDA](https://scikit-tda.org/) project, an extension of SciPy, is underway in Python for this purpose. The **tdaverse** collection is intended to meet these needs in R through a [tidyverse](https://www.tidyverse.org/) lens.
The tidyverse consists of numerous R packages that are built upon a shared set of syntactic and grammatical conventions and designed to interface naturally with each other.
With its sibling collections [r-lib](https://github.com/r-lib) and [tidymodels](https://www.tidymodels.org/), it provides a comprehensive toolkit for building advanced data analysis and modeling pipelines.

## Vision

The goal of **tdaverse** is to provide the data structures, computational engines, statistical models, and visualization tools needed to efficiently explore and analyze topological data in R and to integrate these tasks into tidyverse workflows.

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

#### {tdaunif}

- Implement (partial) Latin hypercube sampling for sample remainder when using area-preserving maps ([issue 31](https://github.com/corybrunson/tdaunif/issues/31))
- Write samplers from compact matrix groups ([issue 24](https://github.com/corybrunson/tdaunif/issues/24))

#### {simplextree}

- Reconcile v1.0.2 with {Mapper}
- Compute simplicial homology

#### {interplex}

- Add methods for simplicial filtrations ([issue 3](https://github.com/corybrunson/interplex/issues/3))

#### {ripserr}

- Recover representative cocycles and cycles ([issue 26](https://github.com/rrrlw/ripserr/issues/26))

#### {TDAstats}

- Replace spinoff functionality with dependencies
    - {ripserr}
    - {ggtda}
- New methods
    - Write `print()` and `summary()` methods for tests (cf. base R statistical tests)
    - Write {broom} `tidy()` and `glance()` methods

### Incubating packages

#### {landmark}

- Write a more efficient C++ implementation

#### {Mapper}

- Reconcile branch [`simplextree-0.9.1`](https://github.com/corybrunson/Mapper/tree/simplextree-0.9.1) with {simplextree} v1.0.2
- New features
    - Add public method to subset data indices or rows of a lens cover set or a pullback cover set
    - Add color bars to annotated plots
- Replace ball and neighborhood covers with {landmark} dependencies
- Implement other validated clustering methods

#### {ggtda}

- Write new layers
    - persistent terraces
    - persistent images
- Write `fortify()` and/or `autoplot()` methods for 'PHom' class and {TDAstats} test and model classes

### Conceived packages

#### {Cover}

- Spinoff the `CoverRef` class and nerve constructors from {Mapper}
- Add support for towers of covers

#### {reebit}?

- Interface to Tu, Hajij, & Rosen's Java program [`ReebGraphPairing`](https://github.com/USFDataVisualization/ReebGraphPairing) by way of [{rJava}](https://rforge.net/rJava/)
- Return extended persistence data in class 'PHom'
- Ensure that hex sticker includes a frog

#### {perrrsist}? | {filtratr}?

- Construct filtrations from point clouds (coordinate matrices or distance objects)
    - Introduce S3 class 'SimplicialFiltration' and subclasses
- Prepare recipes for constructing filtrations
- Write `cut()` method for filtration classes (generalization of method for class 'hclust')

#### {morphom}?

- Collect common or validated transformations of persistence data
    - [Persistence images](https://jmlr.org/papers/v18/16-337.html)
    - Persistence landscapes (interface to [Dłotko & Bubenik's C++ toolbox](https://www2.math.upenn.edu/~dlotko/persistenceLandscape.html))
    - [Feature curves](https://aapm.onlinelibrary.wiley.com/doi/abs/10.1002/mp.15255)

#### {tidyplex}

- Create wrapper class 'tbl_plex' for simplicial complex objects
    - Activate one dimension at a time, à la [{tidygraph}](https://tidygraph.data-imaginist.com/)'s 'tbl_graph'
    - Manipulate & annotate simplicial complexes à la [{ordr}](https://corybrunson.github.io/ordr/)'s 'tbl_ord'

#### {phoment}?

- [{recipes}](https://recipes.tidymodels.org/) [extension](https://www.tidyverse.org/blog/2022/05/recipes-update-05-20222/) for vectorizations of persistence data
    - persistence images
    - persistence landscapes
    - persistence curves

## People

### Contribute

To learn more and contribute to package design or development, please visit the GitHub repositories and consider commenting on or creating an issue!

### Coordinators

- **Raoul R. Wadhwa** (Cleveland Clinic Lerner College of Medicine, Case Western Reserve University)
- **Matt Piekenbrock** (Khoury College of Computer Sciences, Northeastern University)
- **Jason Cory Brunson** (Laboratory for Systems Medicine, Division of Pulmonary, Critical Care, and Sleep Medicine, University of Florida)
