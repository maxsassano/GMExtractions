# GMExtractions — Software di Estrazione Attività

Applicazione Windows per estrarre attività commerciali (bar, ristoranti, alberghi, ecc.)
da comuni italiani, con esportazione in Excel e CSV, raggruppamento per via.

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

## 3. Dove inserire la API Key nel software

1. Apri `GMExtractions.exe`
2. Menu in alto → **Strumenti → Impostazioni**
3. Nel campo **"API Key:"** incolla la chiave copiata
4. Clicca **OK**

La chiave viene salvata in `config.ini` nella cartella dell'eseguibile.
NON condividerla con nessuno.

Per cambiarla: rifai la procedura e incolla la nuova chiave.

---

## 4. Come usare il software

### 4.1 Aggiungere comuni
1. Nel pannello sinistro, campo **"Digita per cercare un comune"**
2. Scrivi le prime lettere (es. `Poli`)
3. Appare un menu a tendina con i comuni che iniziano con quelle lettere
4. Clicca sul comune → viene aggiunto a **"Comuni selezionati"**

I comuni vengono caricati da `comuni.txt` (8.126 comuni italiani).
Per rimuoverne uno: selezionalo e clicca **"Rimuovi comune selezionato"**.

### 4.2 Selezionare categorie
Nel pannello **"Categorie"**, spunta le caselle delle categorie che ti interessano
(es. Bar, Ristoranti, Pizzerie, Caffè).

Le categorie sono 40+ e includono: ristorazione, alloggi, negozi, servizi,
luoghi di interesse.

### 4.3 Avviare la ricerca
1. Clicca **AVVIA RICERCA**
2. Attendi (la barra di avanzamento mostra il progresso)
3. I risultati appaiono nella tabella a destra

### 4.4 Raggruppare per via
- Clicca **"Raggruppa per Via"** → ordina i risultati per via + categoria + nome
- I gruppi sono colorati alternativamente (azzurro / bianco)
- Utile per organizzare visite commerciali
- Clicca **"Vista Normale"** per rimuovere la colorazione

### 4.5 Esportare
- **"Esporta Excel"** → file `.xls` con filtri automatici e URL cliccabili
- **"Esporta CSV"** → file `.csv` compatibile con Excel italiano (separatore `;`)

---

## 5. Interpretazione dei risultati

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
| Google Maps | URL cliccabile per aprire la posizione su Google Maps |

**Nota:** i campi Rating e Recensioni sono spesso vuoti perché Geoapify
non li fornisce. Se ti servono, considera Google Places API (a pagamento)
o l'estensione Chrome LeadGrab.

---

## 6. File di configurazione

| File | Contenuto | Posizione |
|------|-----------|-----------|
| `comuni.txt` | Lista comuni (uno per riga) | Cartella dell'eseguibile |
| `config.ini` | API Key, comuni selezionati, spunte categorie | Cartella dell'eseguibile |

Per aggiornare `comuni.txt`: apri con Notepad++, aggiungi/rimuovi righe, salva.
Il software lo ricarica al prossimo avvio.

---

## 7. Limiti e considerazioni

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

## 8. Problemi comuni

| Problema | Soluzione |
|----------|-----------|
| "API Key mancante" | Vai in Strumenti → Impostazioni e incolla la chiave |
| "Nessun risultato" | Il comune potrebbe essere scritto in modo diverso. Prova con il nome esatto (es. "Policoro" non "Policoro MT") |
| Molti risultati ma di altri comuni | Controlla che il filtro `place_id` sia attivo (non `circle`) |
| Excel non si apre | Prova con il CSV; oppure apri Excel → File → Apri → seleziona il `.xls` |
| Errori SSL | Assicurati che Windows sia aggiornato (richiede TLS 1.2+) |

---

## 9. Contatti e crediti

- **Software:** GMExtractions
- **Framework:** Qt 6.x (Open Source, LGPL)
- **IDE:** Visual Studio 2026 + Qt VS Tools
- **API:** Geoapify (https://www.geoapify.com/)
- **Dati:** OpenStreetMap contributors (ODbL)
---

**GMExtractions v1.0**  
© 2026 **Massimo Sassano** — Tutti i diritti riservati.

Sviluppato in C++ con Qt 6.x su Visual Studio 2026.

Licenza del software: uso personale.
I dati sono forniti "as is" senza garanzie sulla completezza.
