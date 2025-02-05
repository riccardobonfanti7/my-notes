
## Cos'è un Sistema Operativo?

Un **sistema operativo (SO)** è un <u>software fondamentale che gestisce le risorse hardware e software di un computer</u>. Funziona come intermediario tra l'utente e l'hardware, consentendo l'esecuzione di programmi e la gestione delle risorse del sistema.

==**Sistemi operativi lavorano in multiprogrammazione**==. La **multiprogrammazione** è una tecnica che permette a un ==sistema operativo di gestire più programmi in memoria contemporaneamente==. In questo modo, ==quando un processo è in attesa==, ==il sistema operativo può passare a un altro processo che è pronto per essere eseguito==. Questo approccio consente di ridurre i tempi di inattività e di migliorare l'utilizzo della CPU.
## Funzioni Principali di un Sistema Operativo

1. **Gestione delle Risorse Hardware**: Il SO controlla e coordina l'uso di CPU, memoria, dischi rigidi e dispositivi di input/output.

2. **Esecuzione dei Processi**: Gestisce l'esecuzione dei programmi, allocando tempo di CPU e memoria in modo efficiente.

3. **Gestione della Memoria**: Tiene traccia della memoria utilizzata dai processi e gestisce la memoria virtuale.

4. **Gestione dei File**: Fornisce un sistema di file per l'organizzazione, la memorizzazione e l'accesso ai dati.

5. **Interfaccia Utente**: Fornisce un'interfaccia (grafica o testuale) per consentire agli utenti di interagire con il computer.
### Sistemi Operativi Monoutente e Multiutente

- **Monoutente**: Gestisce un solo utente alla volta (es. MS-DOS).
- **Multiutente**: Permette a più utenti di utilizzare il sistema contemporaneamente.
### Sistemi mono-processore e multi-processore 
Nel sistema mono-processore c'è un **unico processore** che può eseguire una sola istruzione alla volta. Tuttavia, per simulare il multitasking, il sistema operativo esegue un’**alternanza** tra i processi, tramite una tecnica chiamata **time slicing**.
Ogni processo viene eseguito per una piccola quantità di tempo, chiamata **quantum di tempo**, prima che il processore passi al processo successivo. Anche se i processi avanzano uno alla volta, l'alternanza è così rapida che l’utente percepisce un'esecuzione simultanea. 

Nel sistema multi-processore sono presenti **più processori** fisici o core che possono eseguire i processi realmente in parallelo. Questo significa che diversi processi o thread possono essere assegnati a processori separati e **eseguiti simultaneamente**.
Questa capacità di eseguire processi parallelamente aumenta la potenza di calcolo e consente un multitasking reale, particolarmente utile per carichi di lavoro intensivi o complessi.
## Esempi di Sistemi Operativi

- **Windows**: Un sistema operativo sviluppato da Microsoft, popolare per computer desktop e laptop.
- **macOS**: Sistema operativo sviluppato da Apple per i suoi computer.
- **Linux**: Un sistema operativo open-source molto usato in server.
- **Android**: Basato su Linux, progettato per dispositivi mobili.

## Vantaggi dei Sistemi Operativi

1. **Facilità d'uso**: Offrono interfacce intuitive per l'interazione con l'hardware.
2. **Gestione Efficiente delle Risorse**: Ottimizzano l'uso della CPU, della memoria e delle periferiche.
3. **Sicurezza**: Forniscono meccanismi per la protezione dei dati e l'autenticazione degli utenti.
## Difetti dei Sistemi Operativi

1. **Costi**: Alcuni sistemi operativi commerciali possono avere costi elevati di licenza.
2. **Risorse**: I sistemi operativi più complessi richiedono più risorse hardware.
3. **Vulnerabilità**: Possono essere soggetti a malware e attacchi informatici se non gestiti correttamente.
