# Performance snapshot: test performance

- Modello: Dashboard HSEQ_v0.3
- Acquisizione: 2026-10-20T15:51:11+02:00
- Eventi acquisiti: 24
- Query DAX: 8

| # | Query | Durata (ms) | CPU (ms) | Impronta DAX |
|---:|---|---:|---:|---|
| 1 | Valori: Tooltip solo linea, Countid, Totale NCO | 311.0 | 94.0 | `15184670dec6f0a9` |
| 2 | Valori: Countid, 'Inspection'[location description], 'Inspection'[Formatted scope] | 296.0 | 31.0 | `d5f5114834415cd0` |
| 3 | Valori: Countid, Totale NCO | 290.0 | 78.0 | `ace83fd3bcab499c` |
| 4 | Valori: Countid | 287.0 | 109.0 | `34bb8bfdd4b41bdf` |
| 5 | Valori: Detection rate | 226.0 | 31.0 | `45f8bc93224700c5` |
| 6 | Valori: Totale NCO | 224.0 | 31.0 | `3ca9765b52af4fd3` |
| 7 | Valori: Totale NCO | 201.0 | 94.0 | `d7c06b4c50cd7fc9` |
| 8 | Valori: Totale Ispezioni | 198.0 | 47.0 | `eb92ec4c1b32b83e` |

Il DAX completo non viene archiviato. La stessa schermata aggiorna questi file; usa la cronologia GitHub per confrontare le versioni.
