# GMExtractions — Software di Estrazione Attività

Applicazione Windows per estrarre attività commerciali (bar, ristoranti, alberghi,
negozi, ecc.) da comuni italiani, con esportazione in Excel e CSV, schede separate
per ogni comune e raggruppamento per via.

**Versione:** 1.0.0
**Autore:** Massimo Sassano
**Anno:** 2026

---

## 1. Requisiti

- Windows 10 o superiore (64-bit)
- Connessione Internet
- Account gratuito **Geoapify** (per la API Key)

---

## 2. Come ottenere la API Key GRATUITA

1. Vai su **https://www.geoapify.com/**
2. Clicca in alto a destra su **"Sign up"** (Registrati)
3. Inserisci **email** e **password** (nessuna carta di credito richiesta)
4. Conferma l'email tramite il link che ricevi
5. Accedi al tuo account
6. Vai su **https://myprojects.geoapify.com/**
7. Clicca **"Create new project"** → dai un nome (es. `GMExtractions`)
8. Nella pagina del progetto, sezione **"API Keys"**, trovi la tua chiave
   (esempio: `97a65d1c319647ea808c60e7b94cf336`)
9. **Copia** la chiave

**Piano gratuito:** 3.000 richieste al giorno, rinnovate ogni giorno alle 00:00 UTC.

---

## 3. Dove inserire la API Key

1. Apri `GMExtractions.exe`
2. Menu in alto → **Strumenti → Impostazioni**
3. Nel campo **"API Key:"** incolla la chiave copiata
4. Clicca **OK**

La chiave viene salvata in `config.ini` nella cartella dell'eseguibile.
NON condividerla con nessuno.

Per cambiarla: rifai la procedura e incolla la nuova chiave.

---

## 4. Interfaccia — Come si usa

L'interfaccia è divisa in **due pannelli**:

### 🔹 Pannello SINISTRO — Selezione

**Comuni** (in alto)
**Categorie** (in basso)

Entrambi funzionano **allo stesso modo**:

1. Nel campo di ricerca, digiti le prime lettere (es. `Poli` o `Rist`)
2. Appare un menu a tendina con i suggerimenti
3. Clicchi sul suggerimento → appare nella lista **"Selezionati"**
4. Ripeti per aggiungere altri comuni/categorie
5. Per togliere una voce: selezionala e clicca **"Rimuovi"**

**Pulsanti disponibili:**
- **`+ Aggiungi ai selezionati`** → aggiunge al campo di lavoro
- **`Rimuovi ... selezionato`** → toglie dalla lista
- **`+ Aggiungi nuovo comune alla lista`** → aggiunge un nuovo comune al file `comuni.txt` in modo **permanente**
- **`+ Aggiungi nuova categoria alla lista`** → aggiunge una nuova categoria al file `categorie.txt` in modo **permanente**

### 🔹 Pannello DESTRO — Risultati

- **AVVIA RICERCA** → avvia l'estrazione
- **Barra di avanzamento** → mostra il progresso
- **Schede (tab)** → **una scheda per ogni comune cercato**
- **Filtra per categoria** → menu a tendina che mostra solo le righe della categoria selezionata. Si popola automaticamente dopo ogni ricerca con le categorie trovate. Seleziona **"Mostra tutte"** per rimuovere il filtro.
- **Apri su Google Maps** → apre il browser con la posizione dell'attività selezionata. Funziona in 3 modi:
  - Clicca il pulsante verde **"Apri su Google Maps"**
  - **Doppio clic** sulla cella della colonna "Google Maps"
  - **Tasto destro** su una riga → **"Apri su Google Maps"** o **"Copia URL"**
- **Raggruppa per Via** → ordina i risultati per via + categoria + nome, con colori alternati
- **Vista Normale** → rimuove la colorazione e riattiva l'ordinamento cliccando sulle intestazioni
- **Esporta Excel / Esporta CSV** → salva i risultati

---

## 5. Flusso tipico d'uso

1. Cerca e aggiungi 3-4 comuni (es. Policoro, Scanzano Jonico, Nova Siri)
2. Cerca e aggiungi 5-6 categorie (es. Bar, Ristoranti, Pizzerie, Caffè)
3. Clicca **AVVIA RICERCA**
4. Attendi 30-60 secondi
5. Guarda le schede (una per comune) in alto
6. Usa il **filtro per categoria** per isolare i risultati di interesse
7. Clicca **Raggruppa per Via** per organizzare le visite
8. Usa **"Apri su Google Maps"** per visualizzare la posizione di un'attività
9. Clicca **Esporta Excel** per salvare

