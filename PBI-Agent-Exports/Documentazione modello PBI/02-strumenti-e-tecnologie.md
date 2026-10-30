# Strumenti e tecnologie

## Stack applicativo

| Ambito | Tecnologia |
|---|---|
| Linguaggio backend | Python 3.10+ (immagine Docker: 3.12) |
| Framework web | FastAPI + Uvicorn |
| Validazione | Pydantic |
| Client HTTP / AI | `httpx`, `openai` (client compatibile OpenAI) |
| Configurazione | `python-dotenv` (file `.env`) |
| Export Excel | `openpyxl` |
| Integrazione MCP | libreria `mcp` (client stdio) |
| Autenticazione Azure | `azure-identity` (`DefaultAzureCredential`) |
| Database | SQLite (`pbi_agent.sqlite3`) |
| Frontend | HTML, CSS e JavaScript vanilla, rendering Markdown (nessun framework) |
| Container | Docker, Helm, OpenShift, oauth2-proxy |

## Server MCP: Power BI Modeling MCP
- Nome predefinito: `powerbi-modeling-mcp` (variabile `POWERBI_MCP_NAME`).
- Comunicazione via **stdio** con l'eseguibile avviato con `--start`.
- Il backend lo individua, in quest'ordine:
  1. `POWERBI_MCP_COMMAND` (+ `POWERBI_MCP_ARGS`) nel `.env`;
  2. `.mcp.json` o `.vscode/mcp.json` del progetto;
  3. estensione VS Code "Power BI Modeling MCP" in `~/.vscode/extensions`.
- Permette di collegarsi a istanze locali di Power BI Desktop (o a modelli in Fabric) ed eseguire operazioni sul modello.
- Famiglie di tool usate dalle skill: `connection_operations`, `database_operations`, `model_operations`, `table_operations`, `column_operations`, `measure_operations`, `relationship_operations`, `dax_query_operations`, `trace_operations`.
- `REQUIRE_POWERBI_MCP=true` rende il server obbligatorio all'avvio.
- Le skill sono in **sola lettura** sul modello, salvo diversa indicazione nella skill.

## Modelli AI supportati
L'utente sceglie il provider al login.

| Provider | Uso | Note |
|---|---|---|
| **GitHub Copilot** (predefinito) | Accesso con token GitHub, modello `auto` o scelto dall'elenco | Richiede il permesso *Copilot Requests* e crediti Copilot; endpoint logico `copilot-sdk://github` |
| **Azure OpenAI** | Endpoint `https://Scriba.services.ai.azure.com/openai/v1`, deployment `gpt-5.4-mini` | Autenticazione con chiave API o `DefaultAzureCredential` (scope `https://ai.azure.com/.default`) |
| **Ollama (locale)** | Modelli sul PC, endpoint `http://127.0.0.1:11434/v1` (es. `qwen3:8b`, `qwen3:4b`) | Nessun dato inviato in cloud; richiede modelli con supporto tool; abilitabile con `OLLAMA_ENABLED` |
| Accesso senza login | Solo consultazione del catalogo | Nessuna chat AI |

La regola condivisa per Azure OpenAI è definita in `.claude/skills/_shared/azure-openai.md`.

## KPI
Il progetto **non** implementa un sistema di KPI propri (nessun calcolo o dashboard di indicatori nell'applicazione). Le skill analizzano modelli Power BI di terzi e, quando serve, riconoscono le **misure di tipo KPI** presenti nel modello (ad esempio nella skill `analyze` per capire il dominio funzionale). Gli unici indicatori operativi prodotti sono metriche tecniche, come durata e tempo CPU delle query DAX (skill di performance).

## Formati e strumenti Power BI
- **PBIP / TMDL**: progetto Power BI in formato testo (`PBIP/`); gli snapshot TMDL sono usati da `compare-model-snapshot`.
- **DAX**: linguaggio delle query di verifica (integrità dati, estrazione tabelle, misure).
- **Trace Analysis Services**: usata da `check-performance` per catturare le query DAX.
- **Custom visual**: widget in `PowerBI Custom Widget/` (Chart&Pie, ComboBarPieProject, Gantt I&N) con procedura in `Procedura per implementare un widget su PBI.docx`.

## Archivio GitHub
- Repository di destinazione: `PBI-Agent-Exports`, cartelle `Documentazione modello PBI`, `performance`, `reports`.
- Il collegamento si configura dal pulsante "Archivio GitHub" (token, repository `proprietario/repo`, branch, cartella).
- Il token richiede permessi di lettura/scrittura dei contenuti; per i repository privati serve un token con accesso al repo.
- Gli upload avvengono tramite API REST di GitHub.
