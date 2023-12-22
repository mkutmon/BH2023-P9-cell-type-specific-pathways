---
title: 'BioHackEU23 report: Cell type-specific and druggable pathway models and maps'
title_short: 'BioHackEU23 #9: Cell type-specific pathway maps'
tags:
  - single-cell data
  - pathway
  - disease maps
  - druggability
authors:
  - name: Marek Ostaszewski
    orcid: 0000-0003-1473-370X
    affiliation: 1
  - name: Martina Kutmon
    orcid: 0000-0002-7699-8191
    affiliation: 2
  - name: Naveed Ishaque
    orcid: 0000-0002-8426-901X
    affiliation: 3
  - name: Ahmed Hemedan
    orcid: 0000-0001-7403-181X
    affiliation: 1
  - name: Alessandro Brandulas Cammarata
    orcid: 0009-0006-5956-9842
    affiliation: 4,5
  - name: Frederic Bastian
    orcid: 0000-0002-9415-5104
    affiliation: 4,5
  - name: George Gavriilidis
    orcid: 0000-0003-2575-4354
    affiliation: 6
  - name: Hasan Balci
    orcid: 0000-0001-8319-7758
    affiliation: 2
  - name: Egon Willighagen
    orcid: 0000-0001-7542-0286
    affiliation: 2
  - name: Kim Vucinic
    orcid: 0009-0008-1553-1935
    affiliation: 7
  - name: Marina Esteban-Medina
    orcid: 0000-0003-2632-9587
    affiliation: 8
  - name: Kinza Rian
    orcid: 0000-0003-4314-7208
    affiliation: 8
  - name: Liya Zaygerman
    orcid: 0009-0005-4947-6223
    affiliation: 9
  - name: Matti Hoch
    orcid: 0000-0002-2486-0246
    affiliation: 10
  - name: Sabrina Jagot
    orcid: 0000-0002-6718-4794
    affiliation: 11
  - name: Sandra Ng
    orcid: 0000-0003-4524-6058
    affiliation: 12
  - name: Sara Pita
    affiliation: 13
affiliations:
  - name: University of Luxembourg, LU
    index: 1
  - name: Maastricht University, NL
    index: 2
  - name: Charite University Hospital, DE
    index: 3
  - name: Department of Ecology and Evolution, University of Lausanne, CH
    index: 4
  - name: SIB Swiss Institute of Bioinformatics, CH
    index: 5
  - name: Institute of Applied Biosciences, GR
    index: 6
  - name: Institute of Molecular Genetics of the Czech Academy of Sciences, CZ
    index: 7
  - name: Fundación Progreso y Salud, ES
    index: 8
  - name: Helmholtz Munich, DE
    index: 9
  - name: University of Rostock, DE
    index: 10
  - name: Université de Nantes, FR
    index: 11
  - name: Queen Mary University of London, UK
    index: 12
  - name: Technical University of Denmark, DK
    index: 13
date: 8 November 2023
cito-bibliography: paper.bib
event: BH23EU
biohackathon_name: "BioHackathon Europe 2023"
biohackathon_url:   "https://biohackathon-europe.org/"
biohackathon_location: "Barcelona, Spain, 2023"
group: Project 9
# URL to project git repo --- should contain the actual paper.md:
git_url: https://github.com/biohackrxiv/publication-template
# This is the short authors description that is used at the
# bottom of the generated paper (typically the first two authors):
authors_short: M. Ostaszewski, M. Kutmon, N. Ishaque \emph{et al.}
---

# Introduction

At the BioHackathon Europe 2023, our group developed workflows for streamlined discovery of druggable targets in single cell RNAseq data to support research of new treatments for human diseases. Our motivation was to address new challenges of data interpretation in rapidly growing universe of scRNAseq datasets. We focused on analysis of druggable targets for important cells in Systemic Lupus Erythematosus (SLE): GSE162577, GSE142016, GSE135779 `[@usesDataFrom:deng2021expression, @usesDataFrom:mistry2019transcriptomic, @usesDataFrom:nehar2020mapping]`. Summary of our project plan can be seen in the figure below.

![overview](Overview_BH2023.png)

