<p align="center">
  <img src="https://github.com/diegosasso/workshop_evolution2023/blob/main/wiki_figures/ontophylo.png" width = "300">
</p>

## OntoPhylo Workflow

*OntoPhylo* (Porto et al. [2023](https://www.biorxiv.org/content/10.1101/2023.06.13.544734v1)) implements the PARAMO pipeline (Tarasov et al. [2019]( https://doi.org/10.1093/isd/ixz009)) in R and expands it by allowing researchers to make different types of inferences from stochastic maps of amalgamated characters. The PARAMO pipeline consists of two main steps: (1) character annotation and coding; and (2) stochastic mapping and ontology-informed character amalgamation. The different types of inferences are implemented in three applications: (1) inferring evolutionary rates on branches; (2) reconstructing morphospace dynamics; and (3) assessing rates of anatomical entities at different levels of the anatomical hierarchy.

<p align="center">
  <img src="https://github.com/diegosasso/workshop_evolution2023/blob/main/wiki_figures/Figure_pipeline.png" width = "1000">
</p>

## Phylogenetic characters and ontologies
Phylogenetic character matrices have several character statements, each of them often referring to a distinct anatomical entity. For example, the character statement “mandible: (0) curved or (1) straight” refers to the entity `mandible`. Organismal anatomy is hierarchical and thus anatomical entities can be grouped at many different levels. Furthermore, anatomical entities are often structurally associated (e.g., an insect mandible is part of the mouthparts; mouthparts are part of the head), thus resulting in dependencies among characters (see Vogt [2018](https://doi.org/10.1111/cla.12209) for a review on types of dependencies). Anatomy ontologies offer an alternative solution to represent morphological data in phylogenetics. They are structured controlled vocabularies allowing knowledge in a particular domain (e.g., insect morphology) to be represented as a graph of logically-defined concepts. In simpler words, we can easily describe the hierarchy of anatomical concepts, including their dependencies, using ontologies.

## STEP 1. Character annotation and coding
Character annotation is the process of linking the anatomical entity of a character statement to a particular term in an ontology. For example, the `mandible` of a hymenopteran insect can be linked to the term [HAO_0000506](http://purl.obolibrary.org/obo/HAO_0000506) in the Hymenoptera Anatomy Ontology (HAO) (Yoder et al. [2010]( https://doi.org/10.1371/journal.pone.0015991)). By linking each character statement to a particular ontology term, we can easily group characters based on their annotations exploring *part_of* relations expressed in the ontology. For example, we can group all characters that are part of `head` ([HAO_0000397](http://purl.obolibrary.org/obo/HAO_0000397)) or `mouthparts` ([HAO_0000639](http://purl.obolibrary.org/obo/HAO_0000639)). Annotations can be done manually or using semi-automatic tools, such as those available in the *ontoFAST* package (Tarasov et al. [2022]( https://doi.org/10.1111/2041-210X.13753) ). Character annotation is described in detail in **Tutorial 1**.

For the purposes of the PARAMO pipeline, all characters are assumed to be independent. As discussed above, however, this is often not true for many characters due to anatomical dependencies. In such cases, dependent characters should be merged and recoded before moving to STEP 2. A more detailed discussion on how to code dependent/inapplicable characters can be found elsewhere (e.g., Tarasov [2019](https://doi.org/10.1093/sysbio/syz005), [2020](https://doi.org/10.1093/sysbio/syz050), [2023](https://doi.org/10.1093/sysbio/syad005); Simões et al. [2023](https://doi.org/10.1093/sysbio/syad006)). In the example data sets used in the tutorials, selected characters have no dependencies.

## STEP 2. Stochastic mapping and character amalgamation
The PARAMO pipeline is presented in detail by Tarasov et al. [2019]( https://doi.org/10.1093/isd/ixz009). In summary, it consists of: (i) given a series of stochastic maps obtained from characters referring to multiple anatomical entities, (ii) use their ontology annotations to amalgamate maps based on a given query. The amalgamation is user-defined and depends on the researcher’s interest. For example, a researcher can amalgamate stochastic maps based on a selected anatomical region (e.g., retrieve all characters from `head`). The PARAMO pipeline is described in detail in **Tutorial 2**.

## APPLICATION 1. Estimating branch rates
*OntoPhylo* can infer evolutionary rates along branches and variation across lineages by using a non-homogeneous Poisson process (NHPP) to model trait evolution. In summary, NHPP can be reconstructed by estimating the density of transitions along branches and the overall number of transitions across the tree. Application 1 is described in detail in **Tutorial 3**.

## APPLICATION 2. Reconstructing morphospace dynamics
*OntoPhylo* can reconstruct the morphospace dynamics through time by applying a method of dimensionality reduction to multidimensional phenotypes present at different time slices and then stacking the resulting morphospaces to produce an animation. Application 2 is described in detail in **Tutorial 4**.

## APPLICATION 3. Assessing rates of different anatomical entities
*OntoPhylo* can link the layers of vector images annotated with ontology terms and color-code them based on the evolutionary rates of different anatomical entities or anatomical regions at different branches of the tree. Application 3 is described in detail in **Tutorial 5**
