# /check-performance: P_Management

Generato il 02/11/2026 14:17

Schermata o controllo: **test p_management**
Modello: **P_Management**
Eventi trace: 30; query DAX individuate: 10.

## Query ordinate per durata
- #1: **7306 ms** (CPU 844 ms). Espressioni DAX: Jira Adoption KPI3
- #2: **6915 ms** (CPU 797 ms). Espressioni DAX: Commento Den KPI3
- #3: **6910 ms** (CPU 1281 ms). Espressioni DAX: Jira Adoption KPI3
- #4: **6006 ms** (CPU 953 ms). Espressioni DAX: DEBUG num KPI3
- #5: **5736 ms** (CPU 1375 ms). Espressioni DAX: DEBUG num KPI3, DEBUG den KPI3, Jira Adoption KPI3
- #6: **5693 ms** (CPU 1172 ms). Espressioni DAX: DEBUG num KPI3, Numero righe Jira Epic, 'Jira Feature Delivery'[Jira FD URL]
- #7: **5686 ms** (CPU 906 ms). Espressioni DAX: DEBUG den KPI3, Numero righe Jira Epic, 'Jira Feature Delivery'[Jira FD URL]
- #8: **5502 ms** (CPU 1000 ms). Espressioni DAX: Commento Num KPI3
- #9: **5494 ms** (CPU 781 ms). Espressioni DAX: Last data
- #10: **5467 ms** (CPU 734 ms). Espressioni DAX: DEBUG den KPI3

## Possibili cause della query più lenta
- La CPU lavora poco rispetto alla durata: la query ha atteso. Cause tipiche: sorgente DirectQuery lenta, altre query in coda nello stesso momento o un refresh in corso. Ripeti la misura a modello "fermo".

Il DAX completo non è incluso nel file.