**Data** involved work on three SLE scRNAseq datasets to identify cell types significantly affected by the disorder. Additionally, in collaboration with [Project 17](https://github.com/elixir-europe/biohackathon-projects-2023/tree/main/17) we developed interfaces for acquisition of drug target information, needed in downstream steps.

**Diagrams** describes the work done to automatically assemble pathway and disease diagrams of mechanisms enriched in cell types identified in the *Data* step. We focused on the content from Reactome and Wikipathways databases, and from selected disease maps.

**Analysis** part used the inputs from *Data* and *Diagrams* to run selected modelling tools for discovering key druggable mechanisms in SLE. Cell type-specific differentially expressed genes (DEGs), and drugs targetting them were the focus of perturbation analyses.

By the end of the BioHackathon'23 we were able to significantly advance each of these areas:
- DEGs for selected cell types (basophils and B-cells) were calculated

- this was used to build two cell type-specific pathway maps available on a public server

- a plugin for the MINERVA Platform was developed allowin interactive expport of the most relevant parts of the diagrams using drug target information and expression data

- two methods of perturbation analysis can use the exported data for modelling analysis

- an indepentent, data-driven drug discovery workflow was run to compare results with the pathway-based discovery workflow.

These results are detailed below.

# Results

Description of the workflow.
Please keep sections to a maximum of only two levels.

## Data

**Single-cell dataset**

As a source of single-cell RNA-seq (scRNA-Seq) data to study the impact of lupus disease at the gene expression level in different cell types, we aggreagated together 3 datasets retrieved from the GEO database: GSE162577, GSE142016, and GSE135779 `[@usesDataFrom:deng2021expression, @usesDataFrom:mistry2019transcriptomic, @usesDataFrom:nehar2020mapping]`. The analysis was done with Seurat package `[@usesMethodIn:hao2021integrated]`. We corrected batch effect using Harmony package`[@usesMethodIn:korsunsky2019fast]`, scTransform `[@usesMethodIn:hafemeister2019normalization]` for normalization and variance stabilization, and singleR `[@usesMethodIn:aran2019reference]` for cell typing.

Sixteen cell types were originally identified in our merged dataset: B cells, basophils, CD4+ T cells, CD8+ T cells, CMPs, dendritic cells, eosinophils, erythroid cells, GMPs, granulocytes, HSCs, megakaryocytes, MEPs, monocytes, NK cells, and NK T cells. After filtering out cell types with less than 100 cells associated to them, we retain 8 cell types: B cells, basophils, CD4+ T cells, CD8+ T cells, dendritic cells, granulocytes, monocytes, NK cells. Finally, during this Biohackathon, we prioritized analyses in 2 cell types: B cells and basophils. For gene expression analyses, we filtered out genes having less than 100 counts over the whole dataset.

We then identified differentially expressed genes for each cell type between lupus status and control status (DEG tests), as well as marker genes corresponding to genes differentially expressed in a cell type compared to all other cell types, regardless of the donor status (marker tests). We merged uncorrected gene counts of cells per sample and cell type by a pseudobulk approach (3 lupus samples, 3 control samples). We performed several analyses using the Seurat package for DEG tests and marker tests using:
* DESeq2 `[@citation:love2014moderated]` based on unnormalized uncorrected read counts
* MAST `[@citation:finak2015mast]` based on unnormalized uncorrected read counts
* DESeq2 based on expression score approach from Bgee database `[@citation:bastian2021bgee]`
* MAST based on expression score approach from Bgee database

The Bgee expression score is a non-parametric statistics allowing to make expression levels comparable between experiments, conditions, genes. Genes are ranked in each sample and cell type in ascending order of their expression level. These ranks are then rescaled between 1 and 1000 using a linear transform. These rescaled ranks are then weighted for downstream analyses based on sample and cell type information (e.g., number of mapped reads); or this Biohackathon each sample and cell type was given the same weight of 1.

After evaluating the accuracy of the results using these different approaches, we selected the results produced by DESeq2 and Bgee expression scores for the rest of the downstream analyses.

**Drug-target information**

## Maps

**Automated map assembly**

- The automap workflow [PMID:37502697] was improved for better representation of mutliple asembled pathways, producing an automatically generated summary diagram
- cell specific expression data can be provided to be autmatically included as a data overlay
- annotation of assembled maps was harmonised

**Selection of relevant components**

- For cell-specific maps, a plugin was developed to select only those compnents of a map that are relevant for a given cell type (coverage in cell expression data) and druggability (drug target information from earlier).

- The plugin exports selected map components in modelling-compatible format for HiPathia and Boolean Modelling downstream (see below). 

## Analysis

**Hipathia**

**Boolean modeling**
-   Construction of Boolean modelling: The diagrams analysed were obtained from the MINERVA Platform. This platform provides the capability to export specific diagrams from the map. The diagrams in CellDesigner SBML format were then automatically transformed into SBML-qual format using the CaSQ (CellDesigner as SBML-qual) tool. CaSQ uses specific rewriting rules to reduce diagrams from Process Description to Activity Flow notation, and to infer the logical functions and translate the interactions.
-   Topological analysis of the Boolean model: The structural and functional correctness of BM was evaluated by analysing the interactions between the biomolecules. To this end the topological features of the BM were analysed as a network.
-   Model analysis with different updating schemes: The behaviour of a BM under different update schemes was visualised through state transition graphs (see section 5 in the supplementary file), which represent all possible states of the system and the transitions between them. The state transition graph illustrates the range of outcomes for a given initial condition based on the update scheme used. Both update schemes demonstrated the ability to simulate expected system behaviour.
-   Perturbation analysis: A perturbation analysis was conducted to evaluate the effect on the topological robustness, dynamic resilience, and attractors reached by the models. Specifically, we focused on node perturbations, which alter the state of a single biomolecule through knockout and overexpressions.
-   Sensitivity analysis in response to different information: The evaluation was performed by performing sensitivity analysis on a selected set of models, examining each biomolecule. Sensitivity analysis is a technique that assesses how changes in a model or system's inputs affect its output, in this case, the two attractors reached by the model (unperturbed and perturbed). To quantify the difference between the two attractors, similarity-based distance and identity-based distance were used.
-   Stochastic Boolean model simulation: The simulations of the specified biological models were conducted using probabilistic Boolean modelling. This framework provides a tool for simulation of biological systems through discrete/continuous time Markov processes. It operates by utilising a Monte Carlo algorithm that simulates the system's evolution over time based on the initial conditions of the biomolecules and the interactions between them.

**PertFlow**
-  Probing for ground truths: Using Decoupler and pseudobulk analysis for distinct cell types, PertFlow enable the leveraging of active TFs and pathways preferentially perturbed in SLE compared to normal controls (e.g., RFX5, MEF2C, ELK4, Hypoxia, NFkb signalling) - these signaling components and patterns are corroborated by the pertinent literature
- Cell type prioritization: Deploying AugurPy package, PertFlow detected that NK T cells, B cells and Basophils were the most affect cell groups due to the SLE perturbation
- Drug Repurposing:   Using ASGARD package, PertFlow facilitated the repurposing of several compounds towards cell groups of interest (e.g., geldamycin that is under investigation for SLE was captured).

- **Network visualization** : Going beyond the current PertFlow architecture, a novel network model was created connecting genes to drugs to cell-types, creating an informative multi-partite graph that can be traversed and analyzed for deeper biological insights
- **Compatibility with Hipathia and boolean modelling**: The transformation of PertFlow results into a graph can enable a seamless integration with the modelling performed by Hipathia in terms of genes of interest, potential druggable targets and putative signaling cascades

# Discussion

# Concluding remarks



# Citation Typing Ontology annotation

You can use [CiTO](http://purl.org/spar/cito/2018-02-12) annotations, as explained in [this BioHackathon Europe 2021 write up](https://raw.githubusercontent.com/biohackrxiv/bhxiv-metadata/main/doc/elixir_biohackathon2021/paper.md) and [this CiTO Pilot](https://www.biomedcentral.com/collections/cito).
Using this template, you can cite an article and indicate _why_ you cite that article, for instance DisGeNET-RDF [@citesAsAuthority:Queralt2016].

The syntax in Markdown is as follows: a single intention annotation looks like
`[@usesMethodIn:Krewinkel2017]`; two or more intentions are separated
with colons, like `[@extends:discusses:Nielsen2017Scholia]`. When you cite two
different articles, you use this syntax: `[@citesAsDataSource:Ammar2022ETL; @citesAsDataSource:Arend2022BioHackEU22]`.

Possible CiTO typing annotation include:

* citesAsDataSource: when you point the reader to a source of data which may explain a claim
* usesDataFrom: when you reuse somehow (and elaborate on) the data in the cited entity
* usesMethodIn
* citesAsAuthority
* citesAsEvidence
* citesAsPotentialSolution
* citesAsRecommendedReading
* citesAsRelated
* citesAsSourceDocument
* citesForInformation
* confirms
* documents
* providesDataFor
* obtainsSupportFrom
* discusses
* extends
* agreesWith
* disagreesWith
* updates
* citation: generic citation

...

## Acknowledgements

...

## References
