# Assembly of the infant gut microbiome and resistome are linked to bacterial strains in mother’s milk

The establishment of the gut microbiome in early life is critical for healthy infant development. Although human milk is recommended as the sole source of nutrition for the human infant, little is known about how variation in milk composition, and especially the milk microbiome, shapes the microbial communities in the infant gut. Here, we quantified the similarity between the maternal milk and the infant gut microbiome using **507 metagenomic samples collected from 195 mother-infant pairs at 1, 3, and 6 months postpartum**. We found that:
- the microbial **taxonomic overlap between milk and the infant gut** was driven by bifidobacteria, and in particular by *B. longum*. Infant stool samples dominated by *B. longum* also showed higher temporal stability compared to samples dominated by other species.
- We identified numerous instances of strain sharing between maternal milk and the infant gut, involving commensal species (e.g. *B. longum*) as well as pathobiont ones (e.g. *K. pneumoniae*). Among strains shared between the mother’s milk and the infant gut, we identified species typically found in the human oral cavity, such as *S. salivarius* and *V. parvula*, suggesting a potential transmission from the infant’s oral cavity to the mother’s milk. 
- The infant gut microbiome at 1 month compared to 6 months of age was enriched in **metabolic pathways** associated with *de-novo* molecule biosynthesis, suggesting that early colonisers might be more versatile and metabolically independent compared to later colonizers.
- Lastly, we found a significant overlap in **antimicrobial resistance** genes carriage between the mother’s milk and their infant's gut microbiome.

Taken together, our results suggest that the human milk microbiome has an important role in the assembly, composition, and stability of the infant gut microbiome. 

## Cite

If you use the data, or find this work useful, please cite:
_______
### Assembly of the infant gut microbiome and resistome are linked to bacterial strains in mother’s milk
* Pamela Ferretti† , Mattea Allert†, Kelsey E. Johnson, Marco Rossi, Timothy Heisel, Sara Gonia, Dan Knights, David A. Fields, Frank W. Albert, Ellen W. Demerath, Cheryl A. Gale, and Ran Blekhman.*
(† equal contribution)
________
For more information on the tools used and their references, please check the **Methods** section of the paper.

## Requirements

This project requires R version 4.2    
The required libraries are indicated at the beginning of each script. 

