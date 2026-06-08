# Raamatukogu

See on lihtne raamatukogu haldamise rakendus. Rakendus võimaldab hallata kasutajaid, otsida ja laenutada raamatuid ning vaadata statistikat.

## Tehnoloogiad

- Node.js
- Express.js
- CORS

## Käivitamine

1. Klooni repositoorium: `git clone https://github.com/DimaAllikvee/raamatukogu-lab.git`
2. Installi sõltuvused: `npm install`
3. Käivita server: `npm start`
4. Rakendus on kättesaadav aadressil: `http://localhost:3000`

## Testikasutajad

Rakenduses on eelseadistatud kaks testikasutajat (parool on mõlemal `1234`):
- Kasutajanimi: `mari` (Mari Maasikas)
- Kasutajanimi: `jaan` (Jaan Jansen)

## API endpointid

### Kasutajad

| Meetod | URL | Kirjeldus |
|--------|-----|-----------|
| POST | /api/users/signup | Registreerib uue kasutaja |
| POST | /api/users/login | Logib kasutaja sisse ja tagastab sessiooni tokeni |
| POST | /api/users/logout | Logib kasutaja välja |
| GET | /api/users/me | Tagastab sisselogitud kasutaja andmed |

### Raamatud

| Meetod | URL | Kirjeldus |
|--------|-----|-----------|
| GET | /api/books | Tagastab kõik raamatud |
| GET | /api/books/:id | Tagastab ühe raamatu andmed ID järgi |
| GET | /api/books/search | Otsib raamatuid autori (`?author=`) või pealkirja (`?title=`) järgi |
| GET | /api/books/genres | Tagastab kõik saadaolevad žanrid |
| GET | /api/books/genre/:genre | Tagastab kõik raamatud vastavas žanris |

### Laenud

| Meetod | URL | Kirjeldus |
|--------|-----|-----------|
| POST | /api/loans | Laenutab uue raamatu |
| POST | /api/loans/:id/return | Tagastab laenutatud raamatu |
| GET | /api/loans | Tagastab kõik laenud |
| GET | /api/loans/me | Tagastab sisselogitud kasutaja laenud |

## Testid

Automaattestide käivitamiseks jooksuta:
```bash
npm test
```
See käivitab kõik API testid, mis kontrollivad endpointide töökorda.

## GitHub Actions

Selles projektis on seadistatud GitHub Actions CI pipeline, mis käivitub automaatselt iga kord, kui pushitakse `main` harusse või luuakse Pull Request. Pipeline:
1. Installeerib Node.js ja sõltuvused
2. Käivitab serveri ja automaattestid (`npm test`)
3. Kontrollib koodi süntaksit
4. Kui testid ja lint läbivad edukalt, teavitab edukast testist.
