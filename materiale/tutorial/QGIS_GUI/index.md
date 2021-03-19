# GUI (Graphical User Interface) di QGIS

QGIS viene distribuito in due versioni principali  la versione più recente (allo stato attuale la 3.18) che però deve essere utilizzata solo da utenti avanzati per il testing, e la versione a lungo supporto LTR (attualmente la 3.16) che è la versione più stabile.

[Download QGIS](https://www.qgis.org/it/site/forusers/download.html)


## Istruzioni per Windows

Per gli utenti Windows esiste la possibilità di scaricare la versione Standalone installer che scarica QGIS con tutto il necessario per il funzionamento e l'OSGeo4W Network Installer che invece permette di selezionare quali pacchetti installare e di scaricare applicativi aggiuntivi (per utenti avanzati).

Si consiglia di scaricare la versione Standalone a lungo supporto. Prima di scaricare bisogna verificare l'archiettura del Sistema Operativo (32 bit o 64 bit). Per la verifica, recarsi nel **Pannello di controllo**, cliccare su **Sistema e sicurezza**, **Sistema** e verificare la versione in **Tipo di sistema**.


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
