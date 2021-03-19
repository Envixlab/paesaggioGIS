# GUI (Graphical User Interface) di QGIS

![sistema](../../../images/gui.png)

1. Barra dei menu
2. Barra degli strumenti
3. Pannello dei Layer: nei GIS i dati geografici (sia raster che vettoriali) vengono gestiti secondo la struttura dei layer (o strati). Un layer può contenere un solo tipo di dato (es. puntuale, lineare, areale, raster)
4. Pannello del browser: permette di navigare nelle cartelle del computer
5. Map Canvas
6. Barra di stato

Per la lista completa delle funzioni dei menu, consultare nel manuale utente di QGIS, la sezione [QGIS GUI](https://docs.qgis.org/3.16/it/docs/user_manual/introduction/qgis_gui.html). Di seguito la lista dei comandi che verrà utilizzata maggiormente durante il corso.

## Barra dei menu

* Dal menu `Progetto` è possibile crea un nuovo progetto, salvarlo, settare le impostazioni del progetto corrente, creare un layout di stampa


![sistema](../../../images/sistema.png)


## Istruzioni per Linux (Distribuzioni Debian/Ubuntu)

Aggiungere alla fine del file le seguenti linee

```
sudo nano /etc/apt/source.list
```

```
#QGIS 3.16
deb https://qgis.org/ubuntu-ltr codename main
deb-src https://qgis.org/ubuntu-ltr codename main
```

Sostituire codename con la versione di ubuntu/debian in possesso (es. bionic, xenial, focal, ...)

Aggiornare i pacchetti di ubuntu/debian e installare QGIS

```
sudo apt update
sudo apt-get install qgis python3-qgis qgis-plugin-grass
```

In caso di errori al server delle chiavi, aggiungere la chiave pubblica del repository di QGIS e reinstallare.

```
wget -O - https://qgis.org/downloads/qgis-2020.gpg.key | gpg --import
gpg --fingerprint F7E06F06199EF2F2
```

```
gpg --export --armor F7E06F06199EF2F2 | sudo gpg --no-default-keyring --keyring gnupg-ring:/etc/apt/trusted.gpg.d/qgis-archive.gpg --import
sudo chmod a+r /etc/apt/trusted.gpg.d/qgis-archive.gpg
```

## Istruzioni per Mac OS

Sul sito di QGIS sono presenti gli installer pronti per le versioni del sistema operativo MacOS. Valgono le stesse considerazioni fatte per windows ossia l'installazione della versione LTR.
