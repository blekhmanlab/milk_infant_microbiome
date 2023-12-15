# Strain-sharing, metabolic potential and antimicrobial resistance in human milk and infant gut microbiomes

The establishment of the gut microbiome in early life is critical for healthy infant development. Although breastmilk represents the main dietary source for newborns, little is known about how variation in milk composition, and especially the milk microbiome, shapes the infant gut microbiome. Here, we quantified the similarity between the maternal milk microbiome and the infant gut microbiome using a cohort of 195 mother-infant pairs with 507 microbiome samples from both breastmilk and infant gut collected at one, three, and six months postpartum. We found that the microbial taxonomic overlap between milk and the infant gut was driven by bifidobacteria, and in particular by *B. longum*. Infant stool samples dominated by *B. longum*, *B. breve* or *B. bifidum* showed higher temporal stability in terms of microbial composition, compared to samples dominated by other species. We identified two instances of strain sharing between the maternal milk and the infant’s gut, one involving a commensal (*B. longum*) and one a potential pathogen (*K. pneumoniae*). In addition, strain sharing between unrelated infants was higher among infants born at the same hospital compared to infants born in different hospitals, suggesting a potential role of the hospital environment in microbial transmission. The infant gut microbiome at one month but not six months of age was enriched in metabolic pathways associated with de-novo molecule biosynthesis, suggesting that early colonisers need to be more versatile and metabolically independent in order to survive in the infant gut. Lastly, we found a significant overlap in antimicrobial resistance genes between mothers and their infants. Taken together, our results suggest that the breastmilk microbiome has an important role in the assembly, composition, and stability of the infant gut microbiome. 

## Cite

If you use the data, or find this work useful, please cite:
_______
### Microbial strain and functional overlap between mother's milk and the infant gut
*Mattea Allert† , Pamela Ferretti† , Kelsey E. Johnson, Timothy Heisel, Sara Gonia, Dan Knights, David A. Fields, Frank W. Albert, Ellen W. Demerath, Cheryl A. Gale, and Ran Blekhman.*

________
For more information on the tools used and their references, please check the Methods section of the paper.

## Requirements

This project requires R version 4.2    
To install all the required packages you can run:

`Rscript requirements.R`

## Workflow

#### 1. Cohort and metadata overview
Overview of the structure of the cohort and its relevant metadata, including delivery mode, breastfeeding and antibiotics intake (pre- and post-partum). 
```bash
bin/Rmarkdown src/metadata_stats/metadata_stats.Rmd figures/metadata_stats/metadata_stats.html
```

#### 2. Alpha and beta diversity

Here we looked at the intra and inter-sample taxonomic composition at the species-level for both milk and infant stool samples. Shannon diversity values were generated with the MetaPhlAn4 utility script calculate_diversity.R. 

```bash
bin/Rmarkdown src/alpha_diversity/alpha_diversity.Rmd figures/alpha_diversity/alpha_diversity.html
bin/Rmarkdown src/beta_diversity/beta_diversity.Rmd figures/beta_diversity/beta_diversity.html
```

#### 3. Species composition with MetaPhlAn4

To investigate the microbial composition of milk and infant gut at the species-level we used MetaPhlAn4, and generated the associated heatmap.

```bash
bin/Rmarkdown src/species_composition/species_composition.Rmd figures/species_composition/species_composition.html
```

#### 4. Analysis on Bifidobacteria and species stability

Here we identify the predominance group for each sample. We broadly defined 4 predominance groups: samples dominated by *B. longum*, by *B. breve*, *B. bifidum* and samples dominated by non bifidobacteria species (most frequently *E. coli*). We also focused on the prevalence and mean relative abundance of the above listed Bifidobacteria in relation to the breastfeeding practice in the infants at 1 and 6 months of age. 

```bash
bin/Rmarkdown src/groups_stability/bifido_groups.Rmd figures/groups_stability/bifido_groups.html
bin/Rmarkdown src/groups_stability/name.Rmd figures/groups_stability/name.html
```

#### 5. Functional profiling with HUMAnN3

In this section we investigated the functional potential of the maternal milk and infant gut microbiomes. As the most prevalent pathways identified in the infant stool samples were associated with de-novo biosynthesis of molecules, we further explore the abundance of pathways associated with the biosynthesis of essential amino acids. We also looked at the pathways shared between the maternal milk and the infant gut.

```bash
bin/Rmarkdown src/functional_profiling/name.Rmd figures/functional_profiling/name.html
bin/Rmarkdown src/functional_profiling/name.Rmd figures/functional_profiling/name.html
bin/Rmarkdown src/functional_profiling/name.Rmd figures/functional_profiling/name.html
```

#### 6. Strain sharing and persistence

We then looked at the strain-level composition of the maternal breast milk and infant gut. We used StrainPhlAn4 to identify strains shared between a mother and her infant, as well as between unrelated infants. We leveraged the multi-hospital structure of the cohort to assess wether infants born at the same hospital (and in the same hospital and same year) shared more strains than infants born across different hospitals. 

```bash
bin/Rmarkdown src/strains/name.Rmd figures/strains/name.html
bin/Rmarkdown src/strains/name.Rmd figures/strains/name.html
```

#### 7. Antimicrobial resistance genes prediction

Last, we investigated the carriage of antimicrobial resistance genes (ARGs) in milk and infant stools. To avoid false positives, we considered only ARGs associated with well-defined ARG classes (excluding multi-drug and undefined ARGs classes), and with an identity threshold >95% (See Methods for more details). First, we describe the major classes identified in each sample type and collection timepoint. We then investigate the correlation between the ARGs found in milk compared to those found in the stools, as well as the correlation between the ARGs found at 1M versus those found at 6M. Finally, we looked at ARGs sharing between the mother's milk and her infant's gut.

```bash
bin/Rmarkdown src/ARG/ARG_analysis.Rmd figures/ARG/ARG_analysis.html
bin/Rmarkdown src/ARG/ARG_analysis_MotherInfant_pairs.Rmd figures/ARG/ARG_analysis_MotherInfant_pairs.html
```

### Important Notes

The raw sequences are deposited on NCBI Sequence Read Archive (SRA) under the BioProject accession number PRJNA1019702.
Please refer to the discussions section of the paper for the limitations of this study.
