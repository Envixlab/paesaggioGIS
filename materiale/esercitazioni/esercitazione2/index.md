# Esercitazione #2 - Gestione dei dati Raster

## Overview
In questo esercizio imparerai a caricare un dataset raster, esplorare le caratteristiche del dato e manipolare la sua rappresentazione e riclassificare il raster.

[Download del Dataset](https://github.com/Envixlab/paesaggioGIS/raw/master/dataset/esercitazione_2.zip)

### Caricamento del dataset
Creare una cartella \paesaggioGIS\esercizio_2 nel percorso C:\paesaggioGIS\esecizio_2 e copiare all'interno il dataset DEM_Molise_Tinitaly.tif. Aprire QGIS, creare un nuovo progetto e salvarlo nella cartella appena creata.
In QGIS cliccare su `Layer -> Aggiungi Raster -> Aggiungi Layer Raster`, navigare nella cartella contenente il file e caricare il dataset DEM_Molise_Tinitaly.tif [[link al tutorial](./materiale/tutorial/caricamento_raster/index)].

Il dataset deriva dal Modello Digitale del Terreno d'Italia, creato da  [Tarquini et al. 2007](http://tinitaly.pi.ingv.it/).

### Esplorazione delle proprietà
Cliccare con il tasto destro nel pannello dei layer sul nome del file e selezionare `Proprietà`. Spostarsi nella scheda `Informazioni`.

* Qual è la risoluzione?
* Da quante bande è composto?
* Quali sono i valori minimo, massimo e medio?

### Vestizione del dataset
Spostarsi nella scheda `Simbologia`.

Tipo di visualizzazione:
* `Banda singola grigia`: assegna una scala di grigi
* `Colori banda multipla`: sfrutta le informazioni contenute in raster multibanda per ricreare un colore secondo il modello RGB
* `Banda singola falso colore`: assegna una colorazione utilizzando delle scale di colorazione
* `Valori a Tavolozza/Univoci`: si utilizzano per raster categorici in cui i valori dei pixel esprimono delle qualità o categorie (es. uso del suolo)
* `Ombreggiatura` e `Curve di livello`: si utilizzando per i modelli digitali del terreno

#### Tematizzare il dataset selezionando una scala topografica
Nella scheda `Simbologia`:
* `Tipo di visualizzazione`: Banda singola falso colore
* `Impostazioni dei valori Min e Max`: Min/Max
* `Accuratezza`: Attuale (più lento)
* `Interpolazione`: Lineare
* `Scala colori`: Cliccare sul <img src="https://static.thenounproject.com/png/1786994-200.png" alt="dropdown" height="20"> `Crea Nuova Scala Colore` -> `Catalogo: cpt-city` e selezionare una delle scale sotto la voce `Topography`

### Riclassificare un raster
Riclassificare un raster significa assegnare dei nuovi valori ai pixel secondo delle condizioni. In questo esercizio si vuole riclassificare il modello digitale del terreno per ottenere un raster delle fasce altimetriche.

Aprire gli strumenti di processing e cercare `Riclassifica con tabella`:
* `Layer Raster`: DEM_Molise_Tinitaly
* `Numero banda`: 1
* `Tabella di riclassificazione`:

|Minimo|Massimo|Valore|
| ----------- | ----------- | ----------- |
|0            |400          |1            |
|400          |800          |2            |
|800          |1200         |2            |
|1200         |1600         |2            |
|1600         |2200         |2            |

* `Parametri avanzati`
* `Limiti intervallo`: min < valore <=max
* `Raster riclassificato`: Salvare il file all'interno della cartella di progetto

Per tematizzare il raster utilizzare `Valori a Tavolozza/Univoci`
