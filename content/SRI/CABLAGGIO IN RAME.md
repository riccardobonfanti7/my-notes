# Caratteristiche del cablaggio in rame
Il cablaggio in rame è il tipo più comune di cablaggio utilizzato oggi nelle reti. 

Esistono **tre diversi tipi di cablaggio in rame**, ciascuno utilizzato in situazioni specifiche.

Le reti utilizzano supporti in rame perché sono economici, facili da installare e hanno una bassa resistenza alla corrente elettrica. Tuttavia, i supporti in rame sono limitati dalla distanza e dalle interferenze del segnale.

**I dati vengono trasmessi su cavi di rame come impulsi elettrici**.

>Più il segnale viaggia lontano, più si deteriora. Questo si chiama **attenuazione del segnale**.

Interferenze provenienti da due fonti:
- **Interferenza elettromagnetica (EMI) o interferenza in radiofrequenza (RFI):**  i segnali EMI e RFI possono distorcere e corrompere i segnali dati trasportati dai supporti in rame. Le potenziali fonti di EMI e RFI includono onde radio e dispositivi elettromagnetici, come luci fluorescenti o motori elettrici.

- **Crosstalk:** un disturbo causato dai campi elettrici o magnetici di un segnale su un filo rispetto al segnale in un filo adiacente.  Nei circuiti telefonici, la diafonia può provocare l'ascolto di parte di un'altra conversazione vocale da un circuito adiacente.

>Per contrastare gli effetti negativi di EMI e RFI, alcuni tipi di cavi in rame sono **avvolti in una schermatura metallica** e richiedono collegamenti di messa a terra adeguati.

>Per ==contrastare gli effetti negativi della diafonia==, alcuni tipi di cavi in rame **hanno coppie di fili del circuito opposti intrecciati** insieme, che annullano efficacemente la diafonia.

# Tipi di cablaggio in rame
- [[CABLAGGIO IN RAME#UTP|Doppino intrecciato non schermato (UTP)]]
- [[CABLAGGIO IN RAME#STP|Doppino intrecciato schermato (STP)]]
- [[CABLAGGIO IN RAME#CAVO COASSIALE|Cavo coassiale]]

### UTP
Il cablaggio a doppino intrecciato non schermato (UTP) è il **mezzo di rete più comune**. Il cablaggio UTP, **terminato con connettori RJ-45**, viene utilizzato per interconnettere gli host di rete con dispositivi di rete intermedi, come switch e router.

Nelle LAN, il cavo UTP è costituito da quattro coppie di fili codificati a colori che sono stati intrecciati insieme e quindi racchiusi in una guaina di plastica flessibile che protegge da lievi danni fisici. **La torsione dei cavi aiuta a proteggere dalle interferenze del segnale** provenienti da altri cavi.

  
### STP
Il doppino intrecciato schermato (STP) offre una migliore protezione dal rumore rispetto al cablaggio UTP. Tuttavia, rispetto al cavo UTP, il cavo STP è notevolmente più costoso e difficile da installare. Come il cavo UTP, STP utilizza un connettore RJ-45.

**I cavi STP combinano le tecniche di schermatura** per contrastare EMI e RFI e l**a torsione del filo per contrastare** la diafonia. Per ottenere il massimo vantaggio dalla schermatura, i cavi STP sono terminati con speciali connettori dati STP schermati. Se il cavo non è messo a terra in modo corretto, la schermatura potrebbe fungere da antenna e captare segnali indesiderati.

Il cavo STP mostrato utilizza quattro coppie di fili, ciascuno avvolto in una schermatura in lamina, che viene poi avvolta in lamina metallica complessiva.

  

  

  
### CAVO COASSIALE
Il cavo coassiale è costituito da quanto segue:
Per trasmettere i segnali elettronici viene utilizzato un conduttore di rame. 
Uno strato di isolamento in plastica flessibile circonda il conduttore di rame.

Il materiale isolante è circondato da lamina metallica, che funge da secondo filo nel circuito e da schermatura per il conduttore interno. Questo secondo strato, o schermatura, riduce anche la quantità di interferenze elettromagnetiche esterne.

L'intero cavo è coperto da una guaina per evitare danni fisici minori.

Esistono **diversi tipi di connettori** utilizzati con il cavo coassiale. Nella figura sono mostrati i connettori Bayonet Neill–Concelman (**BNC**), tipo **N** e tipo **F**.

Sebbene il cavo UTP abbia sostanzialmente sostituito il cavo coassiale nelle moderne installazioni Ethernet, il design del cavo coassiale viene utilizzato nelle seguenti situazioni:

**Installazioni wireless** : i cavi coassiali **collegano le antenne ai dispositivi wireless**. Il cavo coassiale trasporta l'energia in radiofrequenza (RF) tra le antenne e le apparecchiature radio.

**Installazioni Internet via cavo** : i fornitori di servizi via cavo forniscono connettività Internet ai propri clienti sostituendo porzioni del cavo coassiale e supportando gli elementi di amplificazione con cavo in fibra ottica. Tuttavia, il cablaggio all'interno della sede del cliente è ancora costituito da cavo coassiale.

