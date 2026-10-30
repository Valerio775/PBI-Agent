# Catalogo delle skill

Le skill sono cartelle in `.claude/skills/<nome>/` con un file `SKILL.md` (frontmatter con `name` e `description` + istruzioni). L'app le rileva automaticamente e le aggiorna ogni 10 secondi. Si invocano con slash command (es. `/count-mm-relationships`).

| Skill | Scopo | Output |
|---|---|---|
| `analyze` | Health check tecnico del modello aperto in Power BI Desktop | Report in chat / JSON in `reports/` |
| `analyze-description` | Spiega in linguaggio accessibile di cosa si occupa il modello, quali dati contiene e quali analisi supporta; permette la descrizione per tabella | Testo Markdown |
| `check-data-integrity` | Chiavi duplicate, valori orfani, chiavi vuote, colonne con troppi valori mancanti (query DAX) | Elenco di evidenze |
| `check-performance` | Cattura le query DAX durante una trace e mostra durata e tempo CPU | Tabella query; archiviabile su GitHub (`performance`) |
| `measure-performance` | Seleziona una misura DAX e ne misura il tempo di esecuzione | Tempi di esecuzione |
| `check-relationship-warnings` | Individua le relazioni molti-a-molti che generano l'avviso di Power BI Desktop | Coppie di tabelle e rischio |
| `count-mm-relationships` | Conta le relazioni molti-a-molti | Numero |
| `compare-model-snapshot` | Confronta il modello con uno snapshot TMDL salvato | Differenze su tabelle, colonne, misure, relazioni |
| `document-model` | Documenta tabelle, relazioni, misure e formule DAX | Workbook Excel in `Documentazione modello PBI/` |
| `extract-table-data` | Estrae le righe di una tabella in Excel (con limite di righe) | Excel in `Estrazione tabelle/` |
| `unused-dax-measures` | Trova le misure non usate nelle pagine/visual (richiede metadati PBIP) | Elenco misure inutilizzate |

## Regole comuni
- Tutte le risposte sono in italiano.
- Le skill non modificano il modello (operazioni di sola lettura).
- Le skill che usano Azure OpenAI seguono `.claude/skills/_shared/azure-openai.md`.
- Per i modelli Ollama il backend usa prompt di sistema ridotti (`OLLAMA_SKILL_PROMPTS`) e un sottoinsieme di tool MCP per skill, per limitare tempi e consumo di memoria.

## Come aggiungere una skill
1. Creare `.claude/skills/<nome>/SKILL.md` con frontmatter `name` e `description`.
2. Descrivere i passi, i tool MCP da usare e il formato di output.
3. Attendere l'aggiornamento automatico del catalogo (o ricaricare la pagina).
4. Se serve un comportamento specifico (tool consentiti, prompt Ollama, salvataggio file), aggiornare le mappe di configurazione in `mbi-agent-webapp/main.py`.
