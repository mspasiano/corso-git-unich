# Corso "GIT a supporto dei tecnici UNIV"
## Programma dettagliato per 2 giornate da 5 ore ciascuna

---

## **GIORNATA 1 - Fondamenti e Lavoro Locale**
### **Durata**: 5 ore (9:00-13:00 + 14:00-15:00)

---

### **SESSIONE 1: Introduzione e Setup (9:00-10:30)**

#### **1.1 Benvenuto e Obiettivi del Corso (20 min)**
- Presentazione partecipanti e aspettative
- Panoramica degli obiettivi del corso
- **Focus**: GIT non solo per sviluppatori, ma per tutto il personale tecnico IT

#### **1.2 Cenni Storici e Motivazioni (25 min)**
- **Storia**: Linus Torvalds e la nascita di GIT (2005)
- **Problemi risolti**: 
  - Gestione versioni distribuite
  - Collaborazione in team
  - Tracciabilità delle modifiche
- **Casi d'uso pratici** per tecnici universitari:
  - Documentazione di procedure
  - Script di configurazione
  - Manuali utente
  - Note di riunioni PNRR

#### **1.3 Setup dell'Ambiente (25 min)**
**🛠️ HANDS-ON**: Preparazione workstation
- Installazione GIT sui notebook dei partecipanti
- Configurazione iniziale:
  ```bash
  git config --global user.name "Nome Cognome"
  git config --global user.email "email@unich.it"
  git config --global init.defaultBranch main
  ```
- Test di connessione a GitLab@UdA
- Setup editor preferito (VS Code, nano, vim)

---

### **SESSIONE 2: Concetti Fondamentali (10:45-12:15)**

#### **2.1 Concetti Base (30 min)**
- **Repository**: cartella "intelligente" con cronologia
- **Commit**: snapshot del lavoro
- **Staging Area**: area di preparazione
- **Working Directory**: cartella di lavoro
- **Branch**: linee di sviluppo parallele

#### **2.2 Il Primo Repository (30 min)**
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

#### **2.3 Lavorare con i File (30 min)**
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

---

### **PAUSA PRANZO (12:15-14:00)**

---

### **SESSIONE 3: Gestione Avanzata Locale (14:00-15:00)**

#### **3.1 Navigare nella Storia (30 min)**
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

#### **3.2 Gestione dei Branch (30 min)**
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

---

## **GIORNATA 2 - Collaborazione e Strumenti Avanzati**
### **Durata**: 5 ore (9:00-13:00 + 14:00-15:00)

---

### **SESSIONE 4: Lavoro Distribuito (9:00-10:30)**

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

---

*Corso progettato per massimizzare l'aspetto pratico e minimizzare la teoria astratta, con focus sui benefici concreti per il lavoro quotidiano del personale tecnico universitario.*