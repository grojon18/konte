# Oppgave 1 - Docker

## Oppgave A
Oppgaven inneholder nå en Dockerfile som bygger et Docker image ved å kjøre følgende kommando i terminalen.

```bash
   docker build . --tag konte
```

## Oppgave B

For å starte en container fra det nyeste container imaget som er laget, må sensor skrive inn følgende kommando i terminalen.
```bash
   docker run -d --name example-konte -p 8080:9999 konte:latest
```

Ved å bare skrive inn ```docker run konte:latest```, ville ikke dette fungert fordi vi må ha med port mapping spesifisert i ```-p 8080:9999```.
Vi gir navn til container med ```--name example-konte```, slik at dette ikke blir tilfeldig opprettet.
   

Når applikasjonen kjører i en Docker container med original kode vil den returnere en 404 - not found statuskode. Slik jeg tolker feilmeldingene skyldes dette at Docker ikke finner `index.html`-fila.
Dette løser jeg ved å tilpasse Dockerfile. Ved å legge til `COPY index.html .` i Dockerfile vil dette kopiere `index.html` inn i app directoriet også, slik at applikasjonen kan kjøre fila når vi kjører Docker.

Aksessering av http://localhost:8080 vil da fungere når vi kjører applikasjonen i Docker. 



