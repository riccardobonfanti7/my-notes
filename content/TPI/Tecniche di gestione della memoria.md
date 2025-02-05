# Tecniche di Gestione della Memoria

Le tecniche di gestione della memoria sono metodi utilizzati dai sistemi operativi per gestire l'allocazione dei processi e l'uso della memoria RAM in modo efficiente. In questa sezione vedremo le principali tecniche: [[Tecniche di gestione della memoria#1. Partizionamento Fisso|partizionamento fisso]], [[Tecniche di gestione della memoria#2. Partizionamento Variabile|partizionamento variabile]], [[Tecniche di gestione della memoria#3. Paginazione|paginazione]] ,[[Tecniche di gestione della memoria#4. Segmentazione|segmentazione]] e [[Tecniche di gestione della memoria#5. Paginazione con Segmentazione|paginazione con segmentazione]].

## 1. Partizionamento Fisso

Il **Partizionamento fisso** è un metodo di gestione della memoria in cui la memoria principale viene suddivisa in blocchi di dimensioni fisse, chiamati "partizioni". Ogni programma o processo viene allocato in una partizione, e non può superare le dimensioni della partizione stessa.
Per ogni partizione viene gestita una coda di entrata dei processi in attesa e vengono aggiunti alla coda della partizione più piccola in cui possono essere allocati.

### Problemi:
1. Frammentazione esterna
2. Frammentazione interna

1.Si verifica quando, nonostante la somma totale della memoria libera sia sufficiente per caricare un nuovo processo, questa memoria è **sparsa in piccoli blocchi** tra le partizioni occupate, quindi **non c'è un blocco contiguo abbastanza grande** per il nuovo processo.

2.La frammentazione interna avviene quando la dimensione di un processo è **inferiore alla dimensione della partizione** in cui viene caricato, lasciando uno spazio non utilizzato all'interno della partizione stessa. Le partizioni sono fisse, non possono essere ridimensionate per adattarsi al processo, e la memoria non utilizzata non può essere riallocata ad altri processi.

## 2. Partizionamento Variabile

Il **partizionamento variabile** è un altro metodo in cui la memoria viene suddivisa in partizioni di dimensioni variabili, [[Tecniche di gestione della memoria#Strategie di allocazione dinamica della memoria centrale|assegnate dinamicamente]] in base alla dimensione del processo. Ogni partizione si adatta alla dimensione del processo. Non avviene frammentazione interna.
### Strategie di allocazione dinamica della memoria centrale:
- **First-fit**: il gestore della memoria scandisce la tabella delle partizioni finché trova la prima zona libera abbastanza grande per contenere il processo. Metodo più veloce
- **Best-fit**: il gestore della memoria scandisce tutta la tabella delle partizioni e sceglie la zona libera più piccola sufficientemente grande da contenere il processo. Metodo più lento del first-fit e tende a lasciare zone di memoria troppo piccole per essere usate.
- **Worst-fit**: sceglie la zona libera più grande
- **Next-fit**: cerca il primo spazio libero in grado di accogliere il processo partendo dallo spaziolibero successivo all’ultimo processo allocato. Questo evita di allocare i processi tutti all’inizio della RAM.


La **memoria virtuale** è una tecnica che permette al computer di usare una parte del disco rigido come estensione della RAM. Quando la **RAM è piena**, il sistema operativo **sposta temporaneamente su disco alcuni dati o processi inattivi (swap out) per fare spazio in RAM per altri programmi attivi**. Questo consente di eseguire programmi più grandi della memoria fisica disponibile, dando l'impressione di avere più RAM di quella realmente installata.

**Program counter cambia:**
Il **program counter** (PC) è un registro che tiene traccia dell'istruzione successiva da eseguire. Quando avviene uno **swap out** in memoria virtuale, cioè lo spostamento temporaneo di un processo inattivo sul disco, il sistema deve aggiornare il program counter per ricordare a che punto si trovava l’esecuzione di quel processo.

## 3. Paginazione
La **paginazione** è una tecnica che suddivide la memoria in blocchi di dimensione fissa chiamati **pagine fisiche** o frame . Ogni processo viene suddiviso in **pagine logiche** di dimensione fissa, e queste pagine possono essere allocate in qualsiasi posizione nella memoria fisica.
Il numero di pagine logiche può differire dal numero di pagine fisiche.
- Se il numero di pagine logiche è minore delnumero di pagine fisiche il programma potrebbe essere caricato tutto in memoria
- Se la pagine logiche sono di più di quelle fisiche il programma viene caricato parzialmente.

Nella paginazione sono presenti due tabelle:
1. ==tabella delle pagine fisiche==
2. ==tabella delle pagine logiche== 

1.Formata da tante righe quanti sono i frame in RAM e ogni voce della tabella contiene:
- **Indirizzi fisici iniziali dei frame:** Ogni pagina logica è mappata a un frame fisico specifico in memoria.
- **Stato della pagina:** Indica se una pagina fisica è libera o occupata.(bit di validità)
- **ID del processo:** Identifica quale processo ha caricato una determinata pagina fisica.

2.formata da tante righe quante sono le pagine logiche di un processo e ogni voce della tabella contiene:
- **Bit di validità:** Indica se una pagina logica del processo è attualmente in RAM (1) o su disco (0).
- **Numero del frame:** indica in quale frame quella pagina logica è stata caricata.

### Traduzione da indirizzi logici a fisici
Il dispositivo che si occupa di questa traduzione è la MMU.
==**Indirizzo logico** ==è composto da:
- ==**Numero di pagina logica**==: identifica quale pagina logica del processo si sta cercando.
- ==**Offset**==: specifica la posizione all'interno della pagina.

==**Indirizzo fisico:**==
• ==**Indirizzo fisico = Numero del frame fisico + Offset**==
1. ==**Traduzione tramite la tabella delle pagine**:==

- La **MMU** consulta la **tabella delle pagine logiche** associata al processo attivo.
- Cerca la voce corrispondente al **numero di pagina logica** utilizzato come indice .
 **Ogni voce della tabella**:
- La voce contiene:
- ==**Numero del frame fisico**==: specifica in quale frame della memoria fisica si trova la pagina logica.
- ==**Bit di validità**==: indica se la pagina è caricata in memoria fisica (1 = valida; 0 = non valida).

2. ==**Verifica del bit di validità**:==
- Se il bit è **1**, la MMU memorizza il numero del frame fisico cercandolo nella tabella delle pagine fisiche e prende l'indirizzo fisico del frame corrispondente con l’**offset** per generare l’indirizzo fisico finale.
- ==Se il bit è **0**, si verifica== un **[[Tecniche di gestione della memoria#Page fault|page fault]]**, e il SO interviene per caricare la pagina nella memoria fisica
#### Page fault
Se durante la traduzione la MMU scopre che il **bit di validità** di una pagina logica è **0** (la pagina non è in RAM), si verifica un **page fault**. Questo evento indica che la pagina richiesta si trova su disco e non in memoria fisica.

**Azioni in caso di page fault:**

1. Il sistema operativo sospende l'esecuzione del processo.
2. Carica la pagina mancante dal disco in un frame libero della RAM (se non ci sono frame liberi, viene eseguito uno [[TPI/PROGRAMMA e PROCESSO#Swap Out|swap-out]] della pagina logica inattiva in ram per lasciare un frame libero alla pagina logica necessaria in quel momento, da essere caricata.
3. Aggiorna la tabella delle pagine.
4. Riprende l'esecuzione del processo.

## 4. Segmentazione

La **segmentazione** è una tecnica che divide la memoria in **segmenti fisici** di dimensioni variabili, dove ogni segmento rappresenta una porzione logica di un programma( suddiviso in **segmenti logici** ad esempio, codice, dati, stack).Questa suddivisione in prozioni logiche del programma viene fatta dal programmatore. Ogni segmento ha una dimensione variabile e può essere caricato in qualsiasi parte della memoria fisica. 

La **segmentazione** utilizza **una sola tabella**: 
**Tabella dei segmenti**:
- ==**Indirizzo Base**==: l'indirizzo di inizio del segmento fisico nella memoria fisica.
- ==**Limite**==: la lunghezza del segmento.
- Se un processo ha **N segmenti**, la **tabella dei segmenti** avrà **N righe**.

#### Traduzione dell'indirizzo logico a fisico 
1. **Indirizzo logico**: È composto da due parti:
- ==**Numero del segmento**==: Indica a quale segmento del programma si sta accedendo.
- ==**Offset**==: È la posizione all’interno di quel segmento.

2. **Traduzione da indirizzo logico a fisico**  fatta dalla MMU:
- Il numero del segmento è usato come indice per consultare la **tabella dei segmenti**.
- La **tabella dei segmenti** fornisce l'indirizzo di base del segmentto fisico e il limite.
- Se l'offset è compreso all'interno del **limite** del segmento (cioè non oltre il fine del segmento), si calcola l'indirizzo fisico come: ==Indirizzo fisico finale =  Base del segmento fisico + offset ==.
- Se l'offset è fuori dal limite, si verifica un **segmentazione fault**, ovvero il programma sta cercando di accedere a memoria che non è parte del segmento.

## 5. Paginazione con Segmentazione

La **paginazione con segmentazione** combina i vantaggi della paginazione e della segmentazione. In questo approccio, la memoria centrale fisica è divisa in pagine fisiche (frame) di dimensione fissa, il processo è suddiviso in segmenti logici di dimensioni diverse, ciascuno suddiviso in pagine logiche. I frame hanno la stessa dimensione delle pagine logiche, che infatti vengono caricate in essi.

In questo sistema, ci sono **due tabelle** principali per la gestione della memoria:
1. **Tabella dei segmenti**:
- Ogni **processo** ha una **tabella dei segmenti**.
- Ogni **voce** della tabella dei segmenti corrisponde a un **segmento** del processo (ad esempio, codice, dati, stack, ecc.).

- Ogni voce nella tabella dei segmenti contiene:
- **Base**: l'indirizzo di base del segmento nella memoria fisica.
- **Limite**: la dimensione del segmento.

2. **Tabella delle pagine (per ogni segmento)**:
- Ogni **segmento** del processo può essere ulteriormente suddiviso in **pagine**.
- Ogni segmento ha la sua **tabella delle pagine**, che mappa le **pagine del segmento** ai **frame fisici**.
- Ogni voce nella tabella delle pagine contiene l'indirizzo del **frame fisico** che corrisponde a una pagina logica.
#### Traduzione da indirizzo logico a fisico (MMU)
Un **indirizzo logico** è composto da tre parti:
- **Indice del segmento**: identifica quale segmento del processo stiamo cercando.
- **Indice della pagina all'interno del segmento**: identifica quale pagina dentro quel segmento stiamo cercando.
- **Offset**: la posizione all'interno della pagina.

**Traduzione**:
- **Passaggio 1 - Traduzione del segmento**:
- Il sistema operativo mantiene una **tabella dei segmenti** che mappa ogni segmento logico al corrispondente segmento in memoria fisica (indicato da un **indirizzo base** e un **limite**).
- La MMU, utilizzando la **tabella dei segmenti**, traduce il numero del segmento **s** in un **indirizzo fisico di base** per quel segmento.

-  **Passaggio 2 - Traduzione della pagina**:
- Una volta che il segmento è stato individuato, l'indirizzo logico viene trattato come una **pagina** all'interno di quel segmento.
- Ogni segmento è suddiviso in **pagine**, quindi la MMU usa la **tabella delle pagine** per tradurre il numero della **pagina** **p** in un **frame fisico**.

- **Passaggio 3 - Calcolo dell'indirizzo fisico finale**:
- Una volta che il numero del **frame fisico** **f** è stato ottenuto dalla **tabella delle pagine**, viene sommato allo **spiazzamento** **d** per ottenere l'indirizzo fisico finale.

