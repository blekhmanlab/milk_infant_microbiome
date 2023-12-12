# Strain-sharing, metabolic potential and antimicrobial resistance in human milk and infant gut microbiomes

The establishment of the gut microbiome in early life is critical for healthy infant development. Although breastmilk represents the main dietary source for newborns, little is known about how variation in milk composition, and especially the milk microbiome, shapes the infant gut microbiome. Here, we quantified the similarity between the maternal milk microbiome and the infant gut microbiome using a cohort of 195 mother-infant pairs with 507 microbiome samples from both breastmilk and infant gut collected at one, three, and six months postpartum. We found that the microbial taxonomic overlap between milk and the infant gut was driven by bifidobacteria, and in particular by *B. longum*. Infant stool samples dominated by *B. longum*, *B. breve* or *B. bifidum* showed higher temporal stability in terms of microbial composition, compared to samples dominated by other species. We identified two instances of strain sharing between the maternal milk and the infant’s gut, one involving a commensal (*B. longum*) and one a potential pathogen (*K. pneumoniae*). In addition, strain sharing between unrelated infants was higher among infants born at the same hospital compared to infants born in different hospitals, suggesting a potential role of the hospital environment in microbial transmission. The infant gut microbiome at one month but not six months of age was enriched in metabolic pathways associated with de-novo molecule biosynthesis, suggesting that early colonisers need to be more versatile and metabolically independent in order to survive in the infant gut. Lastly, we found a significant overlap in antimicrobial resistance genes between mothers and their infants. Taken together, our results suggest that the breastmilk microbiome has an important role in the assembly, composition, and stability of the infant gut microbiome. 

## Cite

If you use the data, or find this work useful, please cite:


## Requirements

This project requires R version XXX   
To install all the required packages you can run:

`Rscript requirements.R`

## Workflow

#### 1. *Alpha and beta diversity

```bash
bin/Rmarkdown src/CDI_analysis/CDI_analysis.Rmd figures/CDI_analysis/CDI_analysis.html
```
