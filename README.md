# 🏋 Workout Tracker — Preparazione Toubkal

**Link dell'app:** https://t-ivan2.github.io/Workout-Toubkal/

App PWA installabile su iPhone e Android. Funziona completamente offline.

---

## 📲 Come installare sul telefono

### iPhone — usa SAFARI (non Chrome)
1. Apri https://t-ivan2.github.io/Workout-Toubkal/ in **Safari**
2. Tocca l'icona **condividi** (quadrato con la freccia)
3. Tocca **"Aggiungi a schermata Home"**
4. Tocca **Aggiungi**

### Android — usa Chrome
1. Apri il link in **Chrome**
2. Apparirà un banner in basso → tocca **Installa**
3. Oppure: menu ⋮ → "Aggiungi a schermata Home"

---

## 💾 Backup automatico

Ogni **domenica alle 23:00** appare un banner arancione che ricorda di scaricare il backup JSON.
Salva il file su iCloud o Google Drive.

Per ripristinare: tab **Dati** → **Importa** → carica il JSON.

---

## ⚠️ Dati

I dati sono salvati localmente sul dispositivo. Non cancellare la cache del browser senza aver prima esportato i dati dalla tab Dati.
# 🏋 Workout Tracker — Preparazione Monte Toubkal

Documentazione completa dell'applicazione. Versione aggiornata al 31 maggio 2026.

**Link app:** https://t-ivan2.github.io/Workout-Toubkal/

---

## Indice

