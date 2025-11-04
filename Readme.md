<!--s-->
## Trasferimento e Condivisione della conoscenza
La storia dell’umanità è, prima di tutto, la storia del trasferimento della conoscenza.
Dalla parola orale alla scrittura, dalla stampa fino al mondo digitale, ogni progresso è nato dalla capacità di trasmettere, condividere e trasformare ciò che sappiamo.

Nel Medioevo la conoscenza passava dai maestri agli apprendisti; nel Rinascimento circolava tra le accademie e le corti; oggi viaggia in tempo reale attraverso reti globali, università e imprese.
<!--v-->
Nel corso dei secoli, anche i supporti utilizzati per trasferire la conoscenza si sono evoluti profondamente.
All’inizio erano la tradizione orale e la memoria collettiva, strumenti fragili ma potenti, grazie ai quali miti, riti e tecniche venivano tramandati di generazione in generazione.

Poi arrivò la scrittura, che rese possibile fissare il sapere nel tempo: dalle tavolette d’argilla alle pergamene, fino ai manoscritti custoditi nei monasteri.<!-- .element: class="fragment text-justify" data-fragment-index="1" -->

Con l’invenzione della stampa a caratteri mobili, la conoscenza uscì dalle biblioteche e divenne patrimonio condiviso, contribuendo in modo decisivo alla diffusione delle idee scientifiche e umanistiche del Rinascimento.<!-- .element: class="fragment text-justify" data-fragment-index="2" -->

<!--v-->
### Questo flusso continuo di saperi ha portato tre vantaggi fondamentali:
- ##### Innovazione .... Ci permette di costruire su esperienze già acquisite, accelerando il progresso scientifico e tecnologico. <!-- .element: class="fragment text-justify" data-fragment-index="0" -->
- ##### Efficienza .... Condividere buone pratiche riduce gli errori e migliora la produttività delle organizzazioni. <!-- .element: class="fragment text-justify" data-fragment-index="1" -->
- ##### Crescita .... collettiva Diffondere conoscenza significa diffondere opportunità: favorisce sviluppo economico, dialogo culturale e coesione sociale. <!-- .element: class="fragment text-justify" data-fragment-index="2" -->

Oggi, nel pieno dell’era digitale, il trasferimento della conoscenza è ancora più strategico. Non basta accumulare informazioni: serve la capacità di trasformarle in valore, di adattarle e di farle circolare tra persone, istituzioni e generazioni.<!-- .element: class="fragment text-justify" data-fragment-index="3" -->

<!--s-->
# Linus Torvalds
## La nascita di GIT (2005)

<table width="100%" height="100%">
  <tr>
    <td width="40%"><img src="img/linus-torvalds.jpeg" alt="Linus Torvalds" width="80%" height="80%"></td>  
    <td>
      I motivi che hanno spinto Linus Torvalds a creare Git nel 2005 sono stati principalmente legati alla crisi del sistema di controllo versione che il kernel Linux stava utilizzando.<!-- .element: class="text-justify top" -->
      <h4>&nbsp;</h4>
    </td>
  </tr>
</table>
<!--v-->

## Il Problema con BitKeeper (2005)

**BitKeeper Crisis**: Fino al 2005, il progetto del kernel Linux utilizzava BitKeeper, un sistema di controllo versione distribuito proprietario. 

La società BitMover aveva concesso una licenza gratuita per progetti open source, ma nell'aprile 2005 **revocò questa licenza gratuita**<!-- .element: class="text-highlights" --> dopo dispute riguardanti il reverse engineering del protocollo da parte di alcuni sviluppatori della community Linux.

<!--v-->
## Le Frustrazioni di Linus

### 1. Sistemi Esistenti Inadeguati
- CVS: Troppo lento e centralizzato, non gestiva bene i merge<!-- .element: class="fragment text-justify" data-fragment-index="0" -->
- Subversion: Ancora centralizzato, non abbastanza veloce per un progetto delle dimensioni del kernel Linux<!-- .element: class="fragment text-justify" data-fragment-index="1" -->
- Altri sistemi distribuiti: Non esistevano o erano troppo complessi/lenti<!-- .element: class="fragment text-justify" data-fragment-index="2" -->

<!--v-->

