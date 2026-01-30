# Prérequis  
Pour installer Grafana et GLPI, il faut faire 2 VM Debian 13 ou tout autre OS Linux. 

## Groupe : 
**R&D (Groupe 3)**
VITROU Vladimir / BRAUD Thomas / CAILLAUD Nino / MOLENDI Lucas / BROSSET Lilian / ALBERTEAU Théotim  

## Date : 
**26/01/2026 - 30/01/2026**

### Installation Debian 13
- Choisir Interface Graphique  

![](Images/debian.png)  

- Nommer la machine (ici celle de Grafana)  

![](Images/debian2.png)  

- Sélection du mot de passe root et du nom d'une session utilisateur  

![](Images/debian3.png)  
![](Images/debian4.png)

- Partionner le(s) disque(s)  
  
![](Images/debian5.png)  

- Sélection des logiciels, puis on termine l'installation 

![](Images/image.png)

## Grafana et Prometheus 
Pour l'installation de Grafana (attention avec un f), nous avons principalement suivi ce tutoriel de la documentation officielle de Grafana : [Tutoriel](https://grafana.com/docs/grafana/latest/fundamentals/getting-started/first-dashboards/get-started-grafana-prometheus/)  

### Prérequis  
Il faut installer sur OPNSense le plugins de node-exporter. Pour le trouver il faut aller dans System, Firmware, Plugins et il faut cocher "Show community plugins"  

![alt text](<Images/Capture d'écran 2026-01-30 120033.png>)

Attention, il faut avoir une version à jour de OPNSense ! 

### Installation et Configuration  

- Lancement de node_exporter  
 
![alt text](<Images/Capture d'écran 2026-01-30 134501.png>)  

- Lancement du container docker grafana  

![alt text](<Images/Capture d'écran 2026-01-30 134750.png>)  

- Contenu du fichier config scrape de prometheus

![alt text](<Images/Capture d'écran 2026-01-30 134912.png>)  

- Page de connexion a Grafana  

![alt text](<Images/Capture d'écran 2026-01-30 135111.png>)  

- Création de la data source Prometheus  

![alt text](<Images/Capture d'écran 2026-01-30 135209.png>)  

- Test des queries Prometheus, node_exporter et OPNSense  

![alt text](<Images/Capture d'écran 2026-01-30 135352.png>)  

- Les valeurs sont à 1, donc tout est activé 

![alt text](<Images/Capture d'écran 2026-01-30 135519.png>)  

### Création des Alertes 

- Alerte si l'interface WAN est down 

![alt text](<Images/Capture d'écran 2026-01-30 135917.png>)  

- Alerte en cas d'un CPU trop élevé  

![alt text](<Images/Capture d'écran 2026-01-30 135951.png>)  

- Alerte d’utilisation de la RAM élevée

![alt text](<Images/Capture d'écran 2026-01-30 140229.png>)  

- Alerte en cas de panne de la gateway de la VLAN20  

![alt text](<Images/Capture d'écran 2026-01-30 140528.png>)

- Alerte en cas de panne du DNS  

![alt text](<Images/Capture d'écran 2026-01-30 140904.png>)  

- Alerte en cas de panne de l'intranet(test avec 8.8.8.8)  
  
![alt text](<Images/Capture d'écran 2026-01-30 141216.png>)

- Statut de l’intranet DNS du panneau de configuration  

![alt text](<Images/Capture d'écran 2026-01-30 141638.png>)


## GLPI  
Pour l'installation de GLPI nous avons suivi ce tutoriel d'IT-Connect : [Tutoriel](https://www.it-connect.fr/installation-pas-a-pas-de-glpi-10-sur-debian-12/)  
 
- Nous avons choisi comme version de GLPI la : GLPI-11.0.5 et comme nom de domaine on met celui présent sur le tuto. Attention, dans notre cas, on accède à GLPI par localhost, car l'adresse est bloquée par le pare-feu Fortinet. 

### Installation et Configuration 

- Page d'installation de GPLI, une fois le service lancé et le tutoriel suivi. 

![alt text](<Images/Capture d'écran 2026-01-30 142048.png>)  

- Configuration de la connexion a la base de donnéees  

![alt text](<Images/Capture d'écran 2026-01-30 142242.png>)

- Test de connexion à la base de données. Il faut bien cocher notre base de données créée au préalable.  

![alt text](<Images/Capture d'écran 2026-01-30 142507.png>)

- Écran d'accueil après connexion  

![alt text](<Images/Capture d'écran 2026-01-30 142647.png>)

### Mise en place du Service Desk