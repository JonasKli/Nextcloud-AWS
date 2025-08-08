# Nextcloud-AWS
In this repository is a step for step process of setting up your own cloud storage solution using Nextcloud on AWS

1. AWS EC2-Instanz starten

AWS Management Console öffnen
Gehe zu https://aws.amazon.com und melde dich an.

2. EC2-Dashboard öffnen
Suche im Suchfeld oben nach „EC2“ und öffne den EC2-Dienst.

3. Instanz starten

Klicke auf „Instanzen“ > „Instanz starten“.

Wähle ein Amazon Machine Image (AMI):

Wähle Ubuntu Server 22.04 LTS (oder eine ähnliche Version).

Wähle eine Instanzgröße (z.B. t2.micro für Testzwecke, kostenlos im AWS Free Tier).

Konfiguriere Netzwerk und Storage (Standard ist meistens in Ordnung).

Erstelle oder wähle ein bestehendes SSH-Schlüsselpaar (wichtig für die Verbindung!).

Starte die Instanz.

IP-Adresse notieren
Notiere die öffentliche IP der Instanz (z.B. 65.1.93.21), die du für SSH und später für den Nextcloud-Zugriff brauchst.
