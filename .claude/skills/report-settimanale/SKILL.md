---
name: report-settimanale
description: Orchestra la rete di agenti che cerca eventi per famiglie e bambini 0-5 anni nel Lazio e produce il report settimanale in reports/. Usare quando si chiede il report settimanale degli eventi o "cosa facciamo questo weekend".
---

# Report settimanale eventi famiglie Lazio

## 1. Prepara
- Data odierna → finestra = **dal venerdì successivo alla domenica della settimana dopo** (≈10 giorni, copre due weekend).
- Leggi `config/famiglia.md` e l'ultimo report in `reports/` (per evitare ripetizioni).

## 2. Ricerca in parallelo (un solo messaggio, tre agenti)
Lancia contemporaneamente con lo strumento Agent, passando a ognuno la finestra di date e il profilo famiglia:
- `scout-roma`
- `scout-provincia-lazio`
- `scout-gite-natura`

## 3. Verifica
Unisci i tre output e passali a `verificatore`.

## 4. Sintesi
Passa l'output verificato + i luoghi di `scout-gite-natura` a `sintetizzatore`, che scrive `reports/AAAA-MM-GG.md`
(data = lunedì della settimana corrente) e aggiorna `reports/ULTIMO.md` con lo stesso contenuto.

## 5. Consegna
- `git add reports/ && git commit -m "Report settimanale <data>"` e `git push -u origin <branch corrente>` (retry con backoff 2s/4s/8s/16s solo su errori di rete).
- Nel messaggio finale riporta: la sezione "In breve", il "Piano consigliato" e il percorso del file.

## Regole generali
- Mai inventare eventi, date, prezzi o link.
- Se gli eventi ✅ sono meno di 3 → priorità a gite fuori porta / giornate in famiglia a Roma.
