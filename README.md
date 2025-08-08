# Nextcloud-AWS
In this repository is a step for step process of setting up your own cloud storage solution using Nextcloud on AWS

Schritt 1. AWS EC2-Instanz starten

AWS Management Console öffnen
Gehe zu https://aws.amazon.com und melde dich an.

2. EC2-Dashboard öffnen
Suche im Suchfeld oben nach „EC2“ und öffne den EC2-Dienst.

3. Instanz starten

Klicke auf „Instanzen“ > „Instanz starten“.

Gebe deiner Instanz einen Namen
z.B Nextcloud

Wähle ein Amazon Machine Image (AMI):

Wähle Ubuntu Server 22.04 LTS (oder eine ähnliche Version).

Wähle eine Instanzgröße (z.B. t3.micro für Testzwecke, kostenlos im AWS Free Tier).

Erstelle oder wähle ein bestehendes SSH-Schlüsselpaar (wichtig für die Verbindung!).
Name: keynextcloud

Danach auf "Schlüssel paar erstellen" dücken

Bei dem Punkt Netzwerk nach unten gehen und alle drei punkte aktivieren
"Allow SSH traffic from"
"Allow HTTPS traffic from Internet"
"Allow HTTP traffic from the internet"

Als nächstes beim Punkt Configure Storage (wenn man möchte)
die Größe von 1x8 auf = 1x30 erstellen, da wir im free tier die möglichkeit dazu haben

Starte die Instanz.

IP-Adresse notieren
Notiere die öffentliche IP der Instanz (z.B. 65.1.93.21), die du für die Verbindung und später für den Nextcloud-Zugriff brauchst.

Schritt 2: verbindung zur EC2-Instanz herstellen

Wir gehen auf unsere Instanz welche wir erstellt haben und copieren und die Public ip adresse z.B 65.1.93.21, danach auf "Connect" drücken 


Schritt 3: Nextcloud Installieren 
wir geben folgende befehle ein
1. sudo us
2.sudo apt update && sudo apt upgrade -y
3.sudo snap install nextcloud
4.snap changes nextcloud

Jetzt gehen wir auf unsere Instanz zurück und klicken auf die Instance-ID, dann auf den Networking bereich gehen und die Interface id anklicken. 
Dort wird die Security Group angezeigt, hier sollten wir drei sehen
Type
SSH
HTTPS
HTTP

Es wird jetzt eine Slap partichen erstellt, dafür gehen wir wieder zurück auf die Instanz mit der wir verbunden sind damit wir mehr 
Wir geben ein 
"HTOP
