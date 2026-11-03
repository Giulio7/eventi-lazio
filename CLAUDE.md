# eventi-lazio

Rete di agenti che ogni settimana cerca eventi nel Lazio per famiglie con bambini 0-5 anni
e produce un report schematico con un piano consigliato.

## Struttura
- `.claude/agents/` – agenti della rete:
  - `scout-roma` – eventi a Roma città
  - `scout-provincia-lazio` – eventi nel resto del Lazio
  - `scout-gite-natura` – luoghi per gite fuori porta / giornate in famiglia (piano B prioritario)
  - `verificatore` – fact-check di date, link, età
  - `sintetizzatore` – report finale con criteri basati su evidenze
- `.claude/skills/report-settimanale/` – orchestrazione (eseguire con `/report-settimanale`)
- `config/famiglia.md` – profilo famiglia (età, budget, raggio, vincoli)
- `reports/` – un report per settimana + `ULTIMO.md`

## Regole
- Lingua: italiano. Stile: schematico.
- Mai inventare eventi, date, prezzi o link; usare "n.d." se un dato manca.
- Se gli eventi confermati sono < 3, dare priorità a gite fuori porta e giornate in famiglia a Roma.
