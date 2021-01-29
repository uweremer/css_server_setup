# BW-Cloud Server nutzen

![bwcloud-logo](https://www.bw-cloud.org/themes/bw-cloud/images/bwcloud_logo_blau_weiss_little.svg)

Der Server der Abteilung ist erreichbar unter IP `193.196.39.179`.  Es handelt sich um eine VM Instanz in der OpenStack Umgebung der der [bwcloud](www.bw-cloud.org). Wir haben 16 Kerne und 32 GB RAM. Speicher ist leider begrenzt. Bis zu 100 GB stehen unter folgendem Pfad zur Verfügung: `/mnt/hdd2` (je nach dem wie viel schon belegt ist).

Auf dem Server läuft ein R-Studio Server, dieser ist erreichbar unter: http://193.196.39.179:8787.

Außerdem ist Python 3.6 installiert. Dieses kann per SSH Terminal genutzt werden (s.u.). Wenn Python mit zusätzlichen Libraries genutzt werden soll, bitte nutzt dafür `venv` für eine virtuelle Umgebung (e.g.: https://realpython.com/python-virtual-environments-a-primer/).



## Verbindung herstellen mit SSH

Um auf den Server zuzugreifen muss man sich per SSH verbinden (z.B. mit [Putty](https://www.putty.org/)). 

- In Putty muss bei `Host Name` die IP Adresse angegebe werden: `193.196.39.179`
- Dann muss ein SSH-Schlüssel zur Authentifizierung genutzt werden (siehe [hier](https://www.bw-cloud.org/de/erste_schritte#step4)). Der private Schlüßel unserer Abteilung liegt auf unserem Netzlaufwerk: `.\Projekte\BWCloudServer\S7Server_private_key.ppk`. Dieser muss in Putty importiert werden: `Connection -> SSH -> Auth`. 
- Schließlich muss noch der Benutzername angegeben werden: `Connection -> Data -> auto-login username`. Er lautet `centos`. 

Dann lässt sich mit `open` die Verbindung herstellen. 


## Dateitransfer mit pscp

Um Dateien von und zum Server zu schicken, lässt sich das Tool `pscp` nutzen, das mitinstalliert wird, wenn man Putty auf dem Windows-Rechner installiert.
`pscp` wird von  der Kommandozeile aus gestartet. Um eine Datei *vom Server auf den lokalen Rechner zu kopieren*, auf dem Windows-Rechenr also `cmd` ausführen. Dann:

```
pscp -i "Pfad_zum_private_key" nutzername@server_IP:/Dateipfad/auf/Server/datei.txt C:\Zielpfad\auf\Windows-Rechner
```

Um eine Datei *auf den Server zu kopieren*, wieder `cmd` und dann: 

```
pscp -i "Pfad_zum_private_key" C:\Quelldatei\auf\Windows-Rechner\datei.txt nutzername@server_IP:/Zielpfaf/auf/Server/ 
```