### **2. Requisiti Specifici del Kernel Linux**
- Scale massive: Migliaia di sviluppatori, milioni di righe di codice <!-- .element: class="fragment text-justify" data-fragment-index="0" -->
- Merge frequenti: Centinaia di patch al giorno da integrare<!-- .element: class="fragment text-justify" data-fragment-index="1" -->
- Velocità: Operazioni che dovevano completarsi in secondi, non minuti<!-- .element: class="fragment text-justify" data-fragment-index="2" -->
- Integrità: Garanzia assoluta che i dati non fossero corrotti<!-- .element: class="fragment text-justify" data-fragment-index="3" -->
- Workflow distribuito: Sviluppatori in tutto il mondo senza server centrale<!-- .element: class="fragment text-justify" data-fragment-index="4" -->

<!--v-->
## **La "Crisi" del Weekend**

**Timeline critica**:
```json [1|1-2|1-3|1-4|1-5]
- 3 Aprile 2005: BitMover annuncia la fine della licenza gratuita
- 6-7 Aprile 2005: Linus inizia a sviluppare Git
- 7 Aprile 2005: Primo commit di Git
- 16 Aprile 2005: Git si auto-ospita (Git gestisce il proprio codice sorgente)
- 26 Luglio 2005: Primo kernel Linux gestito con Git
```
<!--v-->

# **Filosofia di Design di Git**

Linus aveva requisiti molto specifici:

## Performance
> "Git is designed to be very fast. All operations should complete in a few seconds at most"

## Integrità dei Dati
- Ogni oggetto è identificato dal suo hash SHA-1
- Impossibile corrompere file senza accorgersene
- Verifica automatica dell'integrità

<!--v-->
### Semplicità Concettuale
- Poche operazioni primitive ma potenti
- Modello di dati semplice (blob, tree, commit, tag)

### Supporto per Workflow Non-lineari
- Branch rapidi e economici
- Merge intelligente e automatico
- Supporto per migliaia di branch paralleli

<!--v-->
## Le Critiche ai Sistemi Esistenti

Linus era particolarmente critico verso:

### CVS/Subversion:
- "CVS è l'esempio di cosa NON fare"
- Troppo lento per operazioni su larga scala
- Merge problematici
- Modello centralizzato inadeguato

### Altri DVCS(Distributed Version Control System) dell'epoca:
- **Monotone**: Troppo lento, design over-engineered
- **Darcs**: Problemi di performance con repository grandi
- **Bazaar**: Non esisteva ancora in forma utilizzabile
<!--v-->
## Il Fattore Personalità

### Pragmatismo Estremo
Linus voleva qualcosa che "funzionasse semplicemente" senza filosofie complicate:
> "I'm an engineer. I see a problem and I fix it"

### Controllo Totale
Dopo l'esperienza con BitKeeper, Linus voleva:
- Nessuna dipendenza da software proprietario
- Controllo completo degli algoritmi e delle decisioni di design
- Garanzia che non si ripetesse mai più una "crisi BitKeeper"
<!--v-->
## L'Urgenza della Situazione

La community Linux aveva bisogno di una soluzione **immediata**:
- Il prossimo rilascio del kernel (2.6.12) era imminente
- Migliaia di patch in attesa di essere integrate
- Impossibilità di tornare a sistemi primitivi come patch e tar

<!--v-->
## Risultato

Git fu sviluppato in tempo record:
- **2 settimane**<!-- .element: class="text-highlights" --> per la prima versione funzionante
- **3 mesi**<!-- .element: class="text-highlights" --> per diventare il sistema ufficiale del kernel Linux
- **Meno di 1 anno**<!-- .element: class="text-highlights" --> per diventare lo standard de facto per progetti open source

<!--v-->
### La Filosofia "Do One Thing Well"<!-- .slide: class="top-50" -->

Linus applicò la filosofia Unix anche a Git:
- Ogni comando fa una cosa specifica molto bene
- Componibilità: i comandi si combinano per operazioni complesse
- Efficienza: ottimizzato per le operazioni più comuni

**Citazione famosa di Linus**:
> "I really never wanted to do source control management at all and felt that it was just about the least interesting thing in the computing world, but somebody had to do it."

<!--v-->
### IN CONCLUSIONE

La creazione di Git fu quindi una **necessità pratica urgente** più che una passione per i sistemi di controllo versione, ma il risultato fu rivoluzionario per l'intero mondo dello sviluppo software.

- **Problemi risolti**: 
  - Gestione versioni distribuite
  - Collaborazione in team
  - Tracciabilità delle modifiche

