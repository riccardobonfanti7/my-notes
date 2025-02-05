# Definizioni
In parole semplici, un programma per computer è una serie di istruzioni dettagliate che indicano al computer cosa fare.
==**Un programma** è **costituito dall’insieme delle sue istruzioni memorizzate su una memoria di massa**. È una **entità statica**.==
Per essere eseguito, un programma deve essere **interpretato** o **compilato**. Gli [[INTERPRETE|interpreti]] eseguono il codice riga per riga, mentre i [[Compilatore|compilatori]] trasformano tutto il codice in un formato eseguibile in una singola operazione.

==**Processo** è **un'istanza di un programma in evoluzione,** è una **entità dinamica**== ==utilizza risorse come CPU, memoria== e file aperti.
==**Un Processo possiede una traccia di esecuzione**==(sequenza di stati assunti dal processore durante l’esecuzione del processo).

A un **processo** sono associati:
- **Codice eseguibile**
- **Spazio di memoria con i** ==**dati**== **e lo spazio per lo Stack**
- Il **PCB**(process control Block) o descrittore di processo: struttura apposita che contiene informazioni dello stato del processo come: ==PID== ( valore numeri da 1 a 30000) pid =**0 indica un processo speciale chiamato swapper, PID =**1**  appartiene al processo **INIT**( **primo processo creato all’avvio del sistema e rimane in funzione tutto il tempo**); ==puntatore==(indirizzo del descrittore del processo che l’ha generato(**processo padre**)), ==a priorità==, ==stato di avanzamento==(contenuto dei registri di lavoro), ==immagine della memoria==, info relative alle ==altre risorse assegnate al processo==.

Processo chiamato **padre** può generare copie di se stesso chiamate **processi figli.**

>Processo per essere eseguito deve essere allocato in memoria centrale (RAM).
>Deve risiedere in una area di RAM sufficientemente grande e contigua

Qui puoi trovare le varie [[Tecniche di gestione della memoria]].

Un processo può essere rimosso dalla memoria e trasferito su disco(swap out) per permettere l’esecuzione di un altro processo che richiede più memoria RAM e in seguito riportarlo in memoria (swap in) per proseguire l’esecuzione.

> Lo **scambio di contesto** (contex-switching) avviene quando il **sistema operativo interrompe l'esecuzione di un processo** (per esempio, per dare spazio a un altro processo) e **salva lo stato del processo corrente** per poterlo riprendere in un momento successivo e così la CPU passa ad eseguire un altro processo.
### Swap Out

- **Obiettivo**: L'operazione di swap out viene eseguita quando la RAM non ha spazio sufficiente per ospitare tutti i processi attivi. Questo può accadere quando:

- Un processo in esecuzione richiede più memoria di quanto attualmente disponibile.

- Un processo (o parte di esso) viene trasferito dallo spazio di memoria RAM allo **spazio di swap** su disco rigido(hard disk).
- Questo libera spazio in RAM, consentendo ad altri processi di essere caricati o continuare la loro esecuzione.

### Swap In

- **Obiettivo**: L'operazione di swap in avviene quando il sistema ha bisogno di accedere nuovamente a un processo che è stato precedentemente swappato nel disco rigido.
- Il sistema operativo recupera il processo dallo spazio di swap su disco e lo carica di nuovo in RAM.
- Se non c'è abbastanza spazio libero in RAM, potrebbe essere necessario swappare un altro processo attualmente in esecuzione per fare spazio per quello che si sta caricando.




