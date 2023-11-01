---
title: 'BioHackEU23 report: Template for the very long title'
title_short: 'BioHackEU23 #9: Cell type-specific and druggable pathway models and maps'
tags:
  - single-cell data
  - pathway
  - disease maps
  - druggability
authors:
  - name: Marek Ostaszewski
    affiliation: 1
  - Martina Kutmon
    affiliation: 2
  - name: Naveed Ishaque
    orcid: 0000-0000-0000-0000
    affiliation: 3
  - Ahmed Hemedan
    affiliation: 4
  - Alessandro Brandulas Cammarata
    affiliation: 5
  - Egon Willighagen
    affiliation: 6
  - Frederic Bastian
    affiliation: 7
  - George Gavriilidis
    affiliation: 8
  - Hasan Balci
    affiliation: 2
  - Kim Vucinic
    affiliation: 9
  - Kinza Rian
    affiliation: 10
  - Liya Zaygerman
    affiliation: 11
  - Marina Esteban-Medina
    affiliation: 10
  - Matti Hoch
    affiliation: 12
  - Sabrina Jagot
    affiliation: 13
  - Sandra Ng
    affiliation: 14
  - Sara Pita
    affiliation: 15
affiliations:
  - name: First Affiliation
    index: 1
  - name: Second Affiliation
    index: 2
  - name: Second Affiliation
    index: 3
  - name: First Affiliation
    index: 4
  - name: Second Affiliation
    index: 5
  - name: Second Affiliation
    index: 6
  - name: First Affiliation
    index: 7
  - name: Second Affiliation
    index: 8
  - name: Second Affiliation
    index: 9
  - name: First Affiliation
    index: 10
  - name: Second Affiliation
    index: 11
  - name: Second Affiliation
    index: 12
  - name: First Affiliation
    index: 13
  - name: Second Affiliation
    index: 14
  - name: Second Affiliation
    index: 15  
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


# Introduction

As part of the BioHackathon Europe 2023, we here report...

# Formatting

This document use Markdown and you can look at [this tutorial](https://www.markdowntutorial.com/).

## Subsection level 2

Please keep sections to a maximum of only two levels.

## Tables and figures

Tables can be added in the following way, though alternatives are possible:

Table: Note that table caption is automatically numbered and should be
given before the table itself.

| Header 1 | Header 2 |
| -------- | -------- |
| item 1 | item 2 |
| item 3 | item 4 |

A figure is added with:

![Caption for BioHackrXiv logo figure](./biohackrxiv.png)

# Other main section on your manuscript level 1

Lists can be added with:

1. Item 1
2. Item 2

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


# Results


# Discussion

...

## Acknowledgements

...

## References
