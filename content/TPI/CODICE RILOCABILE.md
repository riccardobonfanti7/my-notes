Un **codice rilocabile** è un tipo di codice generato durante la fase di compilazione di un programma, in cui gli indirizzi delle istruzioni e dei dati non sono definitivi, ma relativi. Ciò significa che, invece di fare riferimento a indirizzi di memoria fissi (assoluti), **il codice utilizza indirizzi logici** o simbolici che verranno **successivamente trasformati in indirizzi fisici** durante **il caricamento del programma in memoria.**
Quando un programma contenente codice rilocabile viene caricato in memoria, il **loader** del sistema operativo esegue una **rilocazione**, cioè **modifica gli indirizzi relativi per adattarli alla posizione effettiva del programma in memoria.** Questo permette al programma di essere caricato in diverse posizioni fisiche della memoria, rendendolo più flessibile e facilitando la gestione della memoria nei sistemi operativi multitasking. 
Il compilatore genera gli indirizzi ipotizzando che il programma venga caricato nella memoria a partire dalla cella 0 e in base a questo valore vengono generati tutti gli indirizzi e i collegamenti dati/istruzioni. Può avvenire in momenti diversi:
- All’atto del caricamento in memoria (==rilocazione statica==): viene individuato l’indirizzo iniziale (indirizzo base) e viene sommato a tutti i riferimenti presenti nel programma (offset).
- In fase di esecuzione del programma (==rilocazione dinamica==): viene inserito in apposito registro (registro base) il valore dell’indirizzo effettivo della prima locazione di memoria centrale; quindi durante l’esecuzione, istruzione per istruzione, si calcola l’indirizzo fisico sommando a ogni indirizzo relativo il contenuto del registro base.

## MMU (Memory Management Unit)
La MMU è un dispositivo hardware che prende ogni **indirizzo logico** generato da un processo e lo **riloca**, trasformandolo in un **indirizzo fisico** utilizzabile direttamente dalla memoria fisica del sistema. Questa operazione è basata su un valore contenuto in un **registro di rilocazione** (chiamato anche **registro base**). Tale registro contiene l'indirizzo di inizio della porzione di memoria fisica assegnata al processo.

**Formula di rilocazione**
Per eseguire la conversione tra indirizzi logici e fisici, la MMU utilizza la seguente formula:
>Indirizzo fisico=Indirizzo logico+Indirizzo di rilocazione
- **Indirizzo logico**: l'indirizzo generato dal programma o dal processo in esecuzione. Questo indirizzo è relativo alla memoria del processo.
- **Indirizzo di rilocazione**: il valore nel registro di rilocazione (registro base) che indica l'inizio dell’area di memoria fisica assegnata al processo.
- **Indirizzo fisico**: l'indirizzo reale in memoria fisica a cui si accede.

**Linking** dei programmi: **esegue il calcolo degli indirizzi logici**

**Binding**: passaggio da **indirizzo logico a fisico** , può essere fatta in momenti diversi:
- Durante l’esecuzione: MMU dispositivo hardware che attua il mapping/ mappatura( associazione tra ind logico e fisico): processo in esecuzione genera solo ind logici tradotti dalla MMU in corrispondenti indirizzi fisici.(**rilocazione dinamica**)
- nel momento del loading del programma (**rilocazione statica**) 
- durante la compilazione (**indirizzamento assoluto**)

