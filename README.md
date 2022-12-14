# Hvordan bruke docker for å sette opp en NGINX nettside.
***Forhåndsinformasjon***

Denne guiden antar at docker er allerede installert.

***Steg 1 - Forstå Dockerfilen***

Dockefilen er bygget opp av tre enkle setninger. Den første er "FROM nginx", den andre er "COPY content /usr/share/nginx/html" og den tredje er "COPY conf /etc/nginx". Den første setningen spesifiserer at nginx er foreldrebildet som alle videre kommandoer blir basert på. Den andre setningen kopierer innholdet i content mappen, som i vårt tilfelle inneholder index filen til nettsiden, til destinasjonen som er spesifisert. Den tredje setningen kopierer innholdet i conf mappen, som i vårt tilfelle er konfigurasjons filene til nettsiden, til destinasjonen som er spesifisert.

***Steg 2 - Bygge docker bildet***

For å bygge docker bildet som vi kommer til å bruke for å kjøre vår kontainer med nettsiden bruker vi "docker build -t nettside_bilde1 .". Denne kommandoen må bli kjørt i mappen som inneholder filen "Dockerfile". I kommandoen bruker vi "-t" som spesifiserer navnet til bilder vi lager.

***Steg 3 - Kjøre docker kontaineren***

Vi kjører ut docker kontaineren ved å bruke kommandoen "docker run --name minnettside -p 8080:80 -d nettside_bilde1". Hvorav i denne kommandoen spesifiserer "--name" navnet til kontaineren, "-p" spesifiserer hvilke porter eksterne porter som skal bli åpnet og til slutt "-d" som spesifiserer hvilket bilde som skal bli brukt.

***Steg 4 - Verifisere at nettsiden kjører***

For å sjekke at nettsiden fungerer som tiltenkt kan du bruke en nettleser og gå til "http://localhost:8080" eller "http://verts-ip-adressen:8080". En kan også verifisere at kontaineren kjører ved å bruke kommandoen "docker ps", hvis du tror kontaineren kan være i stoppet status kan legge til "-a" taggen.
