# SomeBankingApp — Docker (esercitazione)

I servizi FastAPI e Angular girano in due container su `banking-net`.

## Avvio

```bash
docker compose config
docker compose up --build
```

- Frontend: http://localhost:4200
- API e Swagger: http://127.0.0.1:8000/docs

## Controlli

```bash
docker compose ps
docker compose logs -f frontend backend
docker compose exec frontend getent hosts backend
```

Per terminare: `Ctrl+C`, poi `docker compose down`.

Il frontend gira nel browser e chiama `http://127.0.0.1:8000` (non il nome Docker `backend`).
Il backend CORS permette `http://localhost:4200`: aprire il frontend a quell'indirizzo.
Il file `backend/bank.db` e' montato nel container; modifiche ai dati persistono sul Mac.

Uso didattico locale, non per pubblicazione su Internet.
