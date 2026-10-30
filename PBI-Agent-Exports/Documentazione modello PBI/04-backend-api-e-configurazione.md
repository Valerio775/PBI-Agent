# Backend: API e configurazione

## Variabili d'ambiente (`.env`)

| Variabile | Default | Descrizione |
|---|---|---|
| `SKILLS_PROJECT_DIR` | cartella del progetto | Radice che contiene `.claude/skills` |
| `AZURE_OPENAI_ENDPOINT` | `https://Scriba.services.ai.azure.com/openai/v1` | Endpoint Azure OpenAI |
| `AZURE_OPENAI_DEPLOYMENT` | `gpt-5.4-mini` | Deployment |
| `AZURE_OPENAI_API_KEY` | vuoto | Chiave API |
| `OLLAMA_ENABLED` | `true` | Abilita l'accesso con Ollama |
| `POWERBI_MCP_NAME` | `powerbi-modeling-mcp` | Nome del server MCP |
| `POWERBI_MCP_COMMAND` / `POWERBI_MCP_ARGS` | vuoto / `--start` | Comando del server MCP |
| `REQUIRE_POWERBI_MCP` | `false` | Rende obbligatorio il server MCP |
| `MAX_TOOL_STEPS` | `25` | Massimo cicli di tool calling |
| `MAX_TOOL_RESULT_CHARS` | `30000` | Limite del risultato di un tool |
| `MAX_EXTRACT_TOOL_RESULT_CHARS` | `500000` | Limite per le estrazioni dati |
| `ANALYZE_TIMEOUT_SECONDS` | `120` | Timeout analisi |
| `CHAT_TIMEOUT_SECONDS` | `180` | Timeout chat |
| `CHAT_COMPLETION_TIMEOUT_SECONDS` | `75` | Timeout singola completion |
| `PBI_AGENT_DATA_DIR` | `mbi-agent-webapp/data` | Cartella dati |
| `PBI_AGENT_DB_PATH` | `data/pbi_agent.sqlite3` | File SQLite |
| `PORT` | `8000` | Porta (container) |

Non committare mai il file `.env` né i token.

## Endpoint principali

| Gruppo | Endpoint |
|---|---|
| Pagina e catalogo | `GET /`, `GET /skills` |
| Stato | `GET /mcp-status`, `GET /powerbi-status`, `GET /analyze-status` |
| Autenticazione | `POST /auth/login`, `POST /auth/local-login`, `POST /auth/ollama-login`, `POST /auth/logout`, `GET /auth/options` |
| Modelli e quota | `GET /ollama-models`, `GET/POST /session/model`, `GET /session/quota` |
| Chat | `POST /chat`, `GET /chat-progress/{request_id}`, `GET /chat-history` |
| Analyze description | `POST /analyze-description/table-options`, `.../table-description`, `.../table-description/cancel` |
| Performance | `POST /performance-trace/start`, `/stop`, `/archive`; `POST /measure-performance/catalog`, `/run` |
| Archivio GitHub | `GET /github/archive/status`, `POST /github/archive/config`, `POST /github/archive/upload` |

## Dati persistiti (SQLite)
- `auth_sessions`: sessioni di login (provider, endpoint, configurazione archivio GitHub).
- `chat_messages`: cronologia delle richieste, raggruppata per modello Power BI nel pannello "Cronologia".

## Sicurezza
- I token (Copilot, Azure, GitHub) vengono passati a runtime e non sono scritti nel codice.
- Le sessioni usano identificativi casuali (`secrets`).
- In produzione la webapp è protetta da **oauth2-proxy** (`oauth2-proxy/`, `helm/templates/configmap-oauth2.yaml`).
- Il container gira con utente non privilegiato (`appuser`, uid 10001).
- Ollama invia le richieste solo al servizio locale, senza fallback ad Azure.
- Esistono configurazioni di analisi di sicurezza: `dependency_check_suppressions.xml`, `license_finder_decisions.yml`, `sonar-project.properties`.