1. [Cos'è e come funziona](#cosè-e-come-funziona)
2. [Navigazione](#navigazione)
3. [Tab HOME](#tab-home)
4. [Tab REGISTRA](#tab-registra)
5. [Tab SCHEDE](#tab-schede)
6. [Tab STORICO](#tab-storico)
7. [Tab PROGRESSI](#tab-progressi)
8. [Tab ESERCIZI](#tab-esercizi)
9. [Tab DATI](#tab-dati)
10. [Backup automatico domenicale](#backup-automatico-domenicale)
11. [Come vengono salvati i dati](#come-vengono-salvati-i-dati)
12. [Installazione sul telefono](#installazione-sul-telefono)

---

## Cos'è e come funziona

Workout Tracker è un'app web progressiva (PWA) pensata per tracciare tre tipi di attività fisica nell'ambito della preparazione all'ascensione del Monte Toubkal (4.167 m, Marocco):

- **Palestra** — sessioni con pesi, serie e ripetizioni
- **Cardio** — corsa, ciclismo, camminata veloce
- **Escursione / Trekking** — uscite in montagna con dislivello, distanza e peso zaino

L'app funziona completamente **offline** una volta aperta la prima volta nel browser. Non richiede account, non invia dati a nessun server, non ha pubblicità. Tutto è salvato localmente sul tuo dispositivo.

---

## Navigazione

In fondo allo schermo è sempre visibile una barra di navigazione con 6 tab:

| Icona | Nome | Funzione |
|-------|------|----------|
| 🏠 | **Home** | Dashboard con statistiche e ultimo allenamento |
| ➕ | **Registra** | Inserire un nuovo allenamento |
| ⊞ | **Schede** | Gestire e avviare schede pre-impostate |
| 📅 | **Storico** | Lista di tutti gli allenamenti salvati |
| 📊 | **Progressi** | Grafici e analisi dei dati |
| ⚙️ | **Dati** | Gestione esercizi, export, import, backup |

La tab attiva è evidenziata in blu. Toccando una tab ci si sposta immediatamente, senza perdere dati in corso di inserimento.

---

## Tab HOME

La schermata principale mostra una panoramica immediata della tua preparazione.

### Intestazione
- **Saluto dinamico** — cambia automaticamente in base all'ora: "Buongiorno" (fino alle 12), "Buon pomeriggio" (12–18), "Buonasera" (dopo le 18)
- **Conto alla rovescia** — numero di giorni mancanti al Monte Toubkal (data fissata: 6 settembre 2026), mostrato in blu in alto a destra

### 4 metriche rapide
- **Questo mese** — numero di allenamenti registrati nel mese di calendario corrente (dal 1° del mese a oggi)
- **Questa settimana** — sessioni registrate dall'inizio della settimana corrente (da domenica)
- **Uscite outdoor** — totale storico di tutte le sessioni di tipo Escursione registrate
- **Striscia** — numero di settimane consecutive in cui hai registrato almeno un allenamento (calcolato a ritroso da oggi)

### Barra progresso Toubkal
Mostra visivamente quante uscite outdoor hai fatto rispetto all'obiettivo di **13 uscite** (una a settimana fino a settembre). La barra verde si riempie proporzionalmente, con il contatore numerico affianco (es. "4 / 13").

### Ultimo allenamento
Card cliccabile che mostra il nome, la data e un riepilogo dell'allenamento più recente in assoluto (indipendentemente dal tipo). Toccandola si apre il dettaglio completo. Se non ci sono allenamenti, appare un messaggio vuoto.

### Pulsante "Registra allenamento"
Scorciatoia diretta alla tab Registra.

---

## Tab REGISTRA

Permette di inserire un nuovo allenamento. Il modulo cambia in base al tipo selezionato.

### Campi comuni a tutti i tipi
- **Tipo di sessione** — menu a tendina con tre opzioni: Palestra 🏋, Cardio 🚴, Escursione / Trekking 🥾
- **Nome sessione** — campo testuale libero (es. "Gambe e core", "Uscita Resegone"). Se lasciato vuoto, viene assegnato il nome del tipo automaticamente
- **Data** — selettore data, precompilato con la data odierna. Permette di inserire allenamenti passati o futuri

---

### Tipo: Palestra 🏋

Dopo aver selezionato Palestra appare la sezione **Esercizi**.

#### Aggiungere un esercizio
Tocca il pulsante **+ Aggiungi** in alto a destra della sezione. Si apre un pannello dal basso con:

- **Esercizio** — menu a tendina con tutti gli esercizi del catalogo (predefiniti + quelli aggiunti da te). Gli esercizi sono mostrati col nome; una volta selezionato, il sistema recupera automaticamente i dati dell'ultima sessione in cui lo hai eseguito e precompila il peso e le ripetizioni della prima serie come suggerimento
- **Numero di serie** — da 1 a 5 (default: 3)
- **Tabella serie** — per ogni serie: campo Peso (kg) e Ripetizioni. Il pulsante freccia verso il basso a destra di ogni serie copia il peso e le reps di quella riga in tutte le serie successive

Confermando con **Aggiungi**, l'esercizio appare nella lista.

#### Gestire gli esercizi già aggiunti
Ogni esercizio nella lista mostra il nome e, sotto, tutte le serie con peso × ripetizioni. Affianco al nome ci sono due pulsanti:
- **Modifica** (icona matita) — riapre il pannello precompilato con i valori attuali, inclusi esercizio selezionato, numero di serie e tutti i pesi/reps. Puoi modificare qualsiasi campo e confermare
- **Elimina** (icona cestino, rosso) — chiede conferma prima di rimuovere l'esercizio dalla sessione in corso

Puoi aggiungere lo stesso esercizio più volte: se lo selezioni una seconda volta, sovrascrive quello esistente (aggiorna le serie).

#### Salvataggio
Il pulsante **Salva allenamento** in fondo alla pagina salva la sessione. Richiede almeno un esercizio. Dopo il salvataggio tutti i campi vengono azzerati e si torna alla Home.

---

### Tipo: Cardio 🚴

Campi disponibili (tutti facoltativi tranne la data):
- **Durata** — in minuti
- **Distanza** — in km (con decimali)
- **Dislivello** — in metri (utile per uscite collinari o trail)
- **FC media** — frequenza cardiaca media in bpm
- **Zaino** — peso del carico portato in kg
- **Note** — campo testo libero per qualsiasi annotazione

---

### Tipo: Escursione / Trekking 🥾

Campi disponibili:
- **Durata** — in ore (con decimali, es. 3.5)
- **Distanza** — in km
- **Dislivello +** — dislivello positivo in metri
- **Quota max** — quota massima raggiunta in metri slm
- **Peso zaino** — in kg
- **Sensazione** — scala da 1 a 5 stelle: Molto dura / Faticosa / Nella media / Buona / Ottima
- **Note** — campo testo libero

---

## Tab SCHEDE

Le schede sono template pre-impostati di allenamenti che puoi preparare in anticipo e avviare con un tocco, senza dover riselezionare ogni volta tutti gli esercizi da zero.

### Creare una nuova scheda
Tocca **+ Nuova** in alto a destra. Si apre un pannello con:
- **Nome scheda** — nome libero (es. "Gambe pesante", "Scheda A")
- **Tipo** — Palestra, Cardio o Escursione
- Se il tipo è **Palestra**: sezione per aggiungere esercizi alla scheda, ciascuno con il numero di serie previste (da 1 a 5). Tocca **+ Aggiungi** per inserire ogni esercizio

Conferma con **Salva scheda**.

### Visualizzazione schede
Ogni scheda appare come una card con:
- Nome e tipo (con etichetta colorata)
- Elenco degli esercizi con il numero di serie (per le schede palestra), visualizzati come chip grigi
- Tre pulsanti: **Modifica**, **Elimina** (con conferma), **Inizia**

### Avviare una scheda
Tocca **Inizia**. Si apre un pannello di anteprima con l'elenco degli esercizi e le serie previste. Toccando **Inizia allenamento**:
- Vai automaticamente alla tab Registra
- Il nome della scheda è precompilato come nome sessione
- La data è impostata su oggi
- Tutti gli esercizi della scheda sono già caricati, con pesi e ripetizioni precompilati dall'ultima sessione in cui li hai eseguiti (se disponibili)
- Puoi aggiungere altri esercizi liberamente, modificare serie e pesi, e salvare normalmente

### Modificare una scheda
Tocca **Modifica**: si riapre il pannello precompilato con i dati attuali. Puoi cambiare nome, tipo, aggiungere o rimuovere esercizi (con conferma alla rimozione).

---

## Tab STORICO

Mostra tutti gli allenamenti salvati in ordine cronologico inverso (il più recente in cima).

### Filtri
Quattro pill in cima permettono di filtrare per tipo:
- **Tutti** — mostra tutto
- **Palestra** — solo sessioni in palestra
- **Cardio** — solo cardio
- **Escursioni** — solo escursioni/trekking

### Lista allenamenti
Ogni voce mostra:
- Data (giorno della settimana, giorno, mese, anno)
- Nome sessione
- Riepilogo rapido: per la palestra, la lista degli esercizi; per cardio ed escursioni, durata, distanza e dislivello
- Etichetta colorata del tipo (blu = palestra, verde = cardio, arancione = escursione)

### Dettaglio allenamento
Tocca qualsiasi voce per aprire il pannello di dettaglio completo:
- **Palestra** — tutti gli esercizi con ogni serie, peso e ripetizioni
- **Cardio / Escursione** — tutte le metriche inserite, griglia di card, sensazione (per le escursioni), note
- Pulsante **Elimina** (con conferma) per cancellare l'allenamento definitivamente

---

## Tab PROGRESSI

Contiene tre sezioni grafiche distinte.

### 1. Analisi esercizio (grafico linea)
Un menu a tendina mostra tutti gli esercizi per cui hai registrato almeno una sessione con pesi. Selezionandone uno appare:
- **Badge PR** — il tuo Personal Record: il peso massimo mai sollevato in quell'esercizio (e le ripetizioni fatte a quel peso)
- **Badge Ultima** — il peso massimo nell'ultima sessione in cui hai fatto quell'esercizio
- **Badge sessioni** — quante volte totali hai eseguito quell'esercizio
- **Grafico a linea** — andamento del carico massimo per sessione nel tempo (asse X = data, asse Y = kg). Mostra solo le sessioni con dati validi di peso

### 2. Volume settimanale (grafico a barre)
Istogramma delle ultime **8 settimane** con barre impilate per tipo:
- 🔵 Blu = sessioni di palestra
- 🟢 Verde = sessioni cardio
- 🟠 Arancione = escursioni

Ogni barra rappresenta quante sessioni totali hai fatto in quella settimana, suddivise per tipo. Appare solo se hai almeno un allenamento registrato.

### 3. Dislivello escursioni (grafico a barre)
Mostra le ultime **12 uscite** (escursioni o cardio) per cui è stato inserito un valore di dislivello. Ogni barra rappresenta i metri di dislivello positivo di quella uscita. Le uscite senza dislivello inserito non appaiono. Utile per vedere la progressione del carico di allenamento outdoor.

---

## Tab ESERCIZI

Catalogo completo di tutti gli esercizi disponibili nell'app, raggruppati per categoria muscolare.

### Categorie disponibili
Gambe · Schiena · Petto · Spalle · Bicipiti · Tricipiti · Avambracci · Polpacci · Core · Full body

### Esercizi predefiniti (17)
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

### Informazioni mostrate per ogni esercizio
- Nome
- Numero di sessioni in cui è stato eseguito
- **Badge PR** — peso massimo × ripetizioni mai raggiunti in quell'esercizio (appare solo se hai almeno una serie con dati validi)

### Aggiungere un esercizio
Tocca **+ Nuovo** in alto a destra. Campi richiesti:
- **Nome** — obbligatorio
- **Categoria** — da selezionare tra quelle disponibili
- **Unità** — kg oppure Corpo libero

L'esercizio viene salvato nel catalogo e diventa immediatamente disponibile nei menu di selezione durante la registrazione e nella creazione di schede.

---

## Tab DATI

Sezione di gestione dati e impostazioni avanzate.

### Gestione esercizi
Lista completa di tutti gli esercizi del catalogo, organizzati per categoria, con indicazione dell'unità (kg / corpo libero). Per ogni esercizio:
- **Cestino** — elimina l'esercizio dal catalogo (con conferma). Attenzione: gli esercizi eliminati spariscono dalla lookup ma rimangono nei dati degli allenamenti già salvati

Pulsante **+ Aggiungi esercizio** — apre lo stesso pannello della tab Esercizi per inserirne uno nuovo.

### Esporta dati
Permette di scaricare i dati in due formati.

**Tipo di dati esportabili:**
- Tutti gli allenamenti
- Solo palestra
- Solo cardio
- Solo escursioni
- Lista esercizi

**Periodo:**
- Tutto
- Ultimo mese
- Ultimi 3 mesi
- Ultimo anno

**Formato:**
- **JSON** — formato completo, adatto per backup e reimportazione nell'app. Contiene tutti i dati strutturati
- **CSV** — formato tabellare, apribi con Excel o Fogli Google. Per la palestra include una riga per ogni serie di ogni esercizio; per cardio/escursioni una riga per sessione

Il file viene scaricato nella cartella Download del dispositivo con nome automatico tipo `workout_allenamenti_2026-05-31.json`.

### Importa dati
Carica un file JSON precedentemente esportato dall'app. Il sistema importa solo gli allenamenti non già presenti (controlla per ID), quindi non crea duplicati. I dati esistenti vengono mantenuti.

### Dati app
Mostra il numero totale di sessioni registrate. Il pulsante **Cancella tutto** elimina definitivamente tutti gli allenamenti (con doppia conferma). Gli esercizi e le schede non vengono cancellati.

### Come installare l'app
Istruzioni rapide per aggiungere l'app alla schermata Home del telefono.

---

## Backup automatico domenicale

Ogni **domenica sera alle 23:00**, se l'app è aperta, appare automaticamente un banner arancione in fondo allo schermo che ricorda di fare il backup.

Il banner offre due opzioni:
- **Scarica backup JSON** — scarica immediatamente un file JSON completo con tutti i dati (allenamenti, esercizi, schede). Il file si chiama `workout_backup_YYYY-MM-DD.json`
- **Dopo** — chiude il banner senza scaricare; non riapparirà fino alla domenica successiva

Il controllo avviene al caricamento dell'app e ogni 30 minuti. Il banner non appare se non ci sono allenamenti registrati, oppure se hai già scaricato o rimandato il backup in quella settimana.

**Come ripristinare da backup:** tab Dati → Importa dati → seleziona il file JSON salvato.

---

## Come vengono salvati i dati

Tutti i dati sono salvati nel **localStorage** del browser, una memoria locale permanente del dispositivo. Non esiste nessun server, nessun cloud, nessun account. I dati non lasciano mai il tuo telefono.

### Cosa viene salvato
Un unico oggetto JSON con tre sezioni:
- `exercises` — catalogo di tutti gli esercizi
- `workouts` — lista di tutti gli allenamenti con tutti i dettagli
- `templates` — le schede pre-impostate

### Quando i dati possono andare persi
| Causa | Rischio | Come evitarlo |
|-------|---------|---------------|
| Svuotare la cache del browser | 🔴 Dati cancellati | Esportare JSON prima di farlo |
| Cancellare i dati del sito in Safari/Chrome | 🔴 Dati cancellati | Esportare JSON prima di farlo |
| Disinstallare il browser | 🔴 Dati cancellati | Esportare JSON prima di farlo |
| Spegnere o riavviare il telefono | ✅ Nessun rischio | — |
| Chiudere l'app o il browser | ✅ Nessun rischio | — |
| Aggiornare l'app (GitHub Pages) | ✅ Nessun rischio | — |
| Cambiare browser (es. da Safari a Chrome) | 🟡 Dati non visibili | Esportare da un browser e importare nell'altro |
| Passare a un telefono nuovo | 🟡 Dati non trasferiti | Esportare JSON e importare sul nuovo dispositivo |

**Regola d'oro:** esegui il backup JSON ogni domenica sera (l'app te lo ricorda). Salva il file su iCloud o Google Drive.

---

## Installazione sul telefono

### iPhone — obbligatorio usare Safari
1. Apri **Safari** e vai su `https://t-ivan2.github.io/Workout-Toubkal/`
2. Tocca l'icona **condividi** (quadrato con freccia verso l'alto, in fondo alla barra)
3. Scorri l'elenco e tocca **"Aggiungi a schermata Home"**
4. Modifica il nome se vuoi e tocca **Aggiungi**

L'app apparirà come icona sulla schermata Home, si aprirà a schermo intero senza la barra di Safari, e funzionerà offline.

> ⚠️ Su iPhone, Chrome e altri browser non permettono l'installazione PWA — usa solo Safari.

### Android — usa Chrome
1. Apri **Chrome** e vai sul link dell'app
2. Chrome mostra automaticamente un banner in basso → tocca **Installa**
3. In alternativa: tocca il menu ⋮ in alto a destra → "Aggiungi a schermata Home" o "Installa app"

### Condividere l'app con altri
Basta mandare il link `https://t-ivan2.github.io/Workout-Toubkal/` — chiunque può aprirlo e installarlo sul proprio telefono. Ogni utente avrà i propri dati separati e indipendenti (il localStorage è locale al dispositivo di ciascuno).

---

*Documentazione generata il 31 maggio 2026*
