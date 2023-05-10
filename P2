# Praktische Lernziele P2

 
## Dockerfiles

### Syntax

Die Syntax eines Dockerfiles ist ein Satz von Anweisungen, die Docker verwendet, um ein Docker-Image zu bauen. Jede Anweisung im Dockerfile führt eine bestimmte Aktion aus, um das Image zu erstellen. Hier sind einige der grundlegenden Syntaxelemente, die in einem Dockerfile verwendet werden:

* `FROM`: Definiert die Basis des Images, auf dem das neue Image aufgebaut wird.
* `RUN`: Führt eine Befehlszeile innerhalb des Containers aus.
* `COPY` und `ADD`: Kopiert Dateien und Verzeichnisse aus dem Host in das Image.
* `WORKDIR`: Setzt das Arbeitsverzeichnis innerhalb des Containers.
* `EXPOSE`: Offenbart einen Port innerhalb des Containers.
* `CMD` oder `ENTRYPOINT`: Definiert den Befehl, der beim Starten des Containers ausgeführt wird.

### Chaining
In einem Dockerfile wird das Symbol "&" normalerweise verwendet, um mehrere Befehle in einer einzigen Zeile zu kombinieren. Diese Technik wird als "chaining" bezeichnet und hilft, die Größe des Docker-Images zu reduzieren, indem unnötige Schritte und temporäre Dateien vermieden werden.

Ein Beispiel dafür ist das Verketten mehrerer Befehle, um den Container zu aktualisieren und erforderliche Pakete zu installieren. Anstatt dies in zwei separaten Zeilen zu tun, kann man diese in einer Zeile zusammenführen, indem man das Symbol "&" verwendet:
```txt
RUN apt-get update && \
    apt-get install -y package1 package2 package3
```
In diesem Beispiel wird der Container zuerst aktualisiert und dann werden die Pakete installiert. Durch die Verwendung des `&` Symbols kann man diese beiden Schritte in einer Zeile kombinieren.

Es ist jedoch zu beachten, dass das Verketten von Befehlen mit "&" in manchen Fällen zu Problemen führen kann, insbesondere wenn eine der Anweisungen fehlschlägt. In diesen Fällen ist es möglicherweise besser, separate Zeilen zu verwenden, um die Ausführung der Befehle sicherzustellen.

Hier ist eine Syntax, um eine Webseite zu hosten:

```txt
FROM httpd:2.4
COPY ./public-html/ /usr/local/apache2/htdocs/
```

Speichern Sie diese Datei als `Dockerfile` in einem Verzeichnis auf Ihrem Host-Computer.

### Bauen Sie das Docker-Image

Jetzt, da wir unser Dockerfile haben, können wir das Docker-Image erstellen. Öffnen Sie ein Terminal und navigieren Sie zum Verzeichnis, das Ihr `Dockerfile` enthält. Führen Sie dann den folgenden Befehl aus:

```txt
docker build -t my-apache2 .
```

Dies erstellt das Docker-Image mit dem Tag `my-apache2`.

### Schritt 3: Führen Sie den Docker-Container aus

Sobald das Docker-Image erstellt ist, können wir den Container ausführen. Hier ist ein Beispielbefehl, um den Container auszuführen und den Port 8080 auf unseren Host-Computer zu mappen:
```txt
sudo docker run -d -p 8080:80 -v /var/log/mywebsite/var/log/mywebsite my-apache2:latest
```

Dies startet den Container und macht den phpmyadmin-Webserver über Port 8080 auf Ihrem Host-Computer zugänglich. Das `-v` im Befehl sorgt dafür, dass ein separates volume auf der Hostmaschine angelegt wird, in der die Logdateien abgelegt werden. 


## Docker-Compose

Docker Compose ist ein Tool, das es ermöglicht, Docker-Anwendungen mithilfe einer YAML-Datei zu definieren und zu starten. Es ist eine Erweiterung von Docker, die es einfacher macht, mehrere Docker-Container als eine einzige Anwendung zu verwalten.

Mit Docker Compose kann man verschiedene Container miteinander verknüpfen, um eine komplette Anwendungsumgebung bereitzustellen. Dies ist besonders nützlich für Anwendungen, die aus mehreren Diensten bestehen und eine gemeinsame Infrastruktur wie eine Datenbank oder einen Message-Broker benötigen.

### YAML-Datei

Die YAML-Datei muss immer den Namen `docker-compose` besitzen. in ihr werden alle Parameter des Docker-Compose mitgegeben


Die Yaml Datei kann etwa so aussehen:

```txt
services:
  wordpress:
    image: wordpress
    links:
      - mariadb:mysql
    environment:
      - WORDPRESS_DB_PASSWORD_FILE=/run/secrets/pw
      - WORDPRESS_DB_USER=root
    ports:
      - "127.0.0.1:80:80"
    volumes:
      - ./html:/var/www/html
    secrets: 
      - pw 

  mariadb:
    image: mariadb
    environment:
      - MYSQL_ROOT_PASSWORD_FILE=/run/secrets/pw
      - MYSQL_DATABASE=wordpress
    volumes:
      - ./database:/var/lib/mysql
    secrets:
      - pw 

secrets:
  pw:
    file: pw.txt

 ```
 
Tipp: Korrigiere code mit: https://www.yamllint.com/
### Ausführen des Docker Compose:
Docker compose ist nicht auf jeder VM schon vorinstalliert. Um es zu installieren verwenden wir diesen Befehl:

```txt
sudo curl -L https://github.com/docker/compose/releases/download/1.24.0/docker-compose-$(uname -s)-$(uname -m) -o /usr/local/bin/docker-compose
```
Danach ist es wichtig, dem User Berechtigung auf den Ordner zu geben, in dem die Datei liegt:

```txt
sudo chmod +x /usr/local/bin/docker-compose
```

Ausühren 
```txt
docker compose up -d
```
Mit `docker-compose -v` werden alle laufenden compose setups angezeigt
```txt
docker-compose -v
```


# Beenden des compose-setup
Als erstes muss man in das im terminal ins Verzeichnis Navigieren, in dem das Setup operiert.
Das Setup kann mit folgendem Befehl gestoppt werden:
```txt
docker-compose down
```