The data analyses steps described below require the output of the following publicly available tools: [MetaPhlAn4](https://huttenhower.sph.harvard.edu/metaphlan/), [*B. longum* subspecies profiler](https://github.com/yassourlab/MetaPhlAn-B.infantis/), [StrainPhlAn4](https://github.com/biobakery/MetaPhlAn/wiki/StrainPhlAn-4), [HUMAnN3](https://github.com/biobakery/humann) and [DeepARG](https://github.com/gaarangoa/deeparg). The masterfiles resulting from these steps are provided as Supplementary Tables in the paper and can also be downloaded from [Zenodo](https://zenodo.org/records/17089803). 

## Raw Data

The raw metagenomic sequences and the associated metadata were deposited and are available on NCBI Sequence Read Archive (SRA) under the BioProject accession numbers [PRJNA1019702](https://www.ebi.ac.uk/ena/browser/view/PRJNA1019702) and [PRJNA1198101](https://www.ebi.ac.uk/ena/browser/view/PRJNA1198101). Comprehensive metadata are available in the Supplementary Material and on [Zenodo](https://zenodo.org/records/17089803). 

## Workflow

#### 1. Cohort and metadata overview

Overview of the structure of the cohort and its relevant metadata, including delivery mode, breastfeeding and antibiotics intake (pre- and post-partum). 

```bash
bin/Rmarkdown src/metadata_stats/metadata_stats.Rmd figures/metadata_stats/metadata_stats.html
```

#### 2. Alpha and beta diversity

Here we looked at the intra and inter-sample taxonomic composition at the species-level for both milk and infant stool samples. Shannon diversity values were generated with the [MetaPhlAn4](https://huttenhower.sph.harvard.edu/metaphlan/) utility script [`calculate_diversity.R`](https://github.com/biobakery/MetaPhlAn/blob/master/metaphlan/utils/calculate_diversity.R). 

```bash
bin/Rmarkdown src/alpha_diversity/alpha_diversity.Rmd figures/alpha_diversity/alpha_diversity.html
bin/Rmarkdown src/beta_diversity/beta_diversity.Rmd figures/beta_diversity/beta_diversity.html
```

#### 3. Species composition with MetaPhlAn4

To investigate the microbial composition of milk and infant gut at the species-level we used MetaPhlAn4. Installation and usage commands are available [here](https://github.com/biobakery/MetaPhlAn/wiki/MetaPhlAn-4). From the resulting taxonomic profiles, we generated the species-level heatmaps:

```bash
bin/Rmarkdown src/species_composition/species_composition.Rmd figures/species_composition/species_composition.html
```

#### 4. Analysis on Bifidobacteria and species stability

Here we identify the predominance group for each sample. We broadly defined 4 predominance groups: samples dominated by *B. longum*, by *B. breve*, *B. bifidum* and samples dominated by non bifidobacteria species (most frequently *E. coli*). We also focused on the prevalence and mean relative abundance of the above listed Bifidobacteria in relation to the breastfeeding practice in the infants at 1 and 6 months of age. 

```bash
bin/Rmarkdown src/groups_stability/bifido_groups.Rmd figures/groups_stability/bifido_groups.html
```

#### 5. *B. longum* subspecies analysis

As MetaPhlAn4 has no marker genes to identify and distinguish *B. longum* subspecies (mainly *BL. infantis* and *BL. longum*), we used a modified version of the standard MetaPhlAn4 database. Details of the modified database can be found in the original publication by [Ennis et al.](https://www.nature.com/articles/s41467-024-45209-y), while the database can be found on [GitHub](https://github.com/yassourlab/MetaPhlAn-B.infantis/).

```bash
bin/Rmarkdown src/subspecies/subspecies_analysis_git.Rmd figures/subspecies/subspecies.html
bin/Rmarkdown src/subspecies/heatmap_subspecies.Rmd figures/subspecies/heatmap_subspecies.Rmd
bin/Rmarkdown src/subspecies/bifidos_subspecies_abundances.Rmd figures/subspecies/bifidos_subspecies_abundances.Rmd
```

#### 6. Functional profiling with HUMAnN3

In this section we investigated the functional potential of the maternal milk and infant gut microbiomes using HUMAnN3. Installation and usage commands are available [here](https://github.com/biobakery/humann). As the most prevalent pathways identified in the infant stool samples were associated with de-novo biosynthesis of molecules, we further explore the abundance of pathways associated with the biosynthesis of essential amino acids. We also looked at the pathways shared between the maternal milk and the infant gut.

```bash
bin/Rmarkdown src/functional_profiling/heatmap_pathways.Rmd figures/functional_profiling/heatmap_pathways.html
bin/Rmarkdown src/functional_profiling/functional_analysis_biosynthesis_essentialAA.Rmd figures/functional_profiling/functional_analysis_biosynthesis_essentialAA.html
```

We then investigate the functional potential similarities in mother-infant pairs.

```bash
bin/Rmarkdown src/functional_profiling/functional_analysis_couples.Rmd figures/functional_profiling/functional_analysis_couples.html
```

#### 7. Strain sharing and persistence

We then looked at the strain-level composition of the maternal breast milk and infant gut. We used [StrainPhlAn4](https://github.com/biobakery/MetaPhlAn/wiki/StrainPhlAn-4) to identify strains shared between a mother and her infant. We also looked at how persistent over time were the strains in the infant gut:

```bash
bin/Rmarkdown src/strain_analysis/strain_persistence.Rmd figures/strains/strain_persistence.html
```

#### 8. Assess the impact of mother's milk secretor status 

We also investigated whether the mother's secretor status impacts breast milk microbiome diversity and composition, and strain stability in the infant gut microbiome.

```bash
bin/Rmarkdown src/secretor_status/secretor_analysis.Rmd figures/secretor_status/secretor_analysis.html
```

#### 9. Antimicrobial resistance genes prediction

Last, we investigated the carriage of antimicrobial resistance genes (ARGs) in milk and infant stools using [DeepARG](https://github.com/gaarangoa/deeparg). To avoid false positives, we considered only ARGs associated with well-defined ARG classes (excluding multi-drug and undefined ARGs classes), and with an identity threshold >95% (See Methods for more details). First, we describe the major classes identified in each sample type and collection timepoint. We then investigate the correlation between the ARGs found in milk compared to those found in the stools, as well as the correlation between the ARGs found at 1M versus those found at 6M. Finally, we looked at ARGs sharing between the mother's milk and her infant's gut.

```bash
bin/Rmarkdown src/ARG_analysis/ARG_analysis.Rmd figures/ARG_analysis/ARG_analysis.html
bin/Rmarkdown src/ARG_analysis/ARG_analysis_couples.Rmd figures/ARG_analysis/ARG_analysis_couples.html
```


### Notes

A subset of the whole dataset can be used to first get familiar with the code and the tools listed above. Please refer to the original papers and tutorials for the tools' computational requirements and running time. Supplementary tables can be downloaded on [Zenodo](https://zenodo.org/records/17089803).

Please refer to the **Discussion** section of the paper for the limitations of this study.
