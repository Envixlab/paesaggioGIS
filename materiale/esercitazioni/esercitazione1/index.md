# Esercitazione #1 - Gestione dei dati vettoriali

## Overview

In questo esercizio imparerai a caricare un dataset vettoriale, esplorare la tabella attributi e utilizzare i dati contenuti per tematizzare il dataset. Nella seconda parte dell'esercizio imparerai ad effettura delle queries sia spaziali che non spaziali e ad esportare il dataset selezionato.

## Parte 1: caricamento del dataset vettoriale comuni_molise

### Carciamento del dataset

Creare una cartella \paesaggioGIS\esercizio_1 nel percorso C:\paesaggioGIS\esecizio_1 e copiare all'interno il dataset comuni_molise (.shp, .shx, .dbf, .prj). Aprire QGIS, creare un nuovo progetto e salvarlo nella cartella appena creata.
In QGIS cliccare su `Layer -> Aggiungi Layer -> Aggiungi Layer Vettore` , navigare nell'apposita cartella e caricare il dataset comuni_molise [link al tutorial](./materiale/tutorial/caricamento_vettoriali/index).


Utilizzare gli strumenti di pan e zoom per prendere confidenza con gli strumenti di QGIS. Per aprire la tabella attributi cliccare sull'icona `Apri Tabella Attributi` oppure cliccare il tasto F6. Esplorare la tabella attributi.

### Vestizione o tematizzazione del dataset
Vestire o tematizzare un dato significa assegnare colori differenti alle geometrie del dato sulla base delle caratteristiche contenute nella tabella attributi, al fine di evidenziare un fenomeno.
Nel caso in esame, si vugliono rappresentare i comuni del molise in base alla provincia di appartenenza. Nella tabella attributi è presente il campo `COD_PRO` i cui valori identificano la provincia:

* `COD_PRO = 94` Isernia
* `COD_PRO = 70` Campobasso

Per modificare lo stile del dataset cliccare su `Apri il pannello Stile Layer` oppure premere il tasto F7 oppure cliccare nel pannello dei layer sul nome del dataset, tasto destro, proprietà, selezionare la scheda `Simbologia`.

Esistono diversi tipi di tematizzazione; i più utilizzati sono:

* `Simbolo singolo` (default) : assegna lo stesso colore a tutte le geometrie del layer;
* `Categorizzato` : assegna lo stesso colore a tutte le geometrie del layer;
* `Graduato` : assegna lo stesso colore a tutte le geometrie del layer;



## Parte 2: Query

### Selezione non spaziale


caricamento SIC
Selezione spaziale


|-- karma.conf.js
    |-- package.json
    |-- app
        |-- app.js
        |-- db.js
        |-- directoryList.md
        |-- index.html
        |-- mddir.js
        |-- routing.js
        |-- server.js
        |-- _api
            |-- api.groups.js
            |-- api.posts.js
            |-- api.users.js
            |-- api.widgets.js
