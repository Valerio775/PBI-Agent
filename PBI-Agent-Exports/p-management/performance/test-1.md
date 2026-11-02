# Performance snapshot: Test 1

- Modello: P_Management
- Acquisizione: 2026-11-02T12:42:27+01:00
- Eventi acquisiti: 60
- Query DAX: 20

| # | Query | Durata (ms) | CPU (ms) | Impronta DAX |
|---:|---|---:|---:|---|
| 1 | Espressioni DAX: Data from Approved BF, COUNT Approved Confirm Released | 3907.0 | 813.0 | `47a754aeb8f6ecca` |
| 2 | Espressioni DAX: BF Tech Progress | 3261.0 | 891.0 | `9e77b027070c7dd0` |
| 3 | Espressioni DAX: Conteggio BF Authorized in su | 3171.0 | 844.0 | `09361ce743993512` |
| 4 | Espressioni DAX: COUNT Approved Confirm Released | 3099.0 | 688.0 | `4f8031345423fc3b` |
| 5 | Espressioni DAX: COUNT Approved Confirm Released, AVG Approved Confirm Released | 3074.0 | 672.0 | `44f002b47108d6b1` |
| 6 | Espressioni DAX: Conteggio BF | 3065.0 | 844.0 | `d50172e3073d3e2e` |
| 7 | Espressioni DAX: Last data | 3048.0 | 844.0 | `e66b6e989319a109` |
| 8 | Espressioni DAX: Min Creation date, Max Creation date | 3040.0 | 688.0 | `6f5abdd3f000ec2b` |
| 9 | Espressioni DAX: BF Tech Progress, Conteggio BF | 2588.0 | 703.0 | `fbc8d100e03a7318` |
| 10 | Espressioni DAX: From BF, To Status BF, Filtro Tabella Dinamica BF | 2423.0 | 563.0 | `531bc27d242ee99c` |
| 11 | Espressioni DAX: Conteggio BF | 2348.0 | 422.0 | `55fa831930fdfdc4` |
| 12 | Espressioni DAX: AVG Approved Confirm Released | 2322.0 | 359.0 | `4ccc9e256d8f8afd` |
| 13 | Espressioni DAX: Titolo grafico BF | 772.0 | 672.0 | `e745a6dbbbab6e58` |
| 14 | Espressioni DAX: COUNT In Progress Rf UAT, AVG In Progress Rf UAT | 716.0 | 500.0 | `93788b4dc2e7e7d6` |
| 15 | Espressioni DAX: COUNT In Progress Rf UAT | 713.0 | 438.0 | `2987be40b12da911` |
| 16 | Espressioni DAX: AVG In Progress Rf UAT | 685.0 | 391.0 | `70e778742fe5b251` |
| 17 | Tabelle coinvolte: Jira Business Feature 2, Filtri_grafici_MBI_IE, Quantità_MBI_IE | 256.0 | 250.0 | `ebae8bf08397828c` |
| 18 | Tabelle coinvolte: Jira Business Feature 2, Filtri_grafici_MBI_IE, Assex_MBI_IE | 255.0 | 250.0 | `7f98afb7e698e0d6` |
| 19 | Tabelle coinvolte: Jira Business Feature 2, Filtri_grafici_MBI_IE, Trend_MBI_IE | 254.0 | 250.0 | `262101403d1429a7` |
| 20 | Tabelle coinvolte: Jira Business Feature 2, Filtri_grafici_MBI_IE, Tabella_MBI_IE | 222.0 | 234.0 | `ba40a25ff0ddd71d` |

Il DAX completo non viene archiviato. La stessa schermata aggiorna questi file; usa la cronologia GitHub per confrontare le versioni.
