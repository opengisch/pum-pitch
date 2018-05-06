# Postgres/PostGIS migrations using Python
### PUMp your db with PUM

Mario Baranzini - Opengis.ch
Geopython 2018
Basel - May 8

Note:
- Buongiorno, benvenuti a questa presentazione.

---
# Who am I?

Note:
- Sono Mario Baranzini, vengo dalla Svizzera italiana. (Scusate il mio inglese...).
- sviluppo in ambito GIS, principalmente in Python e Java.
- Lavoro per Opengis.ch

---
# Opengis.ch

Note:
- Opengis.ch è una piccola ditta specializzata in software GIS opensource per PMI.
- Sviluppo di QGIS core e plugin e sviluppo di soluzioni web.

---
Abstract

Note:
- Oggi, vi voglio parlare di migrazioni di database, voglio mostrare come gestiamo l'evoluzione di database in due progetti Opensource legati a QGIS: QWAT e QGEP
- Ma facciamo un salto indietro

---
Development processes: Waterfall

Note:
- Tempo fa, quando il processo a cascata era il modo comune di sviluppare software, si tendeva a definire il db model all'inizio dello sviluppo e si cercava in tutti i modi di non più modificarlo.

+++
Iterative

Note:
- Poi, con il tempo si sono fatte strada altre metodologie di sviluppo iterative, dove in iterazioni più o meno lunghe, viene ripetuto l'intero processo.
- Questo comporta il design di nuove funzionalità e a volte il refactoring di quelle esistenti con conseguenti evoluzioni del codice e del db...

+++
Code evolution

Note:
- Per la gestione delle evoluzioni del codice, si sono diffuse ampiamente e sono praticamete universalmente accettate, delle metodologie. Una su tutte in ambito Opensource, legata al software git, che spinge lo sviluppatore a lavorare su una copia del codice, per poi mergiare le modifiche nel codice originale.

+++
DB evolution

Note:
- In ambito database invece sono meno conosciute e utilizzate le strategie per gestire evoluzioni del datamodel
- Alcune delle pratiche più importanti e utili, che spesso usano un approccio simmile a quanto avviene con il codice, sono:

+++
Local db instances

Note:
- Ogni sviluppatore lavora su una copia locale del db.
- Quindi deve essere semplice generare lo stesso db localmente tramite scripts. Tools come Docker aiutano notevolmente in questo

+++
migration files (deltas)

Note:
- Ogni cambiamento fatto da uno sviluppatore, sulla banca data, deve essere contenuto in un delta file (migration file)

+++
version control

Note:
- Ogni db artefact (generation script, delta file, data dump, ...) viene messo sotto version control.

+++
CI

Note:
- I cambiamenti vengono testati, integrati e deploiati in automatico tramite C.I.

---
Come gestire queste migrazioni in automatico?
Con un migration tool
ce ne sono diversi (citare flyway o liquibase?)
e c'è pum (pip install pum)

Note:
- Come detto in precedenza, qualche tempo fa ci siamo trovati a voler applicare queste pratiche in modo rigoroso in due progetti Opensource (QWAT e QGEP).
- Esistono tools e software appositi (e.g. Flyway or Liquidbase).

+++
PUM (Postgres Upgrades Manager)

Noi abbiamo deciso di sviluppare PUM.

Note:
per potersi integrare nel processo di QGEP e QWAT (con script python)
per poterlo fare specifico per postgres (e postgis)

---
Cosa fa PUM?


Note:
- Panoramica delle funzionalità
- In particolare:

+++
check

Note:
- Permette di testare le differenze tra
---
upgrade

---
test-and-upgrade

---
delta files
py e sql

+++
pre e post

---
Futuri sviluppi

---
Domande e ringraziamenti
