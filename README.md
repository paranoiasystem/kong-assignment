# Kong Assignment

## 1. Local playground with Docker Compose

> NOTA: Alcune immagini Docker fornite da Kong, nello specifico i servizi KongAir, sono sono buildate bene per architettura arm64, la mia soluzione è stata gi aggiungere come submodule il repo di KongAir e modificare a mano i Dockerfile dei servizi: bookings, customer e experience.
> Ho modificato nei Dockerfile la riga:
>
> `ADD https://github.com/krallin/tini/releases/download/${TINI_VERSION}/tini /tini` 
>
> con 
>
> `ADD https://github.com/krallin/tini/releases/download/${TINI_VERSION}/tini-arm64 /tini`