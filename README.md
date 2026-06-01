# 🏔️ Workout Tracker — Preparazione Monte Toubkal

**Versione:** 1.0  
**Link app:** https://t-ivan2.github.io/Workout-Toubkal/  
**Obiettivo:** Tracciare la preparazione atletica per l'ascensione al Monte Toubkal (4.167 m, Marocco) — 6 settembre 2026

---

## Indice

1. [Cos'è questa app](#1-cosè-questa-app)
2. [Come funziona tecnicamente](#2-come-funziona-tecnicamente)
3. [Navigazione](#3-navigazione)
4. [HOME](#4-home)
5. [PIANO — Calendario](#5-piano--calendario)
6. [REGISTRA — Nuovo allenamento](#6-registra--nuovo-allenamento)
7. [SCHEDE](#7-schede)
8. [STORICO](#8-storico)
9. [PROGRESSI](#9-progressi)
10. [DATI — Impostazioni](#10-dati--impostazioni)
11. [Backup automatico domenicale](#11-backup-automatico-domenicale)
12. [Sicurezza dei dati](#12-sicurezza-dei-dati)
13. [Installazione sul telefono](#13-installazione-sul-telefono)
14. [Catalogo esercizi predefiniti](#14-catalogo-esercizi-predefiniti)
15. [Aggiornare l'app](#15-aggiornare-lapp)

---

## 1. Cos'è questa app

Workout Tracker è un'applicazione web progressiva (PWA) pensata specificamente per tracciare tre tipi di attività fisica durante la preparazione al Toubkal:

- **Palestra** — sessioni con pesi, serie e ripetizioni per esercizio
- **Cardio** — corsa, ciclismo, nuoto, camminata veloce
- **Escursione / Trekking** — uscite in montagna con dislivello, distanza e peso zaino

L'app è progettata per il telefono: interfaccia scura, touch-friendly, senza pubblicità, senza account, senza abbonamenti. Tutto è gratuito e tutto rimane sul tuo dispositivo.

---

## 2. Come funziona tecnicamente

L'app è un singolo file HTML che gira nel browser del telefono. Non ha un server, non ha un database remoto, non invia dati a nessuno.

**Tecnologie usate:**
- HTML/CSS/JavaScript puro — nessun framework
- `localStorage` del browser per salvare i dati
- Service Worker per il funzionamento offline
- Web App Manifest per l'installazione come PWA
- Chart.js per i grafici

**Struttura dati salvata:**
```
{
  exercises: [...],   // catalogo esercizi
  workouts:  [...],   // allenamenti registrati
  templates: [...],   // schede pre-impostate
  plans:     [...]    // sessioni pianificate nel calendario
}
```

Tutto viene serializzato in JSON e salvato in `localStorage` con la chiave `wt2_data`. Il salvataggio avviene automaticamente ad ogni modifica.

---

## 3. Navigazione

In fondo allo schermo è sempre visibile una barra di navigazione fissa con **7 tab**:

| Tab | Icona | Funzione |
|-----|-------|----------|
| **Home** | 🏠 Casa | Dashboard riassuntiva con statistiche e prossimi allenamenti |
| **Piano** | 📅 Calendario | Pianificazione settimanale/mensile degli allenamenti |
| **Registra** | ➕ Cerchio | Inserire un nuovo allenamento completato |
| **Schede** | ⊞ Griglia | Creare e avviare schede pre-impostate |
| **Storico** | 📈 Grafico a impulsi | Lista di tutti gli allenamenti registrati |
| **Progressi** | 📊 Barre | Grafici di analisi e progressione |
| **Dati** | ⚙️ Ingranaggio | Esercizi, export, import, impostazioni |

Toccare una tab porta immediatamente alla schermata corrispondente senza perdere dati in corso di inserimento.

---

## 4. HOME

La schermata principale. Si aggiorna automaticamente ogni volta che la si apre.

### Intestazione
- **Saluto dinamico** — "Buongiorno" (fino alle 12:00), "Buon pomeriggio" (12–18), "Buonasera" (dopo le 18)
- **Conto alla rovescia** — giorni mancanti al Toubkal (6 settembre 2026), in blu in alto a destra. Quando il giorno arriva mostra "—"

### 4 metriche rapide
| Metrica | Calcolo |
|---------|---------|
| **Questo mese** | Allenamenti dal 1° del mese corrente ad oggi |
| **Questa settimana** | Sessioni da domenica della settimana corrente |
| **Uscite outdoor** | Totale storico di tutti gli allenamenti di tipo Escursione |
| **Striscia** | Settimane consecutive con almeno un allenamento registrato, contate a ritroso da oggi |

### Barra progresso Toubkal
Mostra il numero di uscite outdoor rispetto all'obiettivo di **13 uscite** (una a settimana fino a settembre). La barra verde si riempie proporzionalmente. Formato: "X / 13".

### Prossimi allenamenti
Lista delle sessioni pianificate nel calendario nei prossimi **7 giorni**, al massimo 4. Per ciascuna mostra: data, ora (se impostata), nome e tipo. Toccare una card apre il dettaglio della pianificazione. Se non ci sono sessioni pianificate, un link diretto al calendario invita a pianificare.

### Ultimo allenamento
Card dell'allenamento più recente registrato in assoluto. Mostra nome, tipo, data e un riepilogo rapido (esercizi per la palestra, durata/km per cardio, ore/dislivello per escursioni). Toccare la card apre il dettaglio completo.

### Pulsante "Registra allenamento"
Scorciatoia diretta alla tab Registra.

---

## 5. PIANO — Calendario

Calendario mensile per pianificare le sessioni future. Accessibile dalla tab **Piano**.

### Griglia mensile
- 7 colonne (Lun–Dom), una riga per settimana
- Naviga tra i mesi con i pulsanti **‹** e **›** in alto
- Il mese e l'anno corrente sono mostrati al centro
- **Oggi** è evidenziato con un cerchio blu pieno con il numero in bianco
- I giorni con **sessioni pianificate** mostrano un pallino blu sotto al numero
- I giorni con **allenamenti registrati** mostrano un pallino verde
- Il giorno **selezionato** ha un bordo blu evidenziato

### Selezionare un giorno
Tocca qualsiasi giorno. Sotto la griglia appare una barra con la data scritta in chiaro (es. "Martedì 10 giugno") e il pulsante blu **Pianifica** a destra. Questa barra è sempre visibile non appena si seleziona un giorno.

### Sessioni del giorno selezionato
Sotto la barra appaiono due sezioni:

**Pianificato** — le sessioni programmate per quel giorno. Per ciascuna:
- Pallino colorato (blu = palestra, verde = cardio, arancione = escursione)
- Nome della sessione
- Badge "↻ sett." se è ricorrente settimanale, "↻ 2sett." o "↻ mens." per le altre ricorrenze
- Orario (se impostato) o "Orario non impostato"
- Toccare la card apre il dettaglio

**Registrato** — gli allenamenti effettivamente salvati in quel giorno. Toccare apre il dettaglio dell'allenamento nello storico.

Se il giorno è vuoto appare un'icona con il testo "Nessun evento — Tocca Pianifica per aggiungere".

### Pianificare una sessione
Tocca il pulsante **Pianifica** nella barra del giorno selezionato. Si apre uno sheet con:

| Campo | Descrizione |
|-------|-------------|
| **Tipo** | Palestra, Cardio o Escursione/Trekking |
| **Nome** | Nome libero della sessione (default: "Allenamento") |
| **Data** | Precompilata con il giorno selezionato, modificabile |
| **Orario** | Facoltativo — es. "07:30" |
| **Note** | Obiettivo, luogo, attrezzatura da portare ecc. |
| **Ricorrenza** | Nessuna / Settimanale / Ogni 2 settimane / Mensile |
| **Ripeti fino al** | Appare solo se si sceglie una ricorrenza. Default: giorno prima del Toubkal |

Toccare **Salva** aggiunge l'evento. Se è ricorrente, appare in tutti i giorni corrispondenti fino alla data di fine. Il calendario si sposta automaticamente al mese del giorno salvato.

### Dettaglio sessione pianificata
Toccare una sessione nella lista apre uno sheet con tutti i dettagli e tre pulsanti:
- **Elimina** (rosso) — richiede conferma prima di eliminare
- **Registra** (ambra) — apre direttamente la tab Registra con tipo, nome e data della sessione precompilati
- **Chiudi**

### Legenda
In fondo al calendario:
- 🔵 Pallino blu = sessione pianificata
- 🟢 Pallino verde = allenamento registrato
- Cerchio blu pieno = oggi

---

## 6. REGISTRA — Nuovo allenamento

La schermata per inserire una sessione appena completata. Accessibile dalla tab **Registra** o dal pulsante in Home.

### Campi comuni a tutti i tipi
| Campo | Note |
|-------|------|
| **Tipo di sessione** | Palestra / Cardio / Escursione — cambia i campi sottostanti |
| **Nome sessione** | Testo libero. Se lasciato vuoto usa il nome del tipo |
| **Data** | Precompilata con oggi. Permette di inserire sessioni di giorni precedenti o futuri |

---

### Tipo Palestra 🏋

Dopo aver selezionato Palestra appare la sezione **Esercizi**.

#### Aggiungere un esercizio
Tocca **+ Aggiungi** in alto a destra. Si apre uno sheet con:

- **Esercizio** — menu con tutti gli esercizi del catalogo (predefiniti + personalizzati). Selezionandone uno il sistema recupera automaticamente l'ultima sessione in cui è stato eseguito e precompila peso e reps della prima serie come suggerimento
- **Numero di serie** — da 1 a 5 (default: 3)
- **Tabella serie** — per ogni serie: campo Peso (kg) e Ripetizioni
- **Pulsante freccia ↓** — copia il peso e le reps di quella riga in tutte le serie successive

Confermare con **Aggiungi**.

#### Modificare un esercizio già aggiunto
Ogni esercizio nella lista mostra due pulsanti affianco al nome:

- **Modifica** (grigio, con icona matita) — riapre lo sheet precompilato con tutti i dati esistenti: esercizio selezionato, numero di serie, ogni peso e ogni ripetizione. Il titolo dello sheet diventa "Modifica esercizio" e il tasto di conferma "Salva modifiche". Puoi cambiare qualsiasi campo prima di confermare.
- **Elimina** (rosso, icona cestino) — chiede conferma prima di rimuovere l'esercizio dalla sessione in corso

#### Visualizzazione esercizi
Ogni esercizio salvato mostra il nome in grassetto e, sotto, tutte le serie con il formato: `Serie 1: 80 kg × 8`

#### Salvataggio
Il pulsante **Salva allenamento** in fondo alla pagina salva la sessione. Richiede almeno un esercizio per la palestra. Dopo il salvataggio tutti i campi vengono azzerati e si torna alla Home con un toast "Allenamento salvato!".

---

### Tipo Cardio 🚴

Tutti i campi sono facoltativi:

| Campo | Unità | Esempio |
|-------|-------|---------|
| Durata | minuti | 45 |
| Distanza | km | 8.5 |
| Dislivello | metri | 200 |
| FC media | bpm | 145 |
| Zaino | kg | 5 |
| Note | testo libero | "Percorso collinare, buone gambe" |

---

### Tipo Escursione / Trekking 🥾

| Campo | Unità | Esempio |
|-------|-------|---------|
| Durata | ore (decimali) | 4.5 |
| Distanza | km | 14 |
| Dislivello + | metri | 900 |
| Quota max | metri slm | 2100 |
| Peso zaino | kg | 10 |
| Sensazione | 1–5 stelle | ⭐⭐⭐⭐ Buona |
| Note | testo libero | "Neve da 1800m, terreno scivoloso" |

La **sensazione** ha 5 livelli: Molto dura / Faticosa / Nella media / Buona / Ottima.

---

## 7. SCHEDE

Le schede sono template pre-impostati. Preparale in anticipo e avviale con un tocco senza dover riselezionare ogni volta tutti gli esercizi. Accessibile dalla tab **Schede**.

### Visualizzazione
Ogni scheda appare come una card con:
- Nome e numero di esercizi (per palestra) o tipo
- Etichetta colorata del tipo
- Chip con il nome di ogni esercizio e il numero di serie previste
- Tre pulsanti: **Modifica**, **Elimina** (con conferma), **Inizia**

Se non ci sono schede appare un messaggio vuoto con invito a crearne una.

### Creare una nuova scheda
Tocca **+ Nuova** in alto a destra. Campi:

| Campo | Descrizione |
|-------|-------------|
| **Nome scheda** | es. "Gambe pesante", "Scheda A", "Uscita domenicale" |
| **Tipo** | Palestra / Cardio / Escursione |
| **Esercizi** | Solo per Palestra: aggiungi esercizi uno alla volta con il numero di serie previste (1–5) |

Per aggiungere un esercizio alla scheda tocca **+ Aggiungi** nella sezione esercizi. Scegli l'esercizio dal catalogo e il numero di serie. Ogni esercizio aggiunto appare come riga con nome, serie e pulsante ✕ per rimuoverlo (con conferma).

Conferma con **Salva scheda**.

### Modificare una scheda
Tocca **Modifica**: si riapre il pannello con tutti i dati precompilati. Puoi cambiare nome, tipo, aggiungere o rimuovere esercizi.

### Avviare una scheda
Tocca **Inizia**. Si apre un pannello di anteprima con l'elenco degli esercizi e le serie previste. Tocca **Inizia allenamento**:

- Vai automaticamente alla tab Registra
- Nome della scheda precompilato come nome sessione
- Data impostata su oggi
- Tutti gli esercizi della scheda già caricati
- Pesi e reps precompilati dall'ultima sessione in cui hai eseguito quegli esercizi (se disponibili)
- Puoi aggiungere altri esercizi, modificare serie, pesi e reps, e salvare normalmente

---

## 8. STORICO

Lista completa di tutti gli allenamenti registrati in ordine cronologico inverso (il più recente in cima). Accessibile dalla tab **Storico**.

### Filtri
Quattro pill in cima filtrano per tipo:
- **Tutti** — mostra tutto
- **Palestra** — solo sessioni in palestra
- **Cardio** — solo cardio
- **Escursioni** — solo escursioni/trekking

### Lista allenamenti
Ogni voce mostra:
- Data (giorno della settimana, giorno, mese, anno)
- Nome sessione
- Riepilogo: esercizi per la palestra; durata/km/dislivello per cardio e trekking
- Etichetta colorata del tipo

### Dettaglio allenamento
Toccare una voce apre il dettaglio completo:

**Palestra** — tutti gli esercizi con ogni serie, peso × ripetizioni. Formato: `S1  80 kg × 8`

**Cardio / Escursione** — griglia di card con tutte le metriche inserite (durata, distanza, dislivello ecc.). Per le escursioni mostra anche la sensazione. Se ci sono note, sono mostrate in un box grigio.

In fondo allo sheet:
- **Elimina** (rosso) — richiede conferma prima di eliminare definitivamente l'allenamento
- **Chiudi**

---

## 9. PROGRESSI

Tre grafici di analisi. Accessibile dalla tab **Progressi**.

### 1. Analisi esercizio — grafico a linea
Menu a tendina con tutti gli esercizi per cui hai registrato almeno una sessione con pesi.

Selezionandone uno appare:
- **Badge PR** — peso massimo mai sollevato in quell'esercizio
- **Badge Ultima** — peso massimo nell'ultima sessione
- **Badge sessioni** — quante volte totali hai eseguito quell'esercizio
- **Grafico a linea** — andamento del carico massimo per sessione nel tempo (X = data, Y = kg)

Il grafico è interattivo: tocca un punto per vedere il valore esatto.

### 2. Volume settimanale — grafico a barre impilate
Istogramma delle ultime **8 settimane**. Ogni barra mostra il numero totale di sessioni suddivise per tipo:
- 🔵 Blu = sessioni palestra
- 🟢 Verde = sessioni cardio
- 🟠 Arancione = escursioni

Appare solo se hai almeno un allenamento registrato.

### 3. Dislivello escursioni — grafico a barre
Le ultime **12 uscite** (escursioni o cardio) per cui è stato inserito un valore di dislivello. Ogni barra = metri di dislivello positivo di quella uscita. Le uscite senza dislivello inserito non appaiono. Utile per vedere la progressione del carico outdoor.

Appare solo se hai almeno un'uscita con dislivello inserito.

---

## 10. DATI — Impostazioni

Gestione completa dei dati dell'app. Accessibile dalla tab **Dati** (icona ingranaggio).

### Gestione esercizi
Lista di tutti gli esercizi del catalogo raggruppati per categoria. Per ogni esercizio mostra nome e unità (kg / corpo libero).

- **Pulsante cestino** — elimina l'esercizio dal catalogo (con conferma). Gli esercizi eliminati non appaiono più nei menu di selezione ma rimangono nei dati degli allenamenti già salvati
- **+ Aggiungi esercizio** — apre lo sheet per creare un nuovo esercizio con nome, categoria e unità

### Esporta dati
Scarica i dati in due formati.

**Filtri disponibili:**

*Tipo di dati:*
- Tutti gli allenamenti
- Solo palestra
- Solo cardio
- Solo escursioni
- Lista esercizi

*Periodo:*
- Tutto
- Ultimo mese
- Ultimi 3 mesi
- Ultimo anno

**Formati:**

**JSON** — formato completo, strutturato, ideale per backup e reimportazione nell'app. Contiene tutti i dati esattamente come sono salvati.

**CSV** — formato tabellare apribile con Excel o Fogli Google:
- Per la palestra: una riga per ogni serie di ogni esercizio (colonne: data, sessione, esercizio, serie, peso_kg, ripetizioni)
- Per cardio/escursioni: una riga per sessione con tutte le metriche
- Per gli esercizi: id, nome, categoria, unità

Il file si scarica nella cartella Download con nome automatico tipo `workout_allenamenti_2026-06-01.json`.

### Importa dati
Carica un file JSON precedentemente esportato. Il sistema importa solo gli allenamenti non già presenti (controlla l'ID), quindi non crea duplicati. I dati esistenti vengono mantenuti.

### Dati app
Mostra il numero totale di sessioni registrate. Il pulsante **Cancella tutto** elimina definitivamente tutti gli allenamenti dopo conferma. Gli esercizi e le schede non vengono cancellati.

### Come installare l'app
Istruzioni rapide per iPhone (Safari) e Android (Chrome).

### Versione
In fondo alla schermata: **Versione 1.0 · Preparazione Monte Toubkal**.

---

## 11. Backup automatico domenicale

Ogni **domenica sera alle 23:00**, se l'app è aperta, appare automaticamente un banner arancione in fondo allo schermo.

Il banner mostra:
- Titolo "💾 Backup settimanale"
- Descrizione: "Sono le 23:00 di domenica — scarica una copia dei tuoi dati"
- Pulsante **Scarica backup JSON** — scarica immediatamente un file JSON completo con tutti i dati (allenamenti, esercizi, schede, piani). Nome file: `workout_backup_YYYY-MM-DD.json`
- Pulsante **Dopo** — chiude il banner; non riappare fino alla domenica successiva

Il controllo avviene al caricamento dell'app e ogni 30 minuti durante l'uso. Non appare se non ci sono allenamenti registrati.

**Come ripristinare da backup:** tab Dati → Importa dati → seleziona il file JSON salvato.

---

## 12. Sicurezza dei dati

### Come vengono salvati
Tutti i dati vivono nel `localStorage` del browser, una memoria permanente locale del dispositivo. Non esistono server, cloud, account o sincronizzazione automatica.

### Quando i dati sono al sicuro
| Azione | Effetto sui dati |
|--------|-----------------|
| Spegnere il telefono | ✅ Nessun effetto |
| Chiudere il browser | ✅ Nessun effetto |
| Riavviare il telefono | ✅ Nessun effetto |
| Aggiornare la pagina | ✅ Nessun effetto |

### Quando i dati possono andare persi
| Causa | Rischio |
|-------|---------|
| Svuotare la cache del browser (Safari/Chrome → Cancella dati di navigazione) | 🔴 Dati cancellati |
| Cancellare i dati del sito nelle impostazioni del browser | 🔴 Dati cancellati |
| Disinstallare il browser | 🔴 Dati cancellati |
| Reimpostare il telefono alle impostazioni di fabbrica | 🔴 Dati cancellati |
| Aprire l'app su un browser diverso (es. Chrome invece di Safari) | 🟡 I dati non sono visibili (sono nell'altro browser) |
| Cambiare telefono | 🟡 Dati non trasferiti automaticamente |

### Regola d'oro
Esporta il JSON dalla tab Dati ogni domenica sera (l'app te lo ricorda). Salva il file su **iCloud Drive** o **Google Drive**. Se cambi telefono o perdi i dati, importi il file JSON e recuperi tutto.

---

## 13. Installazione sul telefono

L'app è una PWA (Progressive Web App): può essere installata come un'app nativa senza passare dall'App Store o dal Play Store.

### iPhone — obbligatorio usare Safari
1. Apri **Safari** (non Chrome, non Firefox)
2. Vai su: `https://t-ivan2.github.io/Workout-Toubkal/`
3. Tocca l'icona **condividi** (il quadrato con la freccia verso l'alto, in fondo alla barra)
4. Scorri l'elenco e tocca **"Aggiungi a schermata Home"**
5. Modifica il nome se vuoi → tocca **Aggiungi**

L'app apparirà come icona sulla schermata Home. Si aprirà a schermo intero senza la barra di Safari.

> ⚠️ Su iPhone, Chrome e altri browser non supportano l'installazione PWA. Usa solo Safari.

### Android — usa Chrome
1. Apri **Chrome** e vai sul link dell'app
2. Tocca i **tre puntini ⋮** in alto a destra
3. Cerca la voce **"Installa app"** — se c'è, toccarla avvia l'installazione nativa (si apre senza barra browser)
4. Se non c'è "Installa app", tocca **"Aggiungi a schermata Home"** — funziona allo stesso modo ma potrebbe aprirsi nel browser

> ℹ️ Chrome mostra "Installa app" solo dopo alcune visite al sito. Se non compare subito, usa "Aggiungi a schermata Home" come alternativa.

### Una volta installata
- Appare con icona e nome "Workout" nella schermata Home
- Si apre a schermo intero come un'app nativa
- Funziona completamente offline dopo la prima apertura
- I dati rimangono anche dopo aggiornamenti dell'app

### Condividere l'app con altri
Basta inviare il link `https://t-ivan2.github.io/Workout-Toubkal/` — chiunque può aprirlo e installarlo. Ogni utente ha i propri dati separati e indipendenti.

---

## 14. Catalogo esercizi predefiniti

L'app include 17 esercizi predefiniti al primo avvio:

| Esercizio | Categoria | Unità |
|-----------|-----------|-------|
| Squat con bilanciere | Gambe | kg |
| Stacco da terra | Gambe | kg |
| Affondi bulgari | Gambe | kg |
| Step-up con manubri | Gambe | kg |
| Hip thrust | Gambe | kg |
| Leg press | Gambe | kg |
| Rematori bilanciere | Schiena | kg |
| Lat machine | Schiena | kg |
| Trazioni | Schiena | corpo libero |
| Arnold press | Spalle | kg |
| Face pull | Spalle | kg |
| Press panca | Petto | kg |
| Plank | Core | corpo libero |
| Dead bug | Core | corpo libero |
| Farmer carry | Core | kg |
| Kettlebell swing | Full body | kg |
| Turkish get-up | Full body | kg |

### Aggiungere un esercizio personalizzato
Dalla tab **Esercizi** (pulsante **+ Nuovo**) oppure dalla tab **Dati** (pulsante **+ Aggiungi esercizio**):

| Campo | Opzioni |
|-------|---------|
| Nome | Testo libero obbligatorio |
| Categoria | Gambe / Schiena / Petto / Spalle / Bicipiti / Tricipiti / Avambracci / Polpacci / Core / Full body |
| Unità | kg / Corpo libero |

L'esercizio diventa immediatamente disponibile nei menu di selezione durante la registrazione e nelle schede.

### Importare esercizi da file JSON
Dalla tab **Dati** → **Importa lista esercizi**: carica un file JSON con il formato raggruppato per categoria:

```json
{
  "gambe": [
    {"name": "Pistol squat", "unit": "bw"},
    {"name": "Leg extension", "unit": "kg"}
  ],
  "core": [
    {"name": "Dragon flag", "unit": "bw"}
  ]
}
```

Categorie valide: `gambe`, `schiena`, `petto`, `spalle`, `bicipiti`, `tricipiti`, `avambracci`, `polpacci`, `core`, `full`  
Unità: `kg` o `bw` (corpo libero)

Gli esercizi già presenti nel catalogo non vengono duplicati (controllo per nome, case-insensitive).

---

## 15. Aggiornare l'app

Poiché l'app è ospitata su GitHub Pages, gli aggiornamenti si pubblicano caricando un nuovo `index.html` nel repository.

### Per chi usa l'app (utente finale)
Non devi fare nulla. La prossima volta che apri l'app con connessione internet, il Service Worker scarica automaticamente la versione aggiornata in background. Al riavvio successivo dell'app trovi la versione nuova.

Se vuoi forzare l'aggiornamento: chiudi completamente il browser e riaprilo sul link dell'app.

### Per chi aggiorna il codice (sviluppatore)
1. Modifica `index.html` in locale
2. Carica il file aggiornato su GitHub nel repository `T-Ivan2/Workout-Toubkal`
3. GitHub Pages pubblica automaticamente in 1–2 minuti
4. Tutti gli utenti riceveranno l'aggiornamento alla prossima apertura con internet

**File del repository:**
```
Workout-Toubkal/
├── index.html              ← l'intera app
├── manifest.json           ← configurazione PWA (nome, icone, colori)
├── sw.js                   ← Service Worker per offline e cache
├── esercizi_template.json  ← template JSON per importare esercizi
├── icons/
│   ├── icon-192.png
│   ├── icon-512.png
│   └── apple-touch-icon.png
└── README.md               ← questo file
```

---

*Documentazione aggiornata al 2 giugno 2026 · Versione app 1.0*
