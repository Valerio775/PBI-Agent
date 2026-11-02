# Performance snapshot: test 3

- Modello: P_Management
- Acquisizione: 2026-11-02T13:06:59+01:00
- Eventi acquisiti: 18
- Query DAX: 6

| # | Query | Durata (ms) | CPU (ms) | Impronta DAX |
|---:|---|---:|---:|---|
| 1 | Espressioni DAX: Giorni in Stato, Filtro Issue per Fase Selezionata | 7059.0 | 781.0 | `c33c3365812d407f` |
| 2 | Espressioni DAX: MBI Tempo Storico Medio nello Stato Semplificato, MBI Giorni Issue Selezionata per Stato TEST, Conteggio Pass Through Semplificato 2 | 5334.0 | 797.0 | `0377bfcff60f21a1` |
| 3 | Espressioni DAX: Last data | 4068.0 | 484.0 | `8b1eb7f83cefe65b` |
| 4 | Espressioni DAX: Icon info | 4057.0 | 500.0 | `f98dafc7eaaa5d4a` |
| 5 | Espressioni DAX: Min Issue created date, Max Issue created date | 3895.0 | 578.0 | `b76bd8917453752e` |
| 6 | Espressioni DAX: Destinazione Dinamica 2 | 507.0 | 484.0 | `6c3198382a87ed02` |

Il DAX completo non viene archiviato. La stessa schermata aggiorna questi file; usa la cronologia GitHub per confrontare le versioni.
