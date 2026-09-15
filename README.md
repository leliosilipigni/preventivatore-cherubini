# Configuratore Cherubini — Ellesse Rappresentanze

Preventivazione rapida Cherubini con distinzione automatica dei canali **EXPRESS** e **SPA**.

## Come funziona

1. **Selezioni il cliente** (ricerca per nome o codice) → il sistema sceglie **da solo** il listino corretto e applica lo sconto pattuito.
2. **Cerchi gli articoli** nel listino attivo (codice o descrizione) e li aggiungi con la quantità.
3. **Stampi / salvi in PDF** il preventivo con logo Cherubini, totali listino → sconto → netto → IVA.

## Archivio preventivi

Il secondo tab conserva tutti i preventivi fatti:

- **Salvataggio automatico** a ogni stampa, oppure manuale con "Salva in archivio"
- **Numero progressivo per anno** (es. `2026-001`), mai riusato anche dopo un'eliminazione
- Ogni scheda mostra cliente, canale, sconto, data, numero articoli, pezzi, netto e totale
- Azioni: **Apri e modifica** · **Ristampa** · **Duplica** (per creare una variante) · **Elimina**
- **Ricerca** per cliente, numero o codice articolo
- **Statistiche**: preventivi totali, totale netto, totale IVA inclusa, quanti nell'anno corrente
- **Esporta / Importa backup** in JSON

⚠️ L'archivio è salvato in `localStorage`, quindi **vive sul dispositivo e sul browser** che usi: non è sincronizzato tra telefono e PC. Usa **Esporta backup** per conservarlo, e **Importa backup** per riportarlo su un altro dispositivo.

### Dati salvati per ogni preventivo

`id, num, anno, data, cliente {cod, nome, stato, sconto}, listino, righe[], note, validita, pagamento, tl, tn, iva, tot`

## Canali e listini

| Canale cliente | Listino usato | Articoli |
|---|---|---|
| **EX** (Express) | Listino EXPRESS | 338 |
| **SPA** | Listino GENERALE | 1.440 |

I prezzi dei due canali **non sono uguali**: il canale EXPRESS ha prezzi più alti del generale.
Sul prezzo di listino si applica lo **sconto cliente** (43%–61% secondo il cliente).

## Fonte prezzi

Listino Cherubini in vigore dal **01/06/2026** (moduli di preventivazione ufficiali Cherubini 06.2026):

- **+3%** listino motori e accessori
- **+6%** listino manovra manuale

Consegna **franco destino** per ordini a partire da **€ 3.500**.
IVA 22%.

## Dati

| File | Contenuto |
|---|---|
| `data/dati.js` | Clienti (51 Cherubini + 37 CH-Mimetal), listino EXPRESS, listino GENERALE |
| `assets/logo_2.png` | Logo Cherubini |

## Aggiornare i listini

```bash
# 1. sostituire i moduli .xls in /data/cache/documents/
python3 /data/scripts/estrai_dati_cherubini.py    # -> JSON
python3 /data/scripts/build_dati_cherubini.py     # -> data/dati.js
```

---

Configuratore gestito da **Hermes** · Ellesse Rappresentanze · Lelio Silipigni