<!--s-->
### Setup dell'Ambiente
**🛠️ HANDS-ON**: Preparazione workstation
- Installazione GIT sui notebook dei partecipanti

## 🪟 **Windows**

1. Vai su [https://git-scm.com/download/win](https://git-scm.com/download/win)
2. Scarica il file `Git-<version>.exe`
3. Esegui l’installer e segui la procedura guidata:
   - Mantieni le opzioni predefinite consigliate.
   - Seleziona *“Git Bash Here”* per aggiungere Git al menu contestuale.
4. Al termine, apri **Git Bash** e verifica:
```bash
git --version
```
<!--v-->

## 🍏 macOS
Installa Homebrew se non lo hai già, e poi installa Git:
```bash
brew install git
```
**Metodo 2 — Tramite Xcode Command Line Tools**
```bash
xcode-select --install
```
**Verifica l’installazione:**
```bash
git --version
```
<!--v-->
## 🐧 Linux
**Ubuntu / Debian**
```bash
sudo apt update
sudo apt install git -y
```
**Fedora**
```bash
sudo dnf install git -y
```
**CentOS / RHEL**
```bash
sudo yum install git -y
```
**Arch Linux**
```bash
sudo pacman -S git
```
**Verifica l’installazione:**
```bash
git --version
```
<!--s-->
### Configurazione iniziale:
  ```bash
  git config --global user.name "Nome Cognome"
  git config --global user.email "email@unich.it"
  git config --global init.defaultBranch main
  ```
- Test di connessione a GitHub
- Setup editor preferito (VS Code, nano, vim)

<!--v-->
### Concetti Fondamentali

#### Concetti Base
- **Repository**: cartella "intelligente" con cronologia 
- **Commit**: snapshot del lavoro
- **Staging Area**: area di preparazione
- **Working Directory**: cartella di lavoro
- **Branch**: linee di sviluppo parallele
<!--v-->
### Git - Repository<!-- .slide: class="top-50" -->

Un repository Git (o repo) è lo spazio in cui viene memorizzato e gestito il codice sorgente di un progetto, insieme alla storia completa delle modifiche.<!-- .element: class="small" -->

In sintesi:<!-- .element: class="small" -->

- È un archivio che contiene file, cartelle e versioni del progetto nel tempo<!-- .element: class="small" -->
- Permette a più sviluppatori di collaborare, condividere modifiche, ripristinare versioni precedenti e gestire rami di sviluppo (branch)<!-- .element: class="small" -->

Un repository può essere:<!-- .element: class="fragment small" data-fragment-index="0" -->

- Locale → sul computer dello sviluppatore (git init)<!-- .element: class="fragment small" data-fragment-index="0" -->
- Remoto → su una piattaforma come GitHub, GitLab o Bitbucket, per la collaborazione online.<!-- .element: class="fragment small" data-fragment-index="1" -->
- 💡 In breve un repository Git è la memoria storica e collaborativa del codice di un progetto.<!-- .element: class="fragment small" data-fragment-index="2" -->

<!--v-->
### Git - Commit
Un git commit è un’istantanea (snapshot) dello stato del progetto in un determinato momento.

In pratica:<!-- .element: class="fragment" data-fragment-index="0" -->

- Registra le modifiche apportate ai file nel repository<!-- .element: class="fragment" data-fragment-index="1" -->
- Include un messaggio descrittivo che spiega cosa è stato cambiato<!-- .element: class="fragment" data-fragment-index="2" -->
- Diventa parte della cronologia del progetto, permettendo di tornare indietro o confrontare versioni<!-- .element: class="fragment" data-fragment-index="3" -->
- 💡 In breve: Un commit è come un “salvataggio” ufficiale del progetto nel tempo, con autore, data e descrizione delle modifiche<!-- .element: class="fragment" data-fragment-index="4" -->
<!--v-->
### Git - Staging Area
La staging area (o area di preparazione) è una zona intermedia di Git dove vengono raccolte le modifiche prima di confermarle con un commit.

In pratica:<!-- .element: class="fragment" data-fragment-index="0" -->

- Permette di scegliere quali file o modifiche includere nel prossimo commit<!-- .element: class="fragment" data-fragment-index="0" -->
- Funziona come un “piano di lavoro temporaneo” tra il working directory e il repository<!-- .element: class="fragment" data-fragment-index="1" -->
- 💡 In breve: La staging area è l’area in cui prepari con precisione ciò che verrà salvato nel prossimo commit<!-- .element: class="fragment" data-fragment-index="2" -->

<!--v-->
### Git - Working Directory
La working directory è la cartella del progetto sul tuo computer dove lavori sui file tracciati da Git.

In pratica:<!-- .element: class="fragment" data-fragment-index="0" -->

- Contiene la versione attuale dei file del repository<!-- .element: class="fragment" data-fragment-index="0" -->
- È l’area in cui modifichi, aggiungi o elimini file prima di metterli in staging o fare un commit<!-- .element: class="fragment" data-fragment-index="2" -->
- 💡 In breve: La working directory è lo spazio di lavoro locale in cui apporti le modifiche al progetto gestito da Git<!-- .element: class="fragment" data-fragment-index="3" -->

<!--v-->
### Git - Branch
Un branch in Git è un ramo di sviluppo indipendente che consente di lavorare su nuove funzionalità o correzioni senza modificare il codice principale.

In pratica:<!-- .element: class="fragment" data-fragment-index="0" -->

- Ogni branch rappresenta una linea separata di sviluppo<!-- .element: class="fragment" data-fragment-index="0" -->
- Puoi creare, unire o eliminare branch per gestire versioni o funzionalità diverse del progetto<!-- .element: class="fragment" data-fragment-index="2" -->
- 💡 In breve: Un branch è una copia del codice su cui puoi lavorare in parallelo, senza influenzare il ramo principale (main o master).<!-- .element: class="fragment" data-fragment-index="3" -->

<!--s-->

## Il Primo Repository
**🛠️ HANDS-ON**: Creazione repository
```bash
# Creiamo una cartella per documentazione IT
mkdir doc-procedure-it
cd doc-procedure-it
git init

# Primo file: procedura backup
echo "# Procedure di Backup Server" > backup-procedure.md
echo "## Backup giornaliero" >> backup-procedure.md
echo "1. Verifica spazio disco" >> backup-procedure.md

git add backup-procedure.md
git commit -m "Prima versione procedura backup"
```
<!--v-->
## Lavorare con i File
**🛠️ HANDS-ON**: Modifiche e commit
```bash
# Aggiungiamo un file binario (simuliamo un PDF)
cp /path/to/sample.pdf checklist-backup.pdf
git add checklist-backup.pdf

# Modifichiamo il file esistente
echo "2. Esecuzione script backup.sh" >> backup-procedure.md
echo "3. Verifica log errori" >> backup-procedure.md

git add backup-procedure.md
git commit -m "Aggiunta checklist e nuovi passi procedura"

# Vediamo la storia
git log --oneline
git diff HEAD~1 HEAD
```
<!--v-->
## Gestione Avanzata Locale

#### Navigare nella Storia
**🛠️ HANDS-ON**: Esplorare i commit
```bash
# Vediamo cosa è cambiato
git log --stat
git log --graph --oneline

# Torniamo indietro per vedere una versione precedente
git checkout HEAD~1
cat backup-procedure.md

# Torniamo al presente
git checkout main

# Correggiamo l'ultimo commit
echo "4. Notifica completamento backup" >> backup-procedure.md
git add backup-procedure.md
git commit --amend -m "Procedura backup completa con notifiche"
```
<!--v-->
## Gestione dei Branch
**🛠️ HANDS-ON**: Creazione e uso branch
```bash
# Creiamo un branch per una nuova procedura
git checkout -b procedura-restore

# Nuovo file per restore
echo "# Procedure di Restore Server" > restore-procedure.md
echo "1. Identificazione backup da ripristinare" >> restore-procedure.md
git add restore-procedure.md
git commit -m "Inizio procedura restore"

# Torniamo su main e vediamo la differenza
git checkout main
ls  # restore-procedure.md non c'è
git checkout procedura-restore
ls  # restore-procedure.md c'è

# Merge del branch
git checkout main
git merge procedura-restore
```
<!--s-->

## Collaborazione e Strumenti Avanzati
### Lavoro Distribuito

#### **4.1 Repository Remoti (45 min)**
**🛠️ HANDS-ON**: Connessione a GitLab@UdA

```bash
# Cloniamo un repository esistente su GitLab@UdA
git clone https://gitlab.unich.it/corso-git/esempio-documentazione.git
cd esempio-documentazione

# Esploriamo il repository
git status
git log --oneline
git remote -v

# Creiamo un nuovo repo sulla nostra area personale GitLab
# (tramite interfaccia web)

# Aggiungiamo il nostro repo locale come remoto
cd ../doc-procedure-it
git remote add origin https://gitlab.unich.it/[username]/doc-procedure-it.git

# Push del nostro lavoro
git push -u origin main
```

#### **4.2 Collaborazione Base (45 min)**
**🛠️ HANDS-ON**: Push e Pull
```bash
# Simuliamo lavoro di un collega (dal docente)
# Modifica da interfaccia web GitLab

# I partecipanti fanno pull
git pull origin main

# Ogni partecipante fa una modifica locale
echo "## Procedura di Monitoring" >> backup-procedure.md
echo "- Controllo stato servizi ogni 30 min" >> backup-procedure.md

git add backup-procedure.md
git commit -m "Aggiunta sezione monitoring"

# Push delle modifiche
git push origin main
```

---

### **SESSIONE 5: Gestione Conflitti (10:45-12:15)**

#### **5.1 Generazione e Risoluzione Conflitti (45 min)**
**🛠️ HANDS-ON**: Conflitti reali
```bash
# Il docente modifica lo stesso file dalla web interface
# I partecipanti modificano localmente la stessa riga

echo "## Backup Schedulati ore 02:00" >> backup-procedure.md
git add backup-procedure.md
git commit -m "Orario backup specificato"

# Tentativo di push (fallirà)
git push origin main

# Pull per scaricare le modifiche remote
git pull origin main
# CONFLITTO!

# Risoluzione conflitto con editor
# Spiegazione dei marker <<<<<<< ======= >>>>>>>
# Risoluzione manuale e commit

git add backup-procedure.md
git commit -m "Risolto conflitto orario backup"
git push origin main
```

#### **5.2 Buone Pratiche nei Messaggi di Commit (45 min)**
**🛠️ HANDS-ON**: Analisi repository reali
```bash
# Analizziamo commit ben scritti
git log --oneline -10

# Esempio di commit messages efficaci:
# "Fix: risolto bug calcolo spazio disco nelle procedure backup"
# "Add: nuova procedura restore database PostgreSQL"
# "Update: aggiornate credenziali accesso server backup"
# "Doc: completata documentazione troubleshooting restore"

# Comando git blame per vedere chi ha modificato cosa
git blame backup-procedure.md

# Colleghiamoci a un repository complesso (es. PostgreSQL)
git clone https://github.com/postgres/postgres.git
cd postgres
git log --oneline -20
git log --grep="backup"
```

---

### **PAUSA PRANZO (12:15-14:00)**

---

### **SESSIONE 6: GitLab e Workflow Avanzati (14:00-15:00)**

#### **6.1 Piattaforme Git Web-Based (20 min)**
- **GitLab vs GitHub vs Bitbucket**: differenze e scelte
- **Funzionalità aggiuntive**:
  - Issue tracking per segnalazioni
  - Wiki integrata per documentazione
  - CI/CD pipeline
  - Code review
- **Perché GitLab@UdA**: controllo, privacy, integrazione GARR

#### **6.2 Workflow di Gruppo (40 min)**
**🛠️ HANDS-ON**: Branch e Merge Request

```bash
# Workflow GitFlow semplificato
git checkout -b feature/procedura-disaster-recovery

# Sviluppiamo la nuova feature
echo "# Disaster Recovery Plan" > disaster-recovery.md
echo "## Fase 1: Valutazione Danni" >> disaster-recovery.md
echo "- Identificazione servizi compromessi" >> disaster-recovery.md
echo "- Stima tempi di ripristino" >> disaster-recovery.md

git add disaster-recovery.md
git commit -m "Add: bozza disaster recovery plan"

echo "## Fase 2: Ripristino Servizi Critici" >> disaster-recovery.md
echo "- Database principale" >> disaster-recovery.md
echo "- Servizi autenticazione" >> disaster-recovery.md

git add disaster-recovery.md
git commit -m "Add: fase 2 disaster recovery"

# Push del branch
git push origin feature/procedura-disaster-recovery
```

**Tramite GitLab Web Interface:**
- Creazione Merge Request
- Assegnazione reviewer
- Discussione e feedback
- Merge finale

---

## **SESSIONE 7: Sicurezza e Best Practices (Durante entrambe le giornate)**

### **7.1 Cosa NON fare - Gestione Segreti**
**🛠️ HANDS-ON**: Simulazione errore comune
```bash
# ERRORE: Commit accidentale di password
echo "DB_PASSWORD=super_secret_123" > config.txt
git add config.txt
git commit -m "Aggiunta configurazione database"

# SCOPRIAMO L'ERRORE!
# Come rimuovere definitivamente il segreto
git reset --soft HEAD~1
git reset HEAD config.txt
rm config.txt

# Versione corretta
echo "DB_PASSWORD=\${DB_PASSWORD}" > config.txt
echo "# Variabile d'ambiente DB_PASSWORD richiesta" >> config.txt
git add config.txt
git commit -m "Template configurazione database (senza credenziali)"
```

### **7.2 File .gitignore**
```bash
# Creiamo .gitignore per file sensibili
echo "*.log" > .gitignore
echo "config.local" >> .gitignore
echo ".env" >> .gitignore
echo "backup/*.sql" >> .gitignore

git add .gitignore
git commit -m "Add: gitignore per file sensibili"
```

---

## **SESSIONE 8: Automazione con GitLab CI/CD (Sessione Avanzata)**

### **8.1 Introduzione alle Pipeline (30 min)**
**🛠️ HANDS-ON**: Prima pipeline GitLab CI

Creiamo `.gitlab-ci.yml`:
```yaml
# Pipeline per generazione documentazione automatica
stages:
  - validate
  - build
  - deploy

validate_markdown:
  stage: validate
  script:
    - echo "Validazione sintassi Markdown..."
    - find . -name "*.md" -exec echo "Checking {}" \;

build_docs:
  stage: build
  script:
    - echo "Generazione HTML da Markdown..."
    - echo "Creazione PDF delle procedure..."
  artifacts:
    paths:
      - docs/
    expire_in: 1 week

deploy_docs:
  stage: deploy
  script:
    - echo "Deploy su server documentazione intranet..."
  only:
    - main
```

### **8.2 Casi d'uso Reali per Tecnici IT (30 min)**
- **Backup automatico**: script attivato da commit
- **Validazione configurazioni**: controllo sintassi file config
- **Generazione documentazione**: da Markdown a HTML/PDF
- **Deploy automatico**: sincronizzazione con server di produzione

---

## **MATERIALI DIDATTICI FORNITI**

### **Repository di Esempio**
- Procedure IT standard
- Template per documentazione
- Script di utilità comune
- Esempi di .gitignore per diversi contesti

### **Cheat Sheet Distribuiti**
- Comandi Git essenziali
- Workflow GitFlow semplificato
- Risoluzione conflitti step-by-step
- Best practices messaggi commit

### **Esercizi da Portare a Casa**
1. **Progetto Documentazione Personale**: Ogni partecipante crea un repository per le proprie procedure di lavoro
2. **Collaborazione Simulata**: Gruppi di 2-3 persone lavorano su documentazione condivisa
3. **Pipeline Sperimentale**: Setup di una pipeline per generazione automatica documenti

---

## **STRUMENTI NECESSARI**

### **Hardware/Software Partecipanti**
- Notebook personale
- Git installato (supporto durante setup)
- Editor di testo (VS Code consigliato)
- Accesso GitLab@UdA configurato
- Connessione Internet (eduroam)

### **Aula/Infrastruttura**
- 25-30 postazioni
- Proiettore/schermo grande
- Connessione Internet stabile
- Prese elettriche/prolunghe
- Flipchart per schemi concettuali

---

## **VALUTAZIONE E FOLLOW-UP**

### **Durante il Corso**
- Quiz interattivi con Kahoot/Mentimeter
- Checkpoint pratici ad ogni sessione
- Feedback continuo tramite domande

### **Post-Corso**
- Questionario di gradimento
- Repository template GitLab@UdA per continuare pratica
- Canale Slack/Teams per domande successive
- Follow-up dopo 1 mese per verificare adozione

---

## **OUTPUT ATTESI**

Al termine del corso, ogni partecipante avrà:
1. **Repository personale** con documentazione propria
2. **Esperienza pratica** di collaborazione su progetti condivisi
3. **Conoscenza** dei workflow Git per team tecnici
4. **Capacità** di risolvere conflitti base
5. **Comprensione** delle potenzialità di automazione GitLab CI


- **Casi d'uso pratici** per tecnici universitari:
  - Documentazione di procedure
  - Script di configurazione
  - Manuali utente
  - Note di riunioni PNRR

---

*Corso progettato per massimizzare l'aspetto pratico e minimizzare la teoria astratta, con focus sui benefici concreti per il lavoro quotidiano del personale tecnico universitario.*