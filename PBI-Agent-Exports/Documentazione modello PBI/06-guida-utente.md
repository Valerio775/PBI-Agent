# Guida utente

La pagina offre un tour guidato dal pulsante **Guida all'utilizzo** (in alto).

## Accesso
Al login si sceglie il provider: GitHub Copilot, Azure OpenAI oppure Ollama locale. "Entra senza login" consente solo di consultare il catalogo.

## Aree dell'interfaccia
1. **Barra superiore**: numero di skill rilevate, stato del collegamento GitHub, Archivio GitHub, Logout.
2. **Archivio GitHub**: collega il repository in cui salvare documenti e report (token, repository, branch, cartella; i campi repository e cartella sono protetti da un lucchetto).
3. **Catalogo skills** (colonna sinistra): ricerca per nome o parola chiave, filtro per categoria, clic su una skill per selezionarla.
4. **Area risposte**: mostra richiesta e risposta dell'agent in Markdown (tabelle, elenchi, risultati).
5. **Chat per scrivere la skill**: campo di input con suggerimenti dei comandi; *Invia*, *Stop*, *Clear*.
6. **Cronologia** (colonna destra): richieste già eseguite, raggruppate per modello Power BI; clic per riutilizzarle, *Svuota* per cancellarle.

## Uso tipico
1. Aprire il modello in Power BI Desktop.
2. Selezionare una skill dal catalogo o digitare, ad esempio, `/analyze NomeModello`.
3. Se richiesto, scegliere il modello o la tabella dal selettore proposto.
4. Leggere il risultato; per `document-model` ed `extract-table-data` viene creato un file Excel e, con l'archivio attivo, caricato su GitHub.

## Esempi di comandi
- `/analyze` – health check tecnico
- `/analyze-description` – descrizione funzionale del modello
- `/check-data-integrity` – controlli sui dati
- `/count-mm-relationships` – numero di relazioni molti-a-molti
- `/document-model` – documentazione in Excel
- `/check-performance` – trace delle query DAX (avvio e stop dal selettore)
