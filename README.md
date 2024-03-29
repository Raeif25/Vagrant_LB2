M300 - LB2 Dokumentation Raeif Al Habash
===
Folgend Liste ich Ihnen meine Lernschritte im Modul 300 auf.

## Inhaltsverzeichnis
- [M300 - LB2 Dokumentation Raeif Al Habash](#m300---lb2-dokumentation-Raeif-Al-Habash)
  - [Inhaltsverzeichnis](#inhaltsverzeichnis)
- [K1](#k1)
  - [VirtualBox](#virtualbox)
  - [Vagrant](#vagrant)
  - [Visual Studio Code](#visual-studio-code)
  - [Git-Client](#git-client)
  - [SSH-Key](#ssh-key)
- [K2](#k2)
  - [GitHub Account](#github-account)
  - [Markdown](#markdown)
- [K3](#k3)
  - [Testen](#testen)
    - [Apache](#apache)
    - [Users and Groups](#users-and-groups)
    - [Ports](#ports)
- [K4](#k4)
  - [Firewall](#firewall)
  - [Reverse-Proxy](#reverse-proxy)
  - [Benutzer und Rechtevergabe](#benutzer-und-rechtevergabe)
  - [SSH](#ssh)
- [K5](#k5)
  - [Vergleich Vorwissen - Wissenszuwachs](#vergleich-vorwissen---wissenszuwachs)
  - [Reflexion](#reflexion)
_

K1
======

> [⇧ Nach oben](#inhaltsverzeichnis)
 
## VirtualBox

1. Als erstes habe ich auf [dieser Webseite](https://www.virtualbox.org) VirtualBox heruntergeladen und danach GUI-basiert installiert.
2. Danach habe ich den Ubuntu Desktop 16.04.05 auf [dieser Webseite](https://www.ubuntu.com/#download) heruntergeladen. 

Nachdem ich das ISO heruntergeladen habe, habe ich die VM erstellt:
1. VirtualBox starten
2. Mit einem klick auf `Neu` eine neue VM erstellen.
3. Als nächstes muss man folgende Attribute angeben:
   *  Name:           `M300_Ubuntu_XX.04_Desktop`
   *  Typ:            `Linux`
   *  Version:        `Ubuntu (64-bit)`
   *  Speichergrösse: `2048 MB`
   *  Platte:         `[X] Festplatte erzeugen`
4. Nun auf `Erzeugen` klicken
5. Im nächsten Fenster, folgende Informationen eintragen:
   *  Dateipfad:                       standard
   *  Dateigrösse:                     `10.00 GB`
   *  Dateityp der Festplatte:         `VMDK (Virtual Maschine Disk)`
   *  Storage on physical hard disk:   `dynamisch alloziert`
6. Nun erneut auf `Erzeugen` klicken, dann im Hauptmenü die VM anwählen (blau markiert) und den Punkt `Ändern` aufrufen
7. Im Abschnitt `Massenspeicher` den SATA-Controller anwählen und auf das CD+Symbol klicken
8. Unter `Medium auswählen` das zuvor heruntergeladene Systemabbild (ISO-Datei) anwählen
9. Alle Änderungen speichern und die VM starten
10. Nun den Installationsanweisungen der OS-Installation folgen. 

Nun ist die VM erstellt.

Danach habe ich in der Bash folgende Befehle ausgeführt.

1. Paketliste neu einlesen und Pakete aktualisieren:
   ```Shell 
   $  sudo apt-get update   #Paketlisten des Paketmanagement-Systems "APT" neu einlesen
   
   $  sudo apt-get update   #Installierte Pakete wenn möglich auf verbesserte Versionen aktualisieren

   $  sudo reboot           #System-Neustart durchführen
   ```
2. Software Controlcenter "Synaptic" installieren:
   ```Shell 
   $  sudo apt-get install synaptic
   ```
3. Nach erfolgreicher Installation in der Suche nach "Synaptic Package Manager" suchen und diesen starten
4. Innerhalb des Managers nach "apache" (Webserver-Programm) suchen und dieses (inkl. aller Abhängigkeiten) installieren
5. System-Neustart durchführen:
   ```Shell 
   $  sudo reboot
   ```
6. Danach habe geprüft, ob der Standard-Content des Webservers unter "http://127.0.0.01:80" erreichbar ist


## Vagrant
> [⇧ Nach oben](#inhaltsverzeichnis)

Zuerst habe ich Vagrant auf [dieser Webseite](https://www.vagrantup.com/ "vagrantup.com")   heruntergeladen und GUI-Basiert installiert.

Danach habe ich mit Vagrant eine VM erstellt.
1. Terminal öffnen
2. Einen neuen Ordner für die VM anlegen:
    ```Shell
      $ cd C:\Users\Raeif Al-Habash\M300-Services
      $ mkdir virtual boxen
      $ cd virtual boxen
     ```
3. Vagrantfile erzeugen, VM erstellen und starten:
    ```Shell
      $ vagrant box add http://10.1.66.11/vagrant/ubuntu/xenial64.box --name ubuntu/xenial64  #Vagrant-Box vom Netzwerkshare hinzufügen
      $ vagrant init ubuntu/xenial64        #Vagrantfile erzeugen
      $ vagrant up --provider virtualbox    #Virtuelle Maschine erstellen & starten
     ```
4. Die VM ist nun bereit und kann mit SSH-Zugriff bedient werden:
    ```Shell
      $ cd C:\Users\Raeif Al-Habash\M300-Services\virtual boxen     #Zum Verzeichnis der VM wechseln
      $ vagrant ssh                       #SSH-Verbindung zur VM aufbauen
     ```

Nachfolgend habe ich eine VM mit Apache Webserver von einem bereits abgeänderten File erstellt:

1. Terminal öffnen
2. In das M300-Verzeichnis wechseln:
    ```Shell
      $ cd C:\Users\Raeif Al-Habash\M300-Services\virtual boxen
     ```
3. VM erstellen und starten:
    ```Shell
      $ vagrant up
     ```
4. Danach habe ich im Webbrowser geprüft, ob der Standard-Content des Webservers unter "http://127.0.0.01:8080" (localhost) erreichbar ist
5. Später habe ich im Ordner `\web` die Hauptseite `index.html` editiert und das Resultat überprüft.
6. Abschliessend habe ich die VM wieder gelöscht:
   ```Shell
      $ vagrant destroy -f
    ```

## Visual Studio Code
> [⇧ Nach oben](#inhaltsverzeichnis)

In diesem Abschnit habe ich Visual Studio Code heruntergeladen, installiert und angewendet.

1. Ich habe Visual Studio Code auf [dieser](https://code.visualstudio.com/"visualstudio.com") Seite heruntergelden und GUI-basiert installiert.
2. Danach habe ich dem Editor drei wichtige Extensions hinzugefügt:

* Markdown All in One (von Yu Zhang)
* Vagrant Extension (von Marco Stanzi)
* vscode-pdf Extension (von tomiko1207)

Dazu habe ich folgende Anweisungen befolgt: 

  1. Visual Studio Code öffnen
  2. Die Tastenkombination `CTRL` + `SHIFT` + `X` drücken und in der Suchleiste die erwähnten Extensions suchen
  3. Auf `Install` klicken und anschliessend auf `Reload`, um die Extension in den Arbeitsbereich zu laden.

Um die Dokumentation lokal mit Visual Studio Code zu bearbeiten, arbeite ich folgendermassen:

  1. Änderungen am Readme-File von meinem Repositorys vornehmen
  2. Datei speichern und in der linken Leiste das Symbol mit einer "1" aufrufen
  3. Unter dem Abschnitt Changes die betroffenen Files bezüglich ihres Changes "stagen"
  4. Nachricht hinterlegen und Haken setzen
  5. Bei den 3 Punkten (...) auf Push klicken
  6. Warten, bis Dateien vollständig gepusht wurden

## Git-Client
> [⇧ Nach oben](#inhaltsverzeichnis)

Damit ich die Arbeiten lokal auf dem eigenen PC machen konnte, musste ich der sogenannte "Git Client", auf Windows "Git/Bash" installieren. 

Client installieren
Ich habe Client-Installation auf [dieser](https://git-scm.com/downloads) Seite heruntergeladen und GUI-basiert installiert.

Danach habe ich den Client konfiguriert:
1. Terminal öffnen
2. Git konfigurieren mit Informationen des GitHub-Accounts:
    ```Shell
      $ git config --global user.name "<username>"
      $ git config --global user.email "<e-mail>"
     ```

Damit ich das readme-File lokal bearbeiten kann, habe ich das Repository heruntergeladen und aktualisiert.

1. Terminal öffnen
2. Ordner für Repository erstellen:
    ```Shell
      $ cd C:\Users\Raeif Al-Habash\M300-Services\virtual boxen
      $ mkdir githublb2
     ```
3. Repository mit SSH klonen:
    ```Shell
      $ git clone git@github.com:Raeif25/Vagrant_LB2.git

      Cloning into 'lb2'...
     ```
4. Repository aktualisieren und Status anzeigen:
    ```Shell
      $ git pull

      Already up to date.
    ```

## SSH-Key 
> [⇧ Nach oben](#inhaltsverzeichnis)

Zuerst musste ich Lokal einen SSH-Key erstellen:

1.  Folgenden Befehl mit der Account-E-Mail von GitHub in Bash einfügen:
    ```Shell
      $  ssh-keygen -t rsa -b 4096 -C "raeif.alhabash.25@gmail.com"
    ```
2. Neuer SSH-Key wird erstellt:
    ```Shell
      Generating public/private rsa key pair.
    ```
3. Bei der Abfrage, unter welchem Namen der Schlüssel gespeichert werden soll, die Enter-Taste drücken (für Standard):
    ```Shell
      Enter a file in which to save the key (~/.ssh/id_rsa): [Press enter]
    ```
4. Nun habe ich ein Passwort für den Key festgelegt:
    ```Shell
      Enter passphrase (empty for no passphrase): [Passwort]
      Enter same passphrase again: [Passwort wiederholen]
    ```
Danach kann ich den SSH-Key dem Client hinzufügen:
1. Auf www.github.com im Benutzerkonto Settings aufrufen
2.  Unter den Menübereichen auf der linken Seite zum Abschnitt SSH und GPG keys wechseln
3.  Auf New SSH key klicken
4.  Im Formular unter Title die Bezeichnung MB SSH-Key vergeben
5.  Den Key von der Datei C:\Users\Raeif Al-Habash\.ssh\id_rsa.pub einfügen und auf Add SSH key klicken

SSH Zugriff auf VM

Um Zugriff via SSH auf die VM aufzubauen, muss man bloss einen kurzen Befehl eingeben.
```shell
vagrant ssh
```

_
K2
======
## GitHub Account
> [⇧ Nach oben](#inhaltsverzeichnis)

Ich habe folgendermassen einen Github Account erstellt:
1. Auf [GitHub.com](https://github.com) gehen
2. Auf Sign up klicken
3. Username, E-mail und Passwort eingeben sowie Aufgabe zum verifizieren lösen
4. Auf Create an Account klicken

## Markdown

Markdown
  ```Shell
+-----------------------+
| Websererver:          |
+-----------------------+
| IP-Adresse: 10.0.2.15 |
+-----------------------+
| Port: 80, 22          |
+-----------------------+
| NAT: 8080             |
+-----------------------+
```
K3
======

> [⇧ Nach oben](#inhaltsverzeichnis)
 
## Testen

### Apache
- Ich habe den Apache getestet, indem ich auf meinem Client die IP-Adresse der VM eingegeben habe. 
- Zudem habe ich das index.html geändert und geschaut ob es die Änderungen übernommen hat.
- Wenn man den folgenden Befehl eingibt, wird das index.html in der Shell angezeigt
    Shell
    curl -f [ip adress]
    

### Users and Groups
- Mit diesem Befehl habe ich alle Benutzer in der VM angezeigt und habe dann gesehen, das meine beiden User erstellt worden sind.
    ```Shell
    cut -d: -f1 /etc/passwd
    ```
- Mit diesem Befehl zeige ich die Gruppen in der VM an und sehe dann, ob die neue Group erstellt wurde.
    ```Shell
    cut -d: -f1 /etc/group
    ```
-  Die beiden Befehle oben kann man in einen zusammenfassen, indem man den User mit der dazugehörigen Group anzeigt:
    ```Shell
    cut -d: -f1 /etc/passwd | xargs groups
    ```

- Um zu testen, ob das Passwort geändert wurde, habe ich mich mit einem zuvor erstellten User eingeloggt.
    ```Shell
    su user01
    password: **
    ```

### Ports
- Um zu testen, ob es die Portkonfiguration übernommen hat,    habe ich folgenden Befehl eingegeben und gesehen, dass die im File angegebenen Ports offen sind.
    ```Shell
    netstat -an |grep LISTEN 
    ```
- In diesem Fall habe ich Port 80 für die Webseite und Port 22 für die SSH-Verbindung geöffnet. Dies kann man auch testen, indem man die Webseite aufruft und eine Verbindung via SSH aufbaut. 

K4
======

> [⇧ Nach oben](#inhaltsverzeichnis)
 
## Firewall

  Ich habe beim aufsetzen automatisch Firewall Regeln erstellt, indem ich die nötigen Zeilen ins Vagrantfile eingefügt habe:

1. Vagrantfile öffnen
2. Folgende Zeilen einfügen:
    ```Shell
      sudo apt-get install ufw
      sudo ufw allow 80/tcp
      sudo ufw allow 22/tcp
      sudo ufw allow out 22/tcp 
      sudo ufw enable
     ```

## Reverse-Proxy
Ich habe beim aufsetzen automatisch einen Reverse-Proxy installiert, indem ich die nötigen Zeilen ins Vagrantfile eingefügt habe:
1. Vagrantfile öffnen
2. Folgende Zeilen einfügen:
    ```Shell
    sudo apt-get -y install libapache2-mod-proxy-html
    sudo apt-get -y install libxml2-dev

    sudo a2enmod proxy
    sudo a2enmod proxy_html
    sudo a2enmod proxy_http
     ```

## Benutzer und Rechtevergabe

Ich habe beim aufsetzen automatisch User mit Passwort erstellt, indem ich die nötigen Zeilen ins Vagrantfile eingefügt habe:

1. Vagrantfile öffnen
2. Folgende Zeilen einfügen:
    ```Shell
      sudo groupadd testadmin
      sudo useradd user1 -g testadmin -m -s /bin/bash 
      sudo useradd user2 -g testadmin -m -s /bin/bash 
      sudo chpasswd <<<user1:abc123	
      sudo chpasswd <<<user2:abc123
    ```
## SSH

Ich habe beim aufsetzen automatisch ein SSH Zugang erstellt, indem ich die nötigen Zeilen ins Vagrantfile eingefügt habe:

1. Vagrantfile öffnen
2. Folgende Zeilen einfügen:
    ```Shell
      sudo apt-get -y install openssh-server
    ```

K5
======

> [⇧ Nach oben](#inhaltsverzeichnis)
 

## Vergleich Vorwissen - Wissenszuwachs

Bereits bekannt

- Virtualisierungen mit Linux und Windows habe ich schon sehr oft in Üks angeschaut, jedoch nur in der Letztes ÜK Modul automatisiert.
- Ich habe schon von GitHub gehört, jedoch habe ich dies nie würklich gebraucht oder angeschaut.

Neu

 - Virtualbox ist ein neues Programm für mich, obwohl es sich nicht sehr von VMWare unterscheidet.
 - Ich kannte Vagrant vor diesem Modul nicht, daher habe ich nur hinzugelernt
 - Auch mit Markdown bin ich zuvor nicht in Berührung gekommen.

Fazit

In der LB2 konnte ich sehr viel neues lernen. Die Auseinandersetzung mit Vagrant und Virtualbox hat mir sehr geholfen. Ich kenne nun verschiedene neue Befehle von Vagrant. Kann ein Vagrantfile erstellen und somit automatisiert VMs erstellen lassen. In meinem Arbeitsplatz kann ich dies gut gebrauchen, als ich in die Abteilung WindowsServer bin.

## Reflexion

Ich habe länger gebraucht um die LB2 fertig zu stellen. Da ich zu Beginn nicht ganz wusste wie ich vorgehen soll. zum Glück konnte ich mich mit meinen Mitlernenden austauschen und somit den Auftrag für mich klar formuliert zu bekommen. Nun fehlten nur noch die Befehle für das Vagrantfile und die Dokumentation musste geschrieben werden. Auf der Webseite VagrantCloud konnte ich mein Betriebssystem auswählen. Danach habe ich mithilfe der Dokumentation im Github weitere Befehle herausgefunden um das Vagrantgfile zu vervollständigen. Die restlichen Befehle konnte ich mithilfe des Internets und Kollegen herausfinden und ergänzen. Die Dokumentation via Markdown war auch, wie schon gesagt neu für mich. Daher hatte ich länger als wenn ich eine Word Dokumentation schreiben würde. Zum Glück gab es ein CheatSheet welches ich benutzen konnte somit war auch dies keine grosse bürde.
