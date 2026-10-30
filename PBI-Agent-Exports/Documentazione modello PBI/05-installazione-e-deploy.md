# Installazione e deploy

## Requisiti
- Python 3.10+
- Power BI Desktop con il modello aperto (per le skill che leggono il modello)
- Server MCP "Power BI Modeling MCP" (estensione VS Code o eseguibile)
- Un provider AI: token GitHub Copilot, chiave Azure OpenAI oppure Ollama locale

## Avvio locale

```powershell
cd mbi-agent-webapp
pip install -r requirements.txt
python main.py        # oppure start-app.bat
```

Apri http://localhost:8000 .

`requirements.txt`: `claude-agent-sdk`, `fastapi`, `uvicorn`, `openai`, `httpx`, `python-dotenv`, `openpyxl`, `azure-identity`.

## Ollama (modalità locale)
1. Installare Ollama per Windows.
2. `ollama pull qwen3:4b` (oppure `qwen3:8b`, selezionato di default se presente).
3. Con Ollama attivo sulla porta 11434, scegliere il modello dal menu "Modello Ollama" al login.

Vedi anche `mbi-agent-webapp/Guida locale Skill Studio con Ollama.docx`.

## Docker

```bash
docker build -t pbi-agent -f mbi-agent-webapp/Dockerfile .
docker run -p 8000:8000 pbi-agent
```

L'immagine copia `mbi-agent-webapp/` e `.claude/`, espone la porta 8000 e avvia `uvicorn main:app`.

Nota: in container il server MCP di Power BI Desktop non è raggiungibile (richiede Windows e Power BI Desktop locale); le funzioni di catalogo e chat restano disponibili.

## Cluster (OpenShift / Kubernetes)
- `helm/`: chart Helm (`Chart.yaml`, `values.yaml`, template per deployment, service, ingress, route, PVC, secret, configmap, oauth2-proxy).
- `mbi-agent-webapp/manifests/`: manifest OpenShift (BuildConfig, ImageStream, Deployment, Route, Secret, ConfigMap).
- `oauth2-proxy/Dockerfile`: immagine del proxy di autenticazione.
- Il volume persistente conserva il database SQLite in `data/`.
- Chiavi e token vanno forniti tramite `secret.yaml`/Secret del cluster, mai nei values in chiaro.

## Risoluzione dei problemi

| Sintomo | Causa probabile | Azione |
|---|---|---|
| Server MCP non trovato | Estensione/comando non rilevati | Installare "Power BI Modeling MCP" o impostare `POWERBI_MCP_COMMAND` |
| Nessuna istanza Power BI | Modello non aperto in Desktop | Aprire il `.pbix`/PBIP e riprovare |
| Errore 402/401 con Copilot | Crediti esauriti o token privo di *Copilot Requests* | Verificare su https://github.com/settings/copilot |
| Timeout su `analyze-description` | Modello troppo lento | Usare un modello più veloce o aumentare i timeout |
| Upload GitHub fallito | Token/branch/cartella errati | Controllare la configurazione in "Archivio GitHub" |
