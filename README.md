# tdaverse

## Motivation

Topological data analysis (TDA) relies heavily on mature libraries like [PHAT](https://bitbucket.org/phat-code/phat/src/master/), [Dionysus](https://www.mrzv.org/software/dionysus/), and [GUDHI](https://gudhi.inria.fr/).
While these libraries have interfaces to Python and, through [the {TDA} package](https://cran.r-project.org/package=TDA), R, they have been developed primarily by and for statistical topologists.
As TDA matures and standard workflows emerge, the need arises for more accessible and modular implementations.
The [SciKit-TDA](https://scikit-tda.org/) project, an extension of SciPy, is underway in Python for this purpose. The **tdaverse** collection is intended to meet these needs in R through a [tidyverse](https://www.tidyverse.org/) lens.

The tidyverse consists of numerous R packages that are built upon a shared set of syntactic and grammatical conventions and designed to interface naturally with each other.
With its sibling collections [r-lib](https://github.com/r-lib) and [tidymodels](https://www.tidymodels.org/), it provides a comprehensive toolkit for building advanced data analysis and modeling pipelines.
The goal of **tdaverse** is to provide the data structures, computational engines, statistical models, and visualization tools needed to efficiently explore and analyze topological data in R and to integrate these tasks into tidy workflows.

## Packages

### Published packages

#### interplex

Inspired by [{intergraph}](https://github.com/mbojan/intergraph), the {interplex} package provides coercers between different data structures that encode simplicial complexes, and also converts between these and graph and network structures (with the loss of 2- and higher-dimensional simplices).

This package will enable tdaverse users to couple functionality from other packages into their workflows, for example layout algorithms from {igraph} and simplicial filtrations from [GUDHI](https://gudhi.inria.fr/) (via {reticulate}).

* [GitHub](https://github.com/corybrunson/interplex)
* [CRAN](https://cran.r-project.org/package=interplex)

#### simplextree

{simplextree} is an R package aimed at simplifying computation for simplicial complexes. The package provides R bindings to a simplex tree data structure implemented in C++11 and exported as an Rcpp module. Instances can be created from abstract or geometric data and exported and imported via serialization, and they can be efficiently inspected, queried, modified, and traversed using both Rcpp and S3 methods. The underlying library implementation also exports a C++ header, which can be specified as a dependency and used in other packages via {Rcpp} attributes.

simplextree will interface with other packages for various tasks: to sample geometric complexes based on arbitrary manifolds with {tdaunif}, to construct and update the nerves of mappers in {Mapper}, and to perform computations involving simplicial complexes stored in other formats via {interplex}.

* [GitHub](https://github.com/peekxc/simplextree/)
* [CRAN](https://cran.r-project.org/package=simplextree)

#### ripserr

{ripserr} ports the Ripser and Cubical Ripser persistent homology computational engines from C++ via Rcpp. It can be used as a convenient and efficient tool in TDA pipelines involving point cloud data (Risper) or image and volume data (Cubical Ripser).

ripserr is designed as a minimal standalone package and will be called to compute persistence data when underlying simplicial filtrations are not needed.

* [GitHub](https://github.com/rrrlw/ripserr)
* [CRAN](https://cran.r-project.org/package=ripserr)

#### TDAstats

Persistent homology can be used in hypothesis testing to compare the topological structure of two point clouds. {TDAstats} uses a permutation test in conjunction with the Wasserstein metric for nonparametric statistical inference.

TDAstats was originally designed with three goals in mind: the calculation, statistical inference, and visualization of persistent homology. Since its release, calculation has been moved to engine ports like {risperr} and {ggplot2}-style visualization has been moved to {ggtda}. Ongoing development of TDAstats will focus on statistical inference.

* [GitHub](https://github.com/rrrlw/tdastats)
* [CRAN](https://cran.r-project.org/package=TDAstats)

#### tdaunif

Methods for detecting topological structure from point cloud data sets are often validated by applying them to point clouds sampled from spaces with known topology. Functions that generate such samples are therefore valuable to developers of topological–statistical software. The goal of {tdaunif} is to assemble a comprehensive collection of such samplers for convenient use.

In addition testing TDA software, tdaunif will be used with {simplextree} to generate geometric random simplicial complexes and on its own as an educational tool for the study of ≥3-dimensional manifolds.

* [GitHub](https://github.com/corybrunson/tdaunif/)
* [CRAN](https://cran.r-project.org/package=tdaunif)

### Incubating packages

#### landmark

The {landmark} package provides functions to calculate landmark sets for finite metric spaces using the maxmin procedure (for fixed-radius balls) or an adaptation of it for rank data (for roughly fixed-cardinality nearest neighborhoods). These procedures can also return membership lists for the covers centered at these landmark sets. These covering method engines will be invoked by {Mapper} and other arbitrary cover–based constructions.

* [GitHub](https://github.com/corybrunson/landmark)

#### Mapper

The {Mapper} package provides a set of tools for computing the mapper construction.
Previous versions of this package included the simplex tree class and the maxmin procedure, which have been or are being spun off and expanded as the {simplextree} and {landmark} packages.

* [GitHub](https://github.com/peekxc/Mapper/)
* [simplextree-0.9.1 devel](https://github.com/corybrunson/Mapper/tree/simplextree-0.9.1)

#### ggtda

The {ggtda} package provides {ggplot2} layers (statistical transformations and geometric elements) and themes for publication-quality plots of data arising from topological objects and models. Persistent homology can be computed for continuous functions and Reeb graphs as well as point clouds, and ggtda layers are in development for numerous plot types that have been proposed to gain insight from persistence data. In addition, ggtda also provides layers to conveniently plot ball covers, Vietoris–Rips complexes, and Čech complexes for 2-dimensional point clouds.

* [GitHub](https://github.com/rrrlw/ggtda/)

### Conceived packages

#### Cover

Covers of data sets are ubiquitous in lower-level topological methods, including mapper-like constructions.
In order to allow more flexible implementations, the object-oriented package {Cover} would spin off the `CoverRef` R6 class from {Mapper} and introduce tools for efficiently storing and analyzing towers and other aggregates of covers.

#### reebit

Reeb graphs can be represented as graphs with height or value attributes, but few methods are available to perform basic computations like critical point pairing.
For starters, an R wrapper of the [ReebGraphPairing](https://github.com/USFDataVisualization/ReebGraphPairing) Java program could produce (extended) persistent homology for downstream analysis.

#### perrrsist / filtratr

A great advantage of [GUDHI](https://gudhi.inria.fr/) is the ability to work directly with simplicial filtrations, including to construct them from raw data and to compute persistent data from them.
{ripserr} sidesteps these objects, but they can be performed using {TDA}.
The idea for this package is to port different engines for computing and processing filtrations, analogously to [{parsnip}](https://github.com/tidymodels/parsnip).

#### morphom

A variety of vectorizations for persistence data have been proposed and validated, often to achieve stability properties.
This package would consolidate them.

#### tidyplex

Analogous to [{tidygraph}](https://github.com/thomasp85/tidygraph), this package would provide a "tidy" API to print, summarize, annotate, and perhaps visualize simplicial complexes and filtrations.

#### phoment

This package would wrap the vectorizations of {morphom} into a set of preprocessing steps for use with [{recipes}](https://github.com/tidymodels/recipes).

## People

### Contribute

To learn more and contribute to package design or development, please visit the GitHub repositories and consider commenting on or creating an issue!
Or check [this list of low-, medium-, and high-hanging fruit](objectives.md).

### Coordinators

- **Raoul R. Wadhwa** (Cleveland Clinic Lerner College of Medicine, Case Western Reserve University)
- **Matt Piekenbrock** (Khoury College of Computer Sciences, Northeastern University)
- **Jason Cory Brunson** (Laboratory for Systems Medicine, Division of Pulmonary, Critical Care, and Sleep Medicine, University of Florida)
