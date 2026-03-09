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

## 2. Service and routing model

Genero i file di configurazione per Kong a partire dalle specifiche OpenAPI dei servizi.
```bash
deck file openapi2kong --spec KongAir/flight-data/flights/openapi.yaml --output-file kong/kongair-flights.yaml
deck file openapi2kong --spec KongAir/sales/customer/openapi.yaml --output-file kong/kongair-customer.yaml
deck file openapi2kong --spec KongAir/sales/bookings/openapi.yaml --output-file kong/kongair-bookings.yaml
deck file openapi2kong --spec KongAir/flight-data/routes/openapi.yaml --output-file kong/kongair-routes.yaml
```

Bisogna modificare i file generati per aggiungere le informazioni di routing, in modificare l'host, il path di ogni servizio, il protocollo e le porte.

Eseguo il comando per sincronizzare la configurazione con Kong:
```bash
deck gateway sync kong/*.yaml
```

## 6. kong dbless mode

Per eseguire Kong in modalità dbless esporto la conf attuale così:

```bash
deck gateway dump -o kong_dbless.yaml
``` 