---

## 6. Interpretazione dei risultati

| Colonna | Cosa contiene |
|---------|--------------|
| Nome | Nome dell'attività |
| Categoria | Categoria cercata (es. Ristoranti) |
| Comune | Comune effettivo (dai dati Geoapify) |
| Indirizzo | Via + numero civico |
| **Via** | **Solo nome via/piazza (senza civico)** |
| CAP | Codice postale |
| Telefono | Numero di telefono (se disponibile) |
| Sito | Sito web (se disponibile) |
| Rating | Valutazione (spesso vuota, dipende dalla fonte) |
| Recensioni | Numero recensioni (spesso vuota) |
| Google Maps | URL cliccabile per aprire la posizione |

**Nota:** i campi Rating e Recensioni sono spesso vuoti perché Geoapify
non li fornisce. Se ti servono, considera Google Places API (a pagamento)
o l'estensione Chrome LeadGrab.

---

## 7. File di configurazione

Tutti i file sono nella **cartella dell'eseguibile**:

| File | Contenuto | Modificabile |
|------|-----------|--------------|
| `comuni.txt` | Lista comuni (uno per riga) | ✅ Sì (Notepad++ o dal software) |
| `categorie.txt` | Lista categorie (una per riga) | ✅ Sì (Notepad++ o dal software) |
| `config.ini` | API Key + selezioni salvate | ⚠️ Solo dal software |

Per aggiornare `comuni.txt` o `categorie.txt` con Notepad++: aggiungi/rimuovi righe, salva. Il software li ricarica al prossimo avvio.

---

## 8. Esportazione

### Esporta Excel (`.xls`)

- **Un foglio per ogni comune** (nome del foglio = nome comune)
- Intestazioni con sfondo blu e testo bianco in grassetto
- URL Google Maps **cliccabili**
- Riga crediti in fondo a ogni foglio
- **Compatibile** con Excel 2016, 2019, 365

### Esporta CSV (`.csv`)

- **UTF-8 con BOM** → Excel italiano lo apre correttamente
- Separatore `;` (standard italiano)
- Tutte le righe di tutti i comuni in un unico file
- Riga crediti in fondo

---

## 9. Limiti e considerazioni

- **Fonte dati:** Geoapify aggrega dati da OpenStreetMap e altre fonti aperte.
  La copertura in Italia è **buona ma non completa**: per alcune città potresti
  trovare 10-30 attività invece di 50-100.
- **Rating e Recensioni:** generalmente non disponibili con Geoapify.
- **Costi:** il piano gratuito di Geoapify offre 3.000 richieste/giorno.
  Ogni coppia (comune × categoria) consuma 2 richieste (geocodifica + places).
  Esempio: 5 comuni × 10 categorie = 100 richieste → puoi fare ~30 estrazioni/giorno.
- **Privacy:** le richieste vengono fatte direttamente al server Geoapify.
  Nessun dato viene inviato ad altri server.

---

## 10. Problemi comuni

| Problema | Soluzione |
|----------|-----------|
| "API Key mancante" | Vai in Strumenti → Impostazioni e incolla la chiave |
| "Nessun risultato" | Il comune potrebbe essere scritto in modo diverso. Prova con il nome esatto (es. "Policoro" non "Policoro MT") |
| "Categoria non mappata" | La categoria è nel file `categorie.txt` ma non è mappata nel codice. Aggiungi la mappatura in `categoriaToGeoapify()` |
| Molti risultati ma di altri comuni | Controlla che il filtro `place_id` sia attivo (non `circle`) |
| Excel non si apre | Prova con il CSV; oppure apri Excel → File → Apri → seleziona il `.xls` |
| Errori SSL | Assicurati che Windows sia aggiornato (richiede TLS 1.2+) |
| `comuni.txt` non trovato | Copia il file nella cartella dell'eseguibile (dove c'è `GMExtractions.exe`) |

---

## 11. Crediti

- **Software:** GMExtractions v1.0.0
- **Framework:** Qt 6.x (Open Source, LGPL)
- **IDE:** Visual Studio 2026 + Qt VS Tools
- **API:** [Geoapify](https://www.geoapify.com/)
- **Dati:** © OpenStreetMap contributors (ODbL)

---

**GMExtractions v1.0.0**
© 2026 **Massimo Sassano** — Tutti i diritti riservati.

Sviluppato in C++ con Qt 6.x su Visual Studio 2026.

Licenza del software: uso personale.
I dati sono forniti "as is" senza garanzie sulla completezza.
