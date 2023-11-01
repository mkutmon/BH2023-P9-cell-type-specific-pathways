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
    affiliation: 1
  - name: Naveed Ishaque
    orcid: 0000-0002-8426-901X
    affiliation: 1
  - name: Ahmed Hemedan
    orcid: 0000-0001-7403-181X
    affiliation: 1
  - name: Alessandro Brandulas Cammarata
    orcid: 0009-0006-5956-9842
    affiliation: 1
  - name: Egon Willighagen
    orcid: 0000-0001-7542-0286
    affiliation: 1
  - name: Frederic Bastian
    orcid: 0000-0002-9415-5104
    affiliation: 1
  - name: George Gavriilidis
    orcid: 0000-0003-2575-4354
    affiliation: 1
  - name: Hasan Balci
    orcid: 0000-0001-8319-7758
    affiliation: 1
  - name: Kim Vucinic
    affiliation: 1
  - name: Kinza Rian
    orcid: 0000-0003-4314-7208
    affiliation: 1
  - name: Liya Zaygerman
    orcid: 0009-0005-4947-6223
    affiliation: 1
  - name: Marina Esteban-Medina
    orcid: 0000-0003-2632-9587
    affiliation: 1
  - name: Matti Hoch
    orcid: 0000-0002-2486-0246
    affiliation: 1
  - name: Sabrina Jagot
    orcid: 0000-0002-6718-4794
    affiliation: 1
  - name: Sandra Ng
    orcid: 0000-0003-4524-6058
    affiliation: 1
  - name: Sara Pita
    affiliation: 1
affiliations:
  - name: First Affiliation
    index: 1
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
authors_short: First Author \emph{et al.}
---

Author order to be decided

# Introduction

As part of the BioHackathon Europe 2023, we here report...

# Results

Description of the workflow.
Please keep sections to a maximum of only two levels.

## Data

**Single-cell dataset**

**Drug-target information**

## Maps

**Generation of map**

**Pruning of relevant components**

## Analysis

**Hipathia**

**Boolean modeling**

**PertFlow**

**Network visualization**

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
