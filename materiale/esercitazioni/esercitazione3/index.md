# Esercitazione #3 - Quantificare il Paesaggio
## Overview
In questo esercizio imparerai a quantificare il paesaggio attraverso l'utilizzo degli indici di paesaggio (o metriche di paesaggio). La prima parte sarà dedicata alla preparazione del dataset, mentre la seconda verterà sull'analisi.
L'esercitazione prevede l'utilizzo del software [Fragstats](https://www.umass.edu/landeco/research/fragstats/fragstats.html): Spatial Pattern Analysis Program for Categorical Maps (McGarigal, K., SA Cushman, and E Ene. 2012).

[Download del Dataset](https://github.com/Envixlab/paesaggioGIS/raw/master/dataset/esercitazione_3.zip)

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
* `Rasterizzato`: Salvare il file all'interno della cartella di progetto (landcover_vandra.tif/landcover_tappino.tif)

# Parte2: analisi del pattern
Lanciare l'eseguibile di Fragstats. Verrà effettuata un'analisi del pattern a livello di classe (per ogni categoria di land cover) e a livello di paesaggio (considerando tutte le categorie insieme).

Nella tab `Input Layers`:
* `Add layer`
* `Data type`: GeoTIFF
* `Select file`: selezionare il file raster landcover_vandra.tif
* `Select file`: selezionare il file raster landcover_tappino.tif

Nella tab `Analysis parameters`:
* `General options`: Use 8 cell neighborhood rule
* `Sampling strategy`: No sampling e spuntare Class metrics e Landscape metrics

Cliccare sull'icona `Class metrics` e selezionare:

| Area-Edge      | Aggregation |
| ----------- | ----------- |
| PLAND      | PD       |
| ED   | NP        |
| -   | AI        |

Cliccare sull'icona `Landscape metrics` e selezionare:

| Diversity    |
| -----------  |
| SHDI        |

Cliccare su `Run`.

* PLAND (Percentage of landscape): indice di base che esprime, in percentuale, la copertura delle singole classi. Descrive la composizione del paesaggio.
* ED (Edge Density): corrisponde alla lunghezza totale del perimetro in rapporto alla superficie in ettari. In generale, ad aumentare dei livelli di frammentazione, ED aumenta. Tuttavia, ED ha un comportamento fortemente non lineare in relazione a PLAND [Carranza et al. 2015](https://github.com/Envixlab/paesaggioGIS/blob/master/pdf/Carranzaetal2015.pdf).
* NP (Number of Patches) e PD (Patches Density): esprimono il numero di pacthes di una determinata classe in valori assoluti (NP) oppure in relazione all'estensione della classe (PD).
* AI (Aggregation Index): esprime il livello di aggregazione delle pacthes (valori elevati esprimono patches compatte e ben connesse)
* SHDI (Shannon Diversity Index): esprime la diversità del paesaggio considerando sia il numero di pathces appartenenti a classi differenti (ricchezza) che la loro abbondanza realtiva.

Nella scheda Results sono presenti i risultati dell'analisi del pattern, a livello di classe (`Class`) e a livello di paesaggio (`Landscape`). Cliccsare su `Save run as`, selezionare la cartella dove salvare il file e dare un nome (es. `risultati_pattern`). Vengono generati due file di output con estensione `.class` e `.land`. Per importarli in un foglio di calcolo e fare le analisi occorre modificare i due file con un editori di testo (Blocco note di windows).

Aprire il Blocco note, cliccare su `File` -> `Apri` -> `Tutti i file` e selezionare `risultati_pattern.class`. Il separatore decimale dell'ouput è il punto, ma i sistemi Windows in Italia, sono settati per avere come sepratore decimale la virgola. Bisogna quindi sostituire il punto con la virgola e, la virgola utilizzata per separare le colonne, con il punto e virgola (**se si usa come foglio elettronico Fogli di Google questa operazione non è necessaria. Si può saltare questo step**).
Cliccare su Modifica -> Sostituisci:
* `Trova`: ,
* `Sostituisci`: ;
* `Sostituisci tutto`
Ripetere l'operazione
* `Trova`: .
* `Sostituisci`: ,
* `Sostituisci tutto`
Salvare il file. Ripetere l'operazione per il file con estensione .land. Rinominare i file `.class` e `.land` in `.class.csv` e `.land.csv`.

Aprire i file (.csv) con un foglio elettronico (Excel, Calc di Open Office, Google Fogli). Controllare la formattazione. Se in excel si hanno problemi, selezionare l'intera colonna, cliccare su Dati, Testo in colonne, Delimitato, spuntare il Punto e virgola, Fine. Salvare il file come cartella di lavoro di Excel.

Rappresentare i dati utilizzando i grafici. Confrontare il pattern del bacino del fiume Vandra con il pattern del bacino del fiume Tappino. Rispondere alle seguenti domande:

* Qual è la matrice dei due paesaggi?
* Confrontare gli indici della classe foreste dei due paesaggi. Qual è il livello di frammentazione?
* Confrontare gli indici NP e PD
* Esaminare il comportamento dell'indice ED. Confrontare i valori con l'andamento dell'indice riportato in [Carranza et al. 2015](https://github.com/Envixlab/paesaggioGIS/blob/master/pdf/Carranzaetal2015.pdf)
* Confrontare gli indici di diversità dei due paesaggi
* Quali potrebbero essere i processi che hanno portato all'assetto attuale del pattern spaziale?
