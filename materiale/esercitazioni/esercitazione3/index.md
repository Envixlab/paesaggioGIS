# Esercitazione #3 - Quantificare il Paesaggio
## Overview
In questo esercizio imparerai a quantificare il paesaggio attraverso l'utilizzo degli indici di paesaggio (o metriche di paesaggio). La prima parte sarà dedicata alla preparazione del dataset, mentre la seconda verterà sull'analisi.

In questo esercizio userai il programma [Fragstats](https://www.umass.edu/landeco/research/fragstats/fragstats.html): Spatial Pattern Analysis Program for Categorical Maps (McGarigal, K., SA Cushman, and E Ene. 2012).

# Parte1: creazione del dataset
Caricare il dataset vettoriale `uso_suolo.shp`. Il dataset deriva dalla [Carta della Natura della Regione Molise in scala 1:25.000](https://www.isprambiente.gov.it/it/servizi/sistema-carta-della-natura/carta-della-natura-alla-scala-1-50.000/molise). La legenda iniziale che prevede la classificazione delle unità di copertura e uso del suolo secondo lo schema CORINE BIOTOPES, è stata modificata in accordo con il sistema di classificazione sviluppato da [Anderson et al. 1976](https://pubs.usgs.gov/pp/0964/report.pdf), che prevede 7 classi:
* Built-up land
* Agricultural land 
