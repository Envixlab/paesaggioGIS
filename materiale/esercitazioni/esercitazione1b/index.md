# Esercitazione #1b - Geoprocessing
## Overview
In questo esercizio imparerai ad utilizzare gli strumenti di Geoprocessing per effettuare un'analisi sulle caratteristiche del paesaggio dei siti di foraggiamento del Barbagianni comune (*Tyto alba*). Il Dataset deriva dal database OpenMice ([Paniccia et al. 2018](https://esajournals.onlinelibrary.wiley.com/doi/full/10.1002/ecy.2506)) e contiene la distribuzione e l'abbondanza dei piccoli mammiferi (eulipotifli e roditori) derivata dalla raccolta delle borre di vari rapaci notturni.

[Download del Dataset](https://github.com/Envixlab/paesaggioGIS/raw/master/dataset/esercitazione_1b.zip)

### Caricamento del dataset
Creare una cartella \paesaggioGIS\esercizio_1b nel percorso C:\paesaggioGIS\esecizio_1b e copiare all'interno i dataset presence_points e uso_suolo (.shp, .shx, .dbf, .prj). Aprire QGIS, creare un nuovo progetto e salvarlo nella cartella appena creata.

### Creazione dei siti di foraggiamento
Viene stimato che l'estensione media del territorio di caccia del Barbagianni comune sia pari a circa 3 km<sup>2</sup>. Bisogna creare, quindi, un buffer circolare intorno ai presence_points di 1000 metri di raggio.

`Vettore -> Strumenti di Geoprocessing -> Buffer`

* `Layer in ingresso`: presence_points
* `Distanza`: 1000
* `Risultato da operazione di buffer`: Salvare il file all'interno della cartella di output e chiamarlo `foraging_areas`

Per ogni sito di foraggiamento si deve estrarre l'informazione relativa all'uso e copertura del suolo. Il dataset da utilizzare è `uso_suolo`. Per maggiori informazioni sul dataset consultare l'[esercitazione#3](/materiale/esercitazioni/esercitazione3/index).

`Vettore -> Strumenti di Geoprocessing -> Ritaglia`

* `Layer in ingresso`: foraging_areas
* `Layer di sovrapposizione`: uso_suolo
* `Ritagliato`: Salvare il file all'interno della cartella di output e chiamarlo `foraging_areas_land_cover`

Per ogni area di foraggiamento abbiamo l'informazione sull'uso e copertura del suolo. L'obiettivo è avere una visione generale della copertura del suolo, quindi l'informazione va aggregata. Utilizzare lo strumento `Dissolvi`.

`Vettore -> Strumenti di Geoprocessing -> Dissolvi`
* `Layer in ingresso`: foraging_areas_land_cover
* `Campo dissolvenza`: Andreson
* `Dissolto`: Salvare il file all'interno della cartella di output e chiamarlo `foraging_areas_land_cover_dissolved`

Bisogna calcolare la superficie percentuale delle diverse tipologie di uso e copertura del suolo all'interno delle aree di foraggiamento. Aprire il `calcolatore di campi` utilizzando l'apposito comando `Apri Calcolatore di Campi` ![field_calculator](https://docs.qgis.org/3.10/it/_images/mActionCalculateField.png).

* `Crea un nuovo campo`
* `Nome campo in uscita`: sup_perc
* `Tipo di campo`: Numeri decimali
* `Lunghezza campo in uscita`: 10
* `Precisione`: 2

La percentuale è uguale alla somma delle superfici della categoria di interesse diviso la somma di delle suoerfici di tutte le categorie presenti, moltiplicato per 100.

![\Large P_i = \frac{\sum\limits_{j=1}^n a_ij}{A}(100)](http://latex.codecogs.com/svg.latex?P_i&space;=&space;\frac{\sum\limits_{j=1}^n&space;a_ij}{A}(100))

* P<sub>i</sub> è la proporzione della paesaggio occupata dalla categoria i
* a<sub>ij</sub> è l'area in m<sup>2</sup> della categoria ij
* A è la superficie totale del paesaggio

Tramite il `Dissolvi` abbiamo già aggregato i poligoni appartenti alle diverse categorie. L' espressione da utilizzare nel calcolatore campi è:

`$area/sum($area)*100`
