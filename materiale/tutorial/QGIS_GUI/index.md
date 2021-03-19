# GUI (Graphical User Interface) di QGIS

![gui](../../../images/gui.png)

1. `Barra dei menu`
2. `Barra degli strumenti`
3. `Pannello dei Layer`: nei GIS i dati geografici (sia raster che vettoriali) vengono gestiti secondo la struttura dei layer (o strati). Un layer può contenere un solo tipo di dato (es. puntuale, lineare, areale, raster)
4. `Pannello del browser`: permette di navigare nelle cartelle del computer
5. `Map Canvas`
6. `Barra di stato`

Per la lista completa delle funzioni dei menu, consultare nel manuale utente di QGIS, la sezione [QGIS GUI](https://docs.qgis.org/3.16/it/docs/user_manual/introduction/qgis_gui.html). Di seguito la lista dei comandi che verrà utilizzata maggiormente durante il corso.

## Barra dei menu

* `Progetto`: creazione di un nuovo progetto, salvataggio, impostazioni del progetto corrente, layout di stampa
* `Modifica`: comandi per l'editing vettoriale
* `Visualizza`: comandi per la navigazione della mappa
* `Layer`: aggiungere, rimuovere, ecc. layer al Map Canvas
* `Impostazioni`: impostazioni generali di QGIS (influenzano il comportamento di tutti i progetti)
* `Plugins`: installazione e gestione dei Plugins
* `Vettore`: alcuni comandi per compiere operazioni su dati vettoriali
* `Raster`: alcuni comandi per compiere operazioni su dati raster
* `Database`: gestione dei dati presenti in formato database (Geopackage, PostGIS, SpatiaLite)
* `Web`: strumenti dedicati all'integrazione web (webmapping, basemaps, ecc.)
* `Mesh`: strumenti dedicati all'elaborazione di layer Mesh (tipo di dato differente dai formati raster e vettoriali, utilizzto per descrivere fenomeni complessi come velocità e direzione del vento)
* `Processing`: racchiude gli strumenti di Processing, il modellatore grafico, gli strumenti di altri software integrati in QGIS, ecc.

## Barra degli strumenti
Alcuni strumenti più utilizzati durante il corso.

* ![new](https://docs.qgis.org/3.16/it/_images/mActionFileNew.png) Crea un nuovo progetto
* ![open](https://docs.qgis.org/3.16/it/_images/mActionFileOpen.png) Apre un progetto esistente
* ![save](https://docs.qgis.org/3.16/it/_images/mActionFileSave.png) Salva il progetto corrente
* ![pan](https://docs.qgis.org/3.16/it/_images/mActionPan.png) Sposta la mappa (in alternativa schiacciare la rotella del mouse)
* ![zoom_in](https://docs.qgis.org/3.16/it/_images/mActionZoomIn.png) ![zoom_out](https://docs.qgis.org/3.16/it/_images/mActionZoomOut.png) Zoom della mappa (in alternativa utilizzare la rotella del mouse)
* ![zoom_all](https://docs.qgis.org/3.16/it/_images/mActionZoomFullExtent.png) Zoom sull'intera estensione della mappa
* ![zoom_select](https://docs.qgis.org/3.16/it/_images/mActionZoomToSelected.png) Zoom sull'elemento selezionato
* ![zoom_layer](https://docs.qgis.org/3.16/it/_images/mActionZoomToLayer.png) Zoom sul layer evidenziato
* ![info](https://docs.qgis.org/3.16/it/_images/mActionIdentify.png) Informazione sul singolo elemento del layer
* ![attribute_table](https://docs.qgis.org/3.16/it/_images/mActionOpenTable.png) Apre la tabella attributi del layer selezionato
* ![field_calculator](https://docs.qgis.org/3.10/it/_images/mActionCalculateField.png) Apre il calcolatore campi per il layer selezionato

## Pannello dei layer
La visualizzazione dei layer nel `Map Canvas` dipende dall'ordine degli stessi nel `Pannello dei Layer`.

### Entrambi i layer visualizzati, il layer `Reg01012019_WGS84` viene visualizzato sopra il layer `TCD_2015_020m_eu_03035_d05_E40N20`

![](../../../images/layer_case_1.png)
