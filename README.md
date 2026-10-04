# Progetto ES2M

Repository dedicata allo sviluppo e alla gestione della **relazione del corso ES2M**.

La repository contiene i file sorgente della relazione, scritti in **LaTeX**, e il materiale necessario alla sua compilazione.

---

## 📑 Indice

* [LaTeX](#latex)
* [Struttura della repository](#struttura-della-repository)
* [Introduzione a Git e GitHub](#introduzione-a-git-e-github)
* [Workflow di lavoro](#workflow-di-lavoro)
* [Comandi principali](#comandi-principali)
* [Convenzioni per i commit](#convenzioni-per-i-commit)
* [Risoluzione dei conflitti](#risoluzione-dei-conflitti)
* [Regola importante](#-regola-importante)

---

## LaTeX

La relazione è scritta utilizzando **LaTeX**.

Per poter modificare e compilare il documento è necessario disporre di:

* un **distribuzione LaTeX**, che fornisce il compilatore e i pacchetti necessari;
* un **editor/IDE** compatibile con LaTeX.

### Windows

Per l'installazione dell'ambiente LaTeX su Windows è disponibile la seguente guida:

[Installazione LaTeX offline con VS Code](https://github.com/Nicklosss/Installazione-LaTeX-offline-con-VSCODE)

---

## Struttura della repository

La struttura della repository può essere organizzata indicativamente nel seguente modo:

```text
Progetto_ES2M/
│
├── main.tex
├── capitoli/
├── immagini/
└── bibliografia.bib
│
├── README.md
└── .gitignore
```

La struttura effettiva può variare in base all'organizzazione scelta per il progetto.

### File principali

| File/Cartella      | Descrizione                                         |
| ------------------ | --------------------------------------------------- |
| `main.tex`         | File principale della relazione                     |
| `capitoli/`        | Contiene i singoli capitoli/sezioni della relazione |
| `immagini/`        | Contiene le immagini utilizzate nel documento       |
| `bibliografia.bib` | File contenente le fonti bibliografiche             |
| `README.md`        | Documentazione della repository                     |
| `.gitignore`       | Specifica i file che Git deve ignorare              |

---

# Introduzione a Git e GitHub

**Git** è un sistema di controllo di versione che permette di registrare e gestire le modifiche apportate ai file di un progetto.

**GitHub** è una piattaforma che permette di ospitare repository Git online, facilitandone la condivisione e la collaborazione tra più persone.

Nel nostro progetto Git viene utilizzato per mantenere sincronizzato il lavoro dei componenti del gruppo e tenere traccia delle modifiche effettuate alla relazione.

---

# Workflow di lavoro

Per ridurre il rischio di conflitti tra le modifiche effettuate dai diversi membri del gruppo, si consiglia di seguire il seguente flusso di lavoro:

```text
1. git pull
      ↓
2. Modifica dei file
      ↓
3. git add
      ↓
4. git commit
      ↓
5. git push
```

### 1. Aggiornare la repository locale

Prima di iniziare a lavorare:

```bash
git pull
```

Questo permette di scaricare le modifiche più recenti presenti sulla repository remota.

### 2. Modificare i file

A questo punto è possibile lavorare sulla relazione utilizzando il proprio editor/IDE.

### 3. Aggiungere le modifiche

Una volta terminato il lavoro, è necessario indicare a Git quali file devono essere inclusi nel prossimo commit.

Per aggiungere un singolo file:

```bash
git add <nomeFile.estensione>
```

Per aggiungere più file:

```bash
git add <nomeFile1.estensione> <nomeFile2.estensione>
```

Per aggiungere tutti i file modificati:

```bash
git add .
```

### 4. Creare un commit

Dopo aver aggiunto i file, è possibile creare un commit:

```bash
git commit -m "<Descrizione dei cambiamenti effettuati>"
```

Ad esempio:

```bash
git commit -m "Aggiunta introduzione"
```

Il messaggio del commit deve descrivere brevemente le modifiche effettuate.

### 5. Caricare le modifiche su GitHub

Per inviare i commit alla repository remota:

```bash
git push origin main
```

Una volta completato il `push`, le modifiche saranno disponibili sulla repository GitHub per gli altri membri del gruppo.

---

# Comandi principali

## `git pull`

Aggiorna la repository locale scaricando le modifiche presenti sulla repository remota.

```bash
git pull
```

---

## `git status`

Mostra lo stato della repository locale, indicando ad esempio quali file sono stati modificati o quali sono pronti per essere inclusi in un commit.

```bash
git status
```

È un comando molto utile per controllare cosa verrà incluso nel prossimo commit.

---

## `git add`

Aggiunge i file all'area di staging, preparando le modifiche per il commit.

```bash
git add <nomeFile.estensione>
```

oppure:

```bash
git add .
```

---

## `git commit`

Registra le modifiche nell'area di staging nella cronologia locale del progetto.

```bash
git commit -m "Descrizione delle modifiche"
```

---

## `git push`

Invia i commit locali alla repository remota.

```bash
git push origin main
```

---

## `git log`

Permette di visualizzare la cronologia dei commit effettuati.

```bash
git log
```

---

# Convenzioni per i commit

Per mantenere una cronologia ordinata e facilmente comprensibile, si consiglia di utilizzare messaggi di commit **brevi, chiari e descrittivi**.

### Esempi consigliati

```text
Aggiunta introduzione
```

```text
Aggiunto capitolo sulla metodologia
```

```text
Correzione formule matematiche
```

```text
Aggiunte immagini al capitolo 2
```

```text
Correzione errori di formattazione
```

### Da evitare

Messaggi troppo generici come:

```text
modifiche
```

```text
update
```

```text
prova
```

```text
varie
```

Un buon messaggio di commit permette agli altri membri del gruppo di capire rapidamente quali modifiche sono state effettuate.

---

# Gestione delle modifiche alla relazione

Quando possibile, è consigliabile evitare che più persone modifichino contemporaneamente le **stesse parti dello stesso file LaTeX**.

Ad esempio, se la relazione è suddivisa in più capitoli, è preferibile che ogni capitolo sia contenuto in un file `.tex` separato:

```text
capitoli/
├── introduzione.tex
├── metodologia.tex
├── risultati.tex
└── conclusioni.tex
```

Il file `main.tex` può quindi includere i diversi capitoli.

Questa organizzazione riduce la possibilità che due persone modifichino contemporaneamente le stesse righe di codice e rende più semplice la gestione della collaborazione.

---

# Risoluzione dei conflitti

Un **conflitto** può verificarsi quando due persone modificano la stessa parte di un file e Git non è in grado di determinare automaticamente quale versione mantenere.

In caso di conflitto, **non eseguire comandi casualmente e non sovrascrivere il lavoro degli altri membri del gruppo**.

Il file interessato conterrà delle indicazioni simili a:

```text
<<<<<<< HEAD
Modifica locale
=======
Modifica proveniente dalla repository remota
>>>>>>> ...
```

È necessario analizzare le due versioni, decidere quali modifiche mantenere e rimuovere i marcatori del conflitto.

Dopo aver risolto il conflitto:

```bash
git add <file>
git commit -m "Risoluzione conflitto"
git push origin main
```

In caso di dubbi, è preferibile chiedere agli altri membri del gruppo prima di procedere.

---

# ⚠️ Regola importante

**Prima di iniziare a lavorare alla relazione, eseguire sempre:**

```bash
git pull
```

In questo modo si lavora sulla versione più recente disponibile della repository e si riduce il rischio di creare conflitti con le modifiche effettuate dagli altri membri del gruppo.

### Workflow consigliato

In sintesi:

```bash
# 1. Aggiornare la repository
git pull

# 2. Lavorare sui file

# 3. Controllare le modifiche
git status

# 4. Aggiungere i file modificati
git add .

# 5. Creare il commit
git commit -m "Descrizione delle modifiche"

# 6. Caricare le modifiche su GitHub
git push origin main
```
