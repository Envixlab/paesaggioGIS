# Esercitazione #3 - Quantificare il Paesaggio
## Overview
In questo esercizio imparerai a quantificare il paesaggio attraverso l'utilizzo degli indici di paesaggio (o metriche di paesaggio). La prima parte sarà dedicata alla preparazione del dataset, mentre la seconda verterà sull'analisi.

In questo esercizio userai il programma [Fragstats](https://www.umass.edu/landeco/research/fragstats/fragstats.html): Spatial Pattern Analysis Program for Categorical Maps (McGarigal, K., SA Cushman, and E Ene. 2012).

# Parte1: creazione del dataset
Caricare il dataset vettoriale `uso_suolo.shp`. Il dataset deriva dalla [Carta della Natura della Regione Molise in scala 1:25.000](https://www.isprambiente.gov.it/it/servizi/sistema-carta-della-natura/carta-della-natura-alla-scala-1-50.000/molise). La legenda iniziale che prevede la classificazione delle unità di copertura e uso del suolo secondo lo schema CORINE BIOTOPES, è stata modificata in accordo con il sistema di classificazione sviluppato da [Anderson et al. 1976](https://pubs.usgs.gov/pp/0964/report.pdf), che include 7 classi:
* Built-up land (code 1)
* Agricultural land (code 2)
* Forest land (code 3)
* Rangeland (code 4)
* Barren land (code 5)
* Water (code 6)
* Wetland (code 7)

Caricare i dataset vettoriali `bacino_idrografico_tappino.shp` e `bacino_idrografico_vandra.shp`.

Utilizzare lo strumento `Ritaglia` del menu `Geoprocessing`, per creare due carte di copertura del suolo (landcover_vandra e landcover_tappino). Le mappe create sono in formato vettoriale. Fragstats utilizza solo mappe in formato raster. Per effettuare la conversione, andare nel menu `Raster` -> `Conversione` -> `Rasterizza`
* `Vettore in ingresso`: landcover_vandra (landcover_tappino)
* `Campo da usare per un valore di masterizzazione`: Code_ander
* `Unità di misura del raster in uscita`: Unità georeferenziate
* `Larghezza/Risoluzione orizzontale`: 10
* `Larghezza/Risoluzione verticale`: 10
* `Estensione del risultato`: Calcola da Layer->landcover_vandra (landcover_tappino)
* `Rasterizzato`: Salvare il file all'interno della cartella di progetto (landcover_vandra.tif)

# Parte2: analisi del pattern
Lanciare l'eseguibile di Fragstats. Verrà effettuata un'analisi del pattern a livello di classe (per ogni categoria di land cover) e a livello di paesaggio (considerando tutte le categorie insieme).

Nella tab `Input Layers`:
* `Add layer`
* `Data type`: GeoTIFF
* `Select file`: selezionare il file raster

Nella tab `Analysis parameters`:
* `General options`: Use 8 cell neighborhood rule
* `Sampling strategy`: No sampling e spuntare Class metrics e Landscape metrics

Cliccare sull'icona `Class metrics` e selezionare:

| Area-Edge      | Aggregation |
| ----------- | ----------- |
| PLAND      | PD       |
| ED   | AI        |

Cliccare sull'icona `Landscape metrics` e selezionare:

| Diversity    |
| -----------  |
| SHDI        |

Cliccare su `Run`.

Nella scheda Results sono presenti i risultati dell'analisi del pattern, a livello di classe (`Class`) e a livello di paesaggio (`Landscape`). Cliccsare su `Save run as`, selezionare la cartella dove salvare il file e dare un nome (es. vandra/tappino).